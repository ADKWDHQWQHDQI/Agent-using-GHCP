# Module VII — Containerization and Testing *(Optional)*

> [!NOTE]
> **Duration:** ~15 minutes
> **This module is fully optional.** Part A (Docker containerization) requires Docker Desktop and preparation for production deployment. Part B (structured testing) is a standalone activity you can do independently of Docker.
> Skip to [Part B: Structured Testing](#part-b-structured-testing) if you do not have Docker Desktop installed.

---

## Objectives

- *(Optional)* Use GitHub Copilot Agent mode to generate a Dockerfile for the Streamlit application
- *(Optional)* Build and run the Docker container locally
- Generate structured test scenarios to evaluate agent quality
- Refine the agent instructions in AI Toolkit based on test results

---

## Part A: Containerization with Docker *(Optional)*

> [!NOTE]
> **Part A requires Docker Desktop.** If Docker Desktop is not installed, skip ahead to [Part B: Structured Testing](#part-b-structured-testing).

### Step 1: Generate the Dockerfile with Copilot

1. Open **GitHub Copilot Chat** (`Ctrl+Alt+I`).

2. Switch to **Agent mode**.

3. Ensure `app_ui.py` and `requirements.txt` are referenced as context.

4. Send the following prompt:

   ```
   Generate a production-ready Dockerfile for the Compliance Compass 
   Streamlit application.

   Requirements:
   - Base image: python:3.11-slim
   - Working directory: /app
   - Copy requirements.txt first and install dependencies (for Docker 
     layer caching)
   - Copy all application files (app_ui.py, run_agent.py, .env, and 
     any other necessary files)
   - Expose port 8501 (Streamlit default)
   - Set environment variables:
     - PYTHONUNBUFFERED=1
     - STREAMLIT_SERVER_PORT=8501
     - STREAMLIT_SERVER_ADDRESS=0.0.0.0
   - Health check: curl the Streamlit health endpoint
   - Entry point: streamlit run app_ui.py
   
   Security requirements:
   - Do NOT copy .env into the image (use runtime environment variables 
     or Docker secrets instead)
   - Create a non-root user to run the application
   - Use --no-cache-dir for pip install
   - Pin the base image to a specific digest if possible
   
   Also generate a .dockerignore file that excludes:
   - __pycache__/
   - *.pyc
   - .env
   - .git/
   - .venv/
   - kb_markdown/ (documents are in Azure, not needed in container)
   - kb_source_pdfs/
   - img/
   - lab/
   - *.md (except for documentation needed at runtime)
   - explore/
   
   Save the Dockerfile in the same directory as app_ui.py.
   ```

5. Review and accept the generated files:
   - **`Dockerfile`**
   - **`.dockerignore`**

---

### Step 2: Review the Generated Dockerfile

The generated Dockerfile should look similar to:

```dockerfile
# === Build Stage ===
FROM python:3.11-slim AS base

# Set environment variables
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    STREAMLIT_SERVER_PORT=8501 \
    STREAMLIT_SERVER_ADDRESS=0.0.0.0

# Create non-root user
RUN groupadd --gid 1000 appuser && \
    useradd --uid 1000 --gid 1000 --create-home appuser

# Set working directory
WORKDIR /app

# Install dependencies first (layer caching)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application files
COPY app_ui.py .
COPY run_agent.py .

# Switch to non-root user
USER appuser

# Expose Streamlit port
EXPOSE 8501

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=15s --retries=3 \
    CMD curl -f http://localhost:8501/_stcore/health || exit 1

# Entry point
ENTRYPOINT ["streamlit", "run", "app_ui.py"]
```

> [!IMPORTANT]
> Notice that `.env` is **NOT** copied into the image. Environment variables (`PROJECT_ENDPOINT`, `MODEL_DEPLOYMENT_NAME`) must be provided at runtime using `docker run -e` or a Docker Compose `.env` file. This is a security best practice — credentials should never be baked into container images.

---

### Step 3: Build the Docker Image

1. Open a terminal in the project directory.

2. Build the image:

   ```bash
   docker build -t compliance-compass:latest .
   ```

3. Verify the image was created:

   ```bash
   docker images | findstr compliance-compass
   ```

   **Expected output:**

   ```
   compliance-compass   latest   abc123def456   10 seconds ago   450MB
   ```

---

### Step 4: Run the Docker Container

1. Run the container, passing your Azure credentials as environment variables:

   ```bash
   docker run -d ^
     --name compliance-compass ^
     -p 8501:8501 ^
     -e PROJECT_ENDPOINT="https://<your-foundry-hub>.services.ai.azure.com/api/projects/<your-project>" ^
     -e MODEL_DEPLOYMENT_NAME="gpt-4o" ^
     -e AZURE_TENANT_ID="<your-tenant-id>" ^
     -e AZURE_CLIENT_ID="<your-client-id>" ^
     -e AZURE_CLIENT_SECRET="<your-client-secret>" ^
     compliance-compass:latest
   ```

   > [!NOTE]
   > For local development, you can alternatively mount your Azure credentials:
   > ```bash
   > docker run -d ^
   >   --name compliance-compass ^
   >   -p 8501:8501 ^
   >   -e PROJECT_ENDPOINT="<your-endpoint>" ^
   >   -e MODEL_DEPLOYMENT_NAME="gpt-4o" ^
   >   -v %USERPROFILE%\.azure:/home/appuser/.azure:ro ^
   >   compliance-compass:latest
   > ```
   > This mounts your local Azure CLI credentials into the container so `DefaultAzureCredential` can use them.

2. Check the container is running:

   ```bash
   docker ps
   ```

3. Open `http://localhost:8501` in your browser.

4. Test the application with a compliance query.

### Troubleshooting with Copilot

If the container fails to start, check the logs:

```bash
docker logs compliance-compass
```

Then share the error with Copilot:

```
The Docker container for the Compliance Compass Streamlit app fails with 
this error: [paste error]. The Dockerfile and app_ui.py are in context. 
Diagnose and fix the issue.
```

---

## Part B: Agent Quality Testing (Optional)

> [!NOTE]
> This section is optional. It teaches how to systematically evaluate and improve the agent's response quality using GitHub Copilot.

### Step 5: Generate Test Scenarios with Copilot

1. Open **GitHub Copilot Chat** in **Agent mode**.

2. Send the following prompt:

   ```
   Generate a comprehensive test suite for the Compliance Compass agent. 
   Create a Python script called test_agent.py that tests the agent 
   with the following scenario categories:

   1. **Vendor Risk Assessment** (3 scenarios)
      - Singapore-based AI vendor processing payment data
      - US cloud provider handling employee personal data post-Schrems II
      - China-based manufacturing partner with access to proprietary tech

   2. **Cross-Border Data Transfer** (3 scenarios)
      - EU to India data transfer for payroll processing
      - India to US transfer of customer financial records
      - Multi-jurisdiction: data flowing EU → India → Singapore

   3. **Contract Clause Review** (2 scenarios)
      - Contract with "data stored in China" clause
      - Contract with "data may be transferred to any jurisdiction" clause

   4. **Edge Cases** (2 scenarios)
      - Query about a regulation NOT in the knowledge base (e.g., HIPAA)
      - Extremely vague query: "Is this compliant?"

   For each test scenario, the script should:
   - Send the query to the agent
   - Capture the response
   - Check for:
     a. Response is not empty
     b. Response contains a "Risk Score" (regex match for X/10 pattern)
     c. Response references specific KB documents
     d. Response contains "Recommended Actions" section
   - Print a pass/fail summary for each test
   - Generate an overall quality report at the end

   The script should reuse the same agent creation logic from run_agent.py.
   Output the results in a formatted table.
   ```

3. Review and accept the generated `test_agent.py`.

---

### Step 6: Run the Test Suite

1. Run the test suite:

   ```bash
   python test_agent.py
   ```

2. Review the output. You will see a table like:

   ```
   ═══════════════════════════════════════════════════════════════════
                    Compliance Compass — Test Results
   ═══════════════════════════════════════════════════════════════════
   #   Category          Scenario                      Result  Score
   ─── ────────────────  ────────────────────────────── ─────── ─────
   1   Vendor Risk       Singapore AI vendor            PASS    7/10
   2   Vendor Risk       US cloud post-Schrems II       PASS    6/10
   3   Vendor Risk       China manufacturing partner    PASS    8/10
   4   Cross-Border      EU to India payroll            PASS    5/10
   5   Cross-Border      India to US financial          PASS    6/10
   6   Cross-Border      Multi-jurisdiction flow        PASS    8/10
   7   Contract Review   Data stored in China           PASS    8/10
   8   Contract Review   Any jurisdiction clause        PASS    9/10
   9   Edge Case         HIPAA query (not in KB)        PASS    N/A
   10  Edge Case         Vague query                    WARN    N/A
   ═══════════════════════════════════════════════════════════════════
   Overall: 9/10 PASS | 1/10 WARN | 0/10 FAIL
   ```

---

### Step 7: Refine Instructions Based on Test Results (Optional)

If certain test scenarios produce unsatisfactory results:

1. Open the **AI Toolkit Agent Builder** in VS Code.

2. Load the saved `ComplianceAgent`.

3. Modify the **Instructions** based on the test findings. For example:

   - If the agent does not mention risk scores consistently, add: *"Always include a numerical risk score (X/10) in every report."*
   - If edge cases produce hallucinated regulations, add: *"If the knowledge base does not contain relevant information for a query, explicitly state this limitation. Never fabricate regulatory references."*

4. Re-test in the **Playground** and re-run `test_agent.py` to verify improvements.

5. Save the updated agent to Foundry.

> [!TIP]
> This iterative cycle — **Test → Identify Gaps → Refine Instructions → Re-test** — is the standard approach for improving agent quality in production RAG systems.

---

## Workshop Complete! 🎉

Congratulations! You have successfully built the **Compliance Compass** agent from scratch:

| Module | What You Built |
|---|---|
| **I** | Set up the development environment |
| **II** | Provisioned Azure resources (Foundry, Storage, AI Search) |
| **III** | Designed the agent visually in AI Toolkit |
| **IV** | Exported code and debugged a real Azure SDK error with Copilot |
| **V** | Extended the agent with interactive CLI input |
| **VI** | Built a professional Streamlit web UI |
| **VII** | Containerized the application and tested agent quality |

### Architecture Recap

```
Azure = Brain (Models + Search)
  └── GPT-4o: reasoning and report generation
  └── Embedding model: document vectorization
  └── Azure AI Search: compliance document retrieval
  └── Blob Storage: document storage

AI Toolkit = Agent Designer
  └── Visual agent builder with Playground
  └── Tool integration (Azure AI Search)
  └── Save/export to Foundry

GitHub Copilot = Builder + Debugger + Extender
  └── Diagnosed and fixed Azure SDK runtime errors
  └── Generated interactive input loop
  └── Created complete Streamlit web UI
  └── Generated production Dockerfile
  └── Generated test scenarios for quality evaluation
```

---

## Cleanup (Optional)

To avoid incurring costs, delete the Azure resources after the workshop:

```bash
az group delete --name compliance-agent-rg --yes --no-wait
```

> [!IMPORTANT]
> This will permanently delete all resources in the `compliance-agent-rg` Resource Group, including the AI Foundry hub, deployed models, storage account, and AI Search service.

To stop and remove the Docker container:

```bash
docker stop compliance-compass
docker rm compliance-compass
docker rmi compliance-compass:latest
```

---

## Next Steps

- **Deploy to Azure Container Apps** — Use GitHub Copilot to generate a deployment script for Azure Container Apps or Azure App Service.
- **Add more KB documents** — Expand the Knowledge Base with additional regulatory documents (e.g., HIPAA, SOC 2, PCI DSS).
- **Integrate with CI/CD** — Use GitHub Actions to automate testing and deployment.
- **Add authentication** — Protect the Streamlit UI with Azure AD authentication.
- **Enhance the agent** — Add tools for web search, code interpreter, or custom APIs.

---

## Resources

| Resource | Link |
|---|---|
| Azure AI Foundry Documentation | [learn.microsoft.com/azure/ai-studio](https://learn.microsoft.com/azure/ai-studio) |
| AI Toolkit for VS Code | [code.visualstudio.com/docs/intelligentapps](https://code.visualstudio.com/docs/intelligentapps) |
| Azure AI Search | [learn.microsoft.com/azure/search](https://learn.microsoft.com/azure/search) |
| GitHub Copilot | [docs.github.com/copilot](https://docs.github.com/copilot) |
| Streamlit Documentation | [docs.streamlit.io](https://docs.streamlit.io) |

---

Thank you for completing the **Compliance Compass Workshop**! 🛡️
