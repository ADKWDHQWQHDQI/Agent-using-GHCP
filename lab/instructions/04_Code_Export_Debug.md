# Module IV — Exporting Code and Debugging with GitHub Copilot

> [!NOTE]
> **Duration:** ~15 minutes
> This is the module where **GitHub Copilot becomes your primary tool**. You will export the agent from Foundry Toolkit for VS Code to Python code, encounter a real-world runtime error, and use Copilot to diagnose and fix it. This teaches not just how to *use* Copilot, but how to *think* with Copilot.

---

## Objectives

- Export the Compliance Agent from Foundry Toolkit for VS Code to Python code via **View Code**
- Set up the project directory, install dependencies, and verify the `.env` configuration
- Run the agent and encounter a common Azure runtime error
- Use **GitHub Copilot Agent mode** to diagnose, trace, and fix the error
- Successfully run the agent from the command line

---

## Step 1: Export the Agent Code

1. In the Foundry Toolkit for VS Code Agent Builder (where you saved the ComplianceAgent in Module III), locate the **View Code** button at the top-right corner of the screen.

2. Click **View Code**.

3. You will be prompted to choose a location to save the agent code. A dialog will appear:

   ```
   Choose the folder where your agent root folder will be located
   ```

4. Select the **default location** (e.g., `C:\Users\<username>\AIToolkitAgents`) or click **Browse** to choose a different folder (e.g., inside your workshop repository under `agent/`).

5. Press **Enter** to confirm. A new VS Code window will open with the generated agent project.

---

## Step 2: Explore the Generated Project Structure

The generated project will contain the following key files:

```
ComplianceAgent/
├── run_agent.py           ← Main agent script (entry point)
├── requirements.txt       ← Python dependencies
├── .env                   ← Environment variables (endpoint, model name)
└── README.md              ← Auto-generated documentation
```

### Understanding `run_agent.py`

The main script typically contains:

1. **Imports** — Azure AI Foundry SDK, agent classes
2. **Configuration** — Endpoint and model name from environment variables
3. **Agent creation** — Creates the agent with instructions and Azure AI Search tool
4. **Conversation** — Sends a hardcoded user message and prints the response

> [!TIP]
> To understand the generated code, you can ask GitHub Copilot in **Ask mode**:
>
> Open Copilot Chat (`Ctrl+Alt+I`), ensure `run_agent.py` is referenced as context, and send:
> ```
> Explain what this script does, step by step. Focus on how the agent 
> connects to Azure AI Foundry and uses Azure AI Search for retrieval.
> ```

---

## Step 3: Verify the .env Configuration

Open the `.env` file and verify the following values:

```env
PROJECT_ENDPOINT=https://<your-foundry-hub>.services.ai.azure.com/api/projects/<your-project-name>
MODEL_DEPLOYMENT_NAME=gpt-4o
```

### Find Your Project Endpoint

If you need to find your endpoint:

1. **Option A — From AI Foundry Portal:**
   - Open [AI Foundry](https://ai.azure.com)
   - Navigate to your project
   - Click **Overview** in the left sidebar
   - Copy the **Project endpoint** URL

2. **Option B — Using Azure CLI (ask Copilot):**

   Open Copilot Chat in **Agent mode** and send:

   ```
   Using Azure CLI, find the AI Foundry project endpoint for the 
   "Compliance-Sentinel" project in the "compliance-agent-rg" resource group. 
   Run the command and show me the endpoint URL.
   ```

   GitHub Copilot will generate and run the appropriate `az` command.

> [!IMPORTANT]
> Ensure the `PROJECT_ENDPOINT` URL is correct and the `MODEL_DEPLOYMENT_NAME` matches the name of your GPT-4o deployment from Module II. If these values are incorrect, the agent will fail to connect.

---

## Step 4: Install Dependencies

1. Open a terminal in the project directory.

2. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Verify the installation:

   ```bash
   pip list | findstr azure
   ```

   You should see packages like:
   - `azure-ai-projects`
   - `azure-ai-agents`
   - `azure-identity`

> [!NOTE]
> If you see dependency conflicts, try creating a virtual environment first:
> ```bash
> python -m venv .venv
> .venv\Scripts\activate
> pip install -r requirements.txt
> ```

---

## Step 5: Run the Agent (and Encounter the Error)

1. Ensure you are authenticated with Azure:

   ```bash
   az login
   ```

2. Run the agent script:

   ```bash
   python run_agent.py
   ```

### The Expected Error

There is a **high probability** that you will encounter the following error:

```
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: invalid start byte
```

This is a **known issue** with the Azure AI Foundry SDK when using the `aiohttp` transport layer. **Do not panic** — this is an opportunity to learn how to debug with GitHub Copilot.

> [!NOTE]
> If you **do NOT** encounter this error and the agent runs successfully — congratulations! Skip ahead to **Step 7** and proceed to Module V. The error depends on your specific Python package versions and Azure SDK combination.

---

## Step 6: Debug the Error with GitHub Copilot

This is the **most powerful part of the workshop**. You will use GitHub Copilot to trace through the error, understand the root cause, and generate a fix — all without leaving VS Code.

### 6.1 Share the Error with Copilot

1. Open **GitHub Copilot Chat** (`Ctrl+Alt+I`).

2. Switch to **Agent mode** using the mode selector at the top of the chat panel.

3. Copy the full error traceback from the terminal and paste it into Copilot Chat with the following prompt:

   ```
   I am running an Azure AI Foundry agent and getting this error:

   UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: 
   invalid start byte

   The error occurs when the agent tries to process the response from 
   Azure AI Search. 

   The file run_agent.py is the entry point.

   Diagnose this error and explain the root cause.
   ```

### 6.2 Understanding the Root Cause

GitHub Copilot will trace through the error and identify the root cause. Here is what it will find:

**Error Chain:**
```
aiohttp → azure-core → ContentDecodePolicy → auto_decompress=False
```

**Root Cause Explanation:**

1. The Azure REST API returns responses with **gzip compression** (`Content-Encoding: gzip`).
2. The Azure SDK's `aiohttp` transport layer has `auto_decompress` set to `False` on the `aiohttp.ClientSession`.
3. However, the SDK's `ContentDecodePolicy` expects the response body to be already decompressed UTF-8 text.
4. Since the body is still gzip-compressed (raw bytes starting with `0x1f 0x8b` — the gzip magic number), the UTF-8 decoder fails at byte `0x8b`.

**In simpler terms:** Azure's SDK explicitly tells `aiohttp` "don't decompress automatically," but then the response pipeline tries to decode the still-compressed bytes as UTF-8 text — which fails.

### 6.3 Ask Copilot to Fix the Issue

Now, send the following detailed prompt to Copilot in **Agent mode**:

```
You are debugging an Azure AI Foundry agent runtime.

Error:
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x8b in position 1: 
invalid start byte

Trace through:
aiohttp → azure-core → ContentDecodePolicy → auto_decompress=False

Root cause:
Azure SDK explicitly sets auto_decompress=False on the aiohttp ClientSession,
but the response is gzip-encoded. The ContentDecodePolicy then tries to 
decode raw gzip bytes as UTF-8, which fails.

Goal:
Fix this issue in run_agent.py without breaking the Azure SDK request pipeline.

Constraints:
- Azure sets auto_decompress=False intentionally
- The response body IS gzip compressed
- We need to decompress it before the SDK tries to decode it
- The fix should be a safe monkey-patch or middleware, not a fork of azure-core

Fix the issue safely and explain the change. Apply the fix to run_agent.py.
```

### 6.4 The Fix

GitHub Copilot will generate a **patch** that intercepts the response and decompresses gzip content before the SDK's `ContentDecodePolicy` processes it. The fix typically looks like this:

```python
import gzip
from azure.core.pipeline.policies import SansIOHTTPPolicy

class DecompressPolicy(SansIOHTTPPolicy):
    """Middleware to decompress gzip responses before ContentDecodePolicy sees them."""
    
    def on_response(self, request, response):
        encoding = response.http_response.headers.get("Content-Encoding", "")
        if "gzip" in encoding.lower():
            raw = response.http_response.body()
            if raw[:2] == b'\x1f\x8b':  # gzip magic number
                decompressed = gzip.decompress(raw)
                response.http_response._body = decompressed
                # Remove the Content-Encoding header to prevent double decompression
                if "Content-Encoding" in response.http_response.headers:
                    del response.http_response.headers["Content-Encoding"]
```

> [!NOTE]
> The exact implementation may vary depending on what Copilot generates. The key principle is:
> 1. Intercept the response before `ContentDecodePolicy` processes it
> 2. Check if the body starts with gzip magic bytes (`0x1f 0x8b`)
> 3. Decompress the body
> 4. Replace the raw body with the decompressed content

### 6.5 Apply the Fix

1. GitHub Copilot in **Agent mode** will propose changes to `run_agent.py`.
2. Review the proposed changes carefully.
3. Click **Accept** to apply the fix.
4. Copilot may also need to add the `gzip` import and register the policy in the client pipeline.

---

## Step 7: Run the Agent Successfully

After applying the fix, run the agent again:

```bash
python run_agent.py
```

**Expected output:** The agent should now successfully:
1. Connect to Azure AI Foundry
2. Create the agent with Azure AI Search tool
3. Process the hardcoded user query
4. Retrieve relevant compliance documents
5. Generate a structured compliance report

**Example successful output:**

```
## Compliance Compass Report

**Scenario:** Vendor risk assessment for AI analytics vendor in Singapore
**Generated:** March 18, 2026
**Confidence:** High

### Risk Overview
- **Risk Score:** 7 / 10 (High)
- **Risk Level:** High
- The scenario involves cross-border processing of customer transaction data, 
  triggering RBI data localization requirements and potential GDPR implications.

### Key Regulatory Findings
- **RBI Data Localization:** Payment data must be stored in India. Processing 
  abroad is permitted during the transaction phase only.
- **DPDP Act 2023:** Transfer of personal data outside India requires consent 
  and compliance with Section 16 provisions.

### Retrieved Knowledge Base References
- RBI Data Localization Guidelines: "All data relating to payment systems must 
  be stored in a system only in India."
- DPDP Act 2023: "The Central Government may restrict transfer of personal data 
  to such country or territory outside India as notified."

### Recommended Actions
**Immediate Actions:**
- Conduct a data residency assessment for the Singapore vendor
- Add contractual clauses requiring Indian data storage

**Medium-Term Actions:**
- Perform a vendor cybersecurity audit under RBI vendor onboarding guidelines

**Escalation Option:**
- If the vendor cannot comply with data localization, consider India-based 
  infrastructure alternatives

### Next Steps
For further analysis, provide additional scenario details as needed.
```

---

## What You Learned About Copilot Debugging

This module demonstrated a **real-world debugging workflow** with GitHub Copilot:

| Step | What You Did | Copilot Feature |
|---|---|---|
| 1 | Pasted the error traceback | Agent mode context understanding |
| 2 | Asked for root cause analysis | Deep code tracing across libraries |
| 3 | Provided constraints for the fix | Structured prompt engineering |
| 4 | Applied the generated fix | Agent mode file editing |
| 5 | Verified the fix works | Iterative debugging cycle |

**Key Insight:** The power of Copilot debugging comes from giving it **context** (the error), **constraints** (what cannot change), and a **goal** (what success looks like). This is how you *think* with Copilot, not just use it.

---

## Prerequisites Checklist

Before moving to Module V, confirm:

- [ ] Agent code exported from Foundry Toolkit for VS Code via **View Code**
- [ ] `.env` file configured with correct endpoint and model name
- [ ] Dependencies installed from `requirements.txt`
- [ ] Error diagnosed and fixed using GitHub Copilot (if encountered)
- [ ] Agent runs successfully from the command line
- [ ] Structured compliance report generated in terminal output

---

## Key Takeaways

- **View Code** in Foundry Toolkit for VS Code generates a complete, runnable agent project from your visual prototype.
- Real-world Azure SDK errors (like the gzip/UTF-8 decode issue) are common and can be systematically debugged with Copilot.
- **Structured prompts** for Copilot (error + trace + constraints + goal) produce better fixes than vague "fix this" requests.
- GitHub Copilot in **Agent mode** can read files, trace code paths, generate patches, and apply them — all in a single conversation.

---

Click **Next** to proceed to [Module V: Adding Interactive Input](./05_Interactive_Input.md).
