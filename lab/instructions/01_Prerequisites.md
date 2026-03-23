# Module I — Prerequisites and Environment Setup

> [!NOTE]
> **Duration:** ~10 minutes
> Ensure all tools and accounts are configured before proceeding to the next module.

---

## Objectives

- Install and verify all required tools
- Authenticate with Azure using the Azure CLI
- Confirm GitHub Copilot access in VS Code
- Validate the AI Toolkit extension is installed

---

## Step 1: Required Software

Ensure the following software is installed on your machine. If any tool is missing, follow the installation link below.

| Tool | Version | Installation Link |
|---|---|---|
| **Visual Studio Code** | Latest | [Download VS Code](https://code.visualstudio.com/download) |
| **Python** | 3.10+ | [Download Python](https://www.python.org/downloads/) |
| **Azure CLI** | 2.60+ | [Install Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) |
| **Git** | Latest | [Install Git](https://git-scm.com/downloads) |
| **Docker Desktop** *(Optional — Module VII only)* | Latest | [Install Docker](https://www.docker.com/products/docker-desktop/) |

### Verify Installations

Open a terminal and run the following commands to verify each tool:

```bash
# Check Python version
python --version

# Check Azure CLI version
az version

# Check Git version
git --version

# Check Docker version (optional — needed for Module VII)
docker --version
```

**Expected output example:**

```
Python 3.11.7
azure-cli 2.67.0
git version 2.44.0.windows.1
Docker version 27.5.1
```

> [!IMPORTANT]
> Python 3.10 or higher is required. If you have multiple Python versions installed, ensure `python --version` returns 3.10+. On some systems, you may need to use `python3` instead of `python`.

---

## Step 2: VS Code Extensions

Install the following extensions in Visual Studio Code:

### Required Extensions

1. **GitHub Copilot** — AI-powered code completions and chat
   - Open VS Code → Extensions panel (`Ctrl+Shift+X`)
   - Search for `GitHub Copilot`
   - Click **Install**

2. **GitHub Copilot Chat** — Conversational AI assistant
   - Search for `GitHub Copilot Chat`
   - Click **Install**

3. **AI Toolkit for VS Code** — Agent builder and model playground
   - Search for `AI Toolkit`
   - Click **Install**
   - Publisher: **Microsoft**

4. **Python** — Python language support
   - Search for `Python`
   - Click **Install**
   - Publisher: **Microsoft**

### Verify Extensions

After installation, you should see:
- **GitHub Copilot** icon in the bottom-right status bar
- **AI Toolkit** icon in the left Activity Bar (looks like a chip/brain icon)

> [!TIP]
> After installation, verify the **GitHub Copilot** icon appears in the bottom-right status bar and the **AI Toolkit** icon (chip/brain icon) appears in the left Activity Bar. If you do not see the AI Toolkit icon, right-click on the Activity Bar and enable **AI Toolkit**.

---

## Step 3: Authenticate with Azure

The workshop requires an active Azure subscription with permissions to create resources.

1. Open a terminal in VS Code (`Ctrl+`` ` or **Terminal** → **New Terminal**).

2. Sign in to Azure:

   ```bash
   az login
   ```

   This will open a browser window. Sign in with your Azure account credentials.

3. After successful login, verify your subscription:

   ```bash
   az account show --query "{Name:name, SubscriptionId:id, TenantId:tenantId}" -o table
   ```

   **Expected output:**

   ```
   Name                                    SubscriptionId                        TenantId
   --------------------------------------  ------------------------------------  ------------------------------------
   Visual Studio Enterprise Subscription   xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx  xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
   ```

4. If you have multiple subscriptions, set the correct one:

   ```bash
   az account set --subscription "<Your Subscription Name>"
   ```

> [!IMPORTANT]
> If `az login` opens a device-code flow instead, follow the on-screen instructions to complete authentication:
> ```bash
> az login --use-device-code
> ```

---

## Step 4: Sign In to GitHub Copilot

1. Open GitHub Copilot Chat in VS Code:
   - Press `Ctrl+Alt+I` to open the Copilot Chat panel
   - Or click the **Copilot** icon in the Activity Bar

2. If prompted, sign in with your GitHub account that has an active **GitHub Copilot** subscription.

3. Verify Copilot is active:
   - Type a test message in the chat: `Hello, are you working?`
   - You should receive a response from GitHub Copilot

> [!NOTE]
> GitHub Copilot requires one of the following:
> - **GitHub Copilot Individual** subscription
> - **GitHub Copilot Business** subscription (managed by your organization)
> - **GitHub Copilot Enterprise** subscription
>
> If you do not have a subscription, you can start a free trial at [github.com/features/copilot](https://github.com/features/copilot).

---

## Step 5: Sign In to AI Toolkit

1. Click the **AI Toolkit** icon in the VS Code Activity Bar (left sidebar).

2. You will see the AI Toolkit panel with sections like:
   - **Local Resources**
   - **Compliance-Sentinel** (your Foundry project — will appear after Module II)

3. Click **Sign in to Azure** if prompted, and select the same Azure account used in Step 3.

4. After signing in, you should see your Foundry project and connected resources.

> After signing in, expand the AI Toolkit panel — you should see your Foundry project (e.g., **Compliance-Sentinel**) with sections for **Models**, **Prompt Agents**, **Workflows**, **Tools**, and **Knowledge**.

---

## Step 6: Clone the Workshop Repository

1. Open a terminal in VS Code.

2. Navigate to your preferred working directory:

   ```bash
   cd C:\Users\%USERNAME%\Favorites
   ```

3. Clone the repository:

   ```bash
   git clone https://github.com/ADKWDHQWQHDQI/Agent-using-GHCP.git
   ```

4. Open the cloned repository in VS Code:

   ```bash
   cd Agent-using-GHCP
   code .
   ```

> [!TIP]
> If you already have the workspace open, you can skip this step.

---

## Step 7: Verify the Knowledge Base Documents

The repository includes 12 compliance documents in the `kb_markdown/` folder. Verify they are present:

```bash
ls kb_markdown/
```

**Expected output:**

```
DPDP_Act_India_2023.md
EU_China_Data_Flows_2024.md
Export_Control_US_EU_India_2025.md
GDPR_Article_44_Transfers.md
GDPR_Schrems_II_Post_2020.md
Incident_Response_Best_Practices.md
Mitigation_Templates_DPA.md
RBI_Cross_Border_Transactions_Circular_2023.md
RBI_Data_Localization_2018_Guidelines.md
RBI_Vendor_Onboarding_Risk_2024.md
Risk_Scoring_Framework.md
SEBI_Insider_Trading_Policy.md
```

These documents will be uploaded to Azure Blob Storage in Module II.

---

## Prerequisites Checklist

Before moving to Module II, confirm:

- [ ] Python 3.10+ installed and verified
- [ ] Azure CLI installed and authenticated (`az login`)
- [ ] VS Code installed with all required extensions
- [ ] GitHub Copilot signed in and responding
- [ ] AI Toolkit extension installed and signed in with Azure
- [ ] Workshop repository cloned and opened in VS Code
- [ ] 12 KB Markdown documents present in `kb_markdown/`

---

## Key Takeaways

- A properly configured environment is essential before building AI agents.
- Azure CLI authentication enables programmatic access to Azure resources from your local machine.
- The AI Toolkit extension bridges VS Code with Azure AI Foundry, allowing you to design and manage agents visually.
- GitHub Copilot Agent mode will be your primary tool for coding, debugging, and extending the compliance agent.

---

Click **Next** to proceed to [Module II: Provisioning Azure Resources](./02_Azure_Resources.md).
