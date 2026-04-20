# Module II — Provisioning Azure Resources

> [!NOTE]
> **Duration:** ~15 minutes
> In this module, you will set up all the Azure resources needed to power the Compliance Compass agent: AI Foundry (with models), Blob Storage (for documents), and Azure AI Search (for retrieval).

---

## Objectives

- Create a Resource Group to organize all workshop resources
- Deploy an AI Foundry hub and project with two models (GPT-4o for reasoning, text-embedding for search)
- Create a Storage Account with a Blob container and upload the compliance KB documents
- Set up Azure AI Search (Free tier) and create a knowledge index from the blob data
- Verify the search index with a test query

---

## Architecture of Azure Resources

```mermaid
graph TD
    RG[" Resource Group\ncompliance-agent-rg"]

    subgraph AIF[" AI Foundry Hub: Compliance-Sentinel"]
        GPT[" gpt-4o\nReasoning Model"]
        EMB[" compliance-embedding\ntext-embedding-ada-002"]
    end

    subgraph STO[" Storage Account: compliancekb"]
        BC[" Blob Container: kb-documents"]
        DOCS[" 12 Compliance\nMarkdown Files"]
        BC --> DOCS
    end

    subgraph AIS[" Azure AI Search: compliancesearch (Free)"]
        IDX[" Index: knowledgesource-index\n81 document chunks"]
    end

    RG --> AIF
    RG --> STO
    RG --> AIS
```

---

## Step 1: Create a Resource Group

A Resource Group is a logical container for all the Azure resources you will create.

### Option A: Azure Portal

1. Open the [Azure Portal](https://portal.azure.com).

2. In the search bar at the top, type **Resource groups** and select it.

3. Click **+ Create**.

4. Fill in the details:
   - **Subscription:** Select your subscription (e.g., `Visual Studio Enterprise Subscription – MPN`)
   - **Resource group name:** `compliance-agent-rg`
   - **Region:** Select a region that supports AI Foundry (e.g., `East US`, `East US 2`, or `Sweden Central`)

5. Click **Review + create** → **Create**.

### Option B: Azure CLI

```bash
# Set variables for the workshop (reused throughout this module)
RESOURCE_GROUP="compliance-agent-rg"
LOCATION="eastus2"

# Create the resource group
az group create --name $RESOURCE_GROUP --location $LOCATION
```

> [!TIP]
> Use a consistent region for all resources (e.g., `East US 2`). Some AI models are only available in specific regions. On **Windows CMD**, replace `$VARIABLE` with `%VARIABLE%`; on **PowerShell**, use `$Variable` directly.

---

## Step 2: Create an AI Foundry Hub and Project

AI Foundry is where you deploy the language model (GPT-4o) and embedding model that power the agent.

### 2.1 Create the AI Foundry Hub

#### Option A: Azure Portal

1. In the Azure Portal, search for **Azure AI Foundry** and select it.

2. Click **+ Create** → **Hub**.

3. Fill in the details:
   - **Subscription:** Your subscription
   - **Resource group:** `compliance-agent-rg`
   - **Region:** Same region as your Resource Group
   - **Name:** `Compliance-Sentinel`

4. Click **Review + create** → **Create**.

5. Wait for deployment to complete, then click **Go to resource**.

#### Option B: Azure CLI

```bash
# Create the AI Foundry hub
az ml workspace create \
  --kind hub \
  --resource-group $RESOURCE_GROUP \
  --name "Compliance-Sentinel" \
  --location $LOCATION
```

### 2.2 Create a Project

#### Option A: Azure Portal

1. Inside the AI Foundry hub, click **+ New project**.

2. Enter the project name: `Compliance-Sentinel` (or keep the default).

3. Click **Create**.

#### Option B: Azure CLI

```bash
# Create a project under the hub
az ml workspace create \
  --kind project \
  --resource-group $RESOURCE_GROUP \
  --name "Compliance-Sentinel" \
  --hub-id /subscriptions/<subscription-id>/resourceGroups/$RESOURCE_GROUP/providers/Microsoft.MachineLearningServices/workspaces/Compliance-Sentinel
```

> [!NOTE]
> Replace `<subscription-id>` with your actual Azure subscription ID. You can retrieve it with:
> ```bash
> az account show --query id -o tsv
> ```

### 2.3 Deploy the GPT-4o Model

This model will be used for **reasoning** — it analyzes retrieved compliance documents and generates structured reports.

#### Option A: Azure Portal

1. In the AI Foundry portal, navigate to **Models** in the left sidebar.

2. Click **+ Deploy model** → **Deploy base model**.

3. Search for **gpt-4o** and select it.

4. Configure:
   - **Deployment name:** `gpt-4o`
   - **Model version:** Latest available
   - **Deployment type:** Standard

5. Click **Deploy**.

#### Option B: Azure CLI

```bash
# Deploy GPT-4o model
az ml online-deployment create \
  --resource-group $RESOURCE_GROUP \
  --workspace-name "Compliance-Sentinel" \
  --endpoint-name "gpt-4o" \
  --name "gpt-4o" \
  --model "azureml://registries/azureml-meta/models/gpt-4o" \
  --instance-type "Standard"
```

> [!TIP]
> Alternatively, you can deploy models through the [AI Foundry portal](https://ai.azure.com) under your project's **Deployments** section. The portal provides a visual interface for selecting model versions and configuring deployment parameters.

### 2.4 Deploy the Embedding Model

This model is used for **vectorizing the compliance documents** so Azure AI Search can perform semantic retrieval.

#### Option A: Azure Portal

1. Back in the **Models** section, click **+ Deploy model** → **Deploy base model**.

2. Search for **text-embedding-ada-002** (or **text-embedding-3-small**).

3. Configure:
   - **Deployment name:** `compliance-embedding`
   - **Model version:** Latest available
   - **Deployment type:** Standard

4. Click **Deploy**.

#### Option B: Azure CLI

```bash
# Deploy the embedding model
az ml online-deployment create \
  --resource-group $RESOURCE_GROUP \
  --workspace-name "Compliance-Sentinel" \
  --endpoint-name "compliance-embedding" \
  --name "compliance-embedding" \
  --model "azureml://registries/azureml-meta/models/text-embedding-ada-002" \
  --instance-type "Standard"
```

> After both models are deployed, verify they are listed under **Models** in the AI Foundry portal. You should see both `gpt-4o` (reasoning) and `compliance-embedding` (text-embedding-ada-002).

> [!NOTE]
> These two models will be used by the agent for document vectorization and reasoning respectively.

---

## Step 3: Create a Storage Account and Upload Documents

### 3.1 Create the Storage Account

#### Option A: Azure Portal

1. In the Azure Portal, search for **Storage accounts** and select it.

2. Click **+ Create**.

3. Fill in the details:
   - **Subscription:** Your subscription
   - **Resource group:** `compliance-agent-rg`
   - **Storage account name:** `compliancekb` (must be globally unique — append random digits if needed, e.g., `compliancekb1234`)
   - **Region:** Same as other resources
   - **Performance:** Standard
   - **Redundancy:** LRS (Locally Redundant Storage)

4. Click **Review + create** → **Create**.

#### Option B: Azure CLI

```bash
STORAGE_ACCOUNT="compliancekb"  # Must be globally unique; append digits if needed

az storage account create \
  --name $STORAGE_ACCOUNT \
  --resource-group $RESOURCE_GROUP \
  --location $LOCATION \
  --sku Standard_LRS \
  --kind StorageV2
```

### 3.2 Create a Blob Container

#### Option A: Azure Portal

1. Open the newly created storage account.

2. In the left sidebar, select **Containers** (under **Data storage**).

3. Click **+ Container**.

4. Enter the container name: `kb-documents`.

5. Set **Public access level** to **Private (no anonymous access)**.

6. Click **Create**.

#### Option B: Azure CLI

```bash
az storage container create \
  --name kb-documents \
  --account-name $STORAGE_ACCOUNT \
  --auth-mode login
```

### 3.3 Upload the Knowledge Base Documents

#### Option A: Azure Portal

1. Open the `kb-documents` container.

2. Click **Upload**.

3. Click **Browse for files** and navigate to the `kb_markdown/` folder in your workshop repository.

4. Select **all 12 Markdown files**:
   - `DPDP_Act_India_2023.md`
   - `EU_China_Data_Flows_2024.md`
   - `Export_Control_US_EU_India_2025.md`
   - `GDPR_Article_44_Transfers.md`
   - `GDPR_Schrems_II_Post_2020.md`
   - `Incident_Response_Best_Practices.md`
   - `Mitigation_Templates_DPA.md`
   - `RBI_Cross_Border_Transactions_Circular_2023.md`
   - `RBI_Data_Localization_2018_Guidelines.md`
   - `RBI_Vendor_Onboarding_Risk_2024.md`
   - `Risk_Scoring_Framework.md`
   - `SEBI_Insider_Trading_Policy.md`

5. Click **Upload**.

#### Option B: Azure CLI

```bash
# Upload all 12 KB documents from the local kb_markdown/ folder
az storage blob upload-batch \
  --account-name $STORAGE_ACCOUNT \
  --destination kb-documents \
  --source ./kb_markdown/ \
  --auth-mode login
```

**Verify the upload:**

```bash
az storage blob list \
  --account-name $STORAGE_ACCOUNT \
  --container-name kb-documents \
  --auth-mode login \
  --query "[].name" \
  --output table
```

Expected output — all 12 documents listed:

```
Result
-----------------------------------------
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

---

## Step 4: Create Azure AI Search and Build the Knowledge Index

Azure AI Search indexes the uploaded documents so the agent can retrieve relevant compliance policies when answering queries.

### 4.1 Create the Azure AI Search Resource

#### Option A: Azure Portal

1. In the Azure Portal, search for **Azure AI Search** and select it.

2. Click **+ Create**.

3. Fill in the details:
   - **Subscription:** Your subscription
   - **Resource group:** `compliance-agent-rg`
   - **Service name:** `compliancesearch` (must be globally unique)
   - **Location:** Same as other resources
   - **Pricing tier:** **Free** (sufficient for this workshop)

4. Click **Review + create** → **Create**.

5. Wait for deployment to complete.

#### Option B: Azure CLI

```bash
SEARCH_SERVICE="compliancesearch"  # Must be globally unique

az search service create \
  --name $SEARCH_SERVICE \
  --resource-group $RESOURCE_GROUP \
  --location $LOCATION \
  --sku free
```

**Verify the search service is running:**

```bash
az search service show \
  --name $SEARCH_SERVICE \
  --resource-group $RESOURCE_GROUP \
  --query "{Name:name, Status:status, Sku:sku.name}" \
  --output table
```

### 4.2 Create a Knowledge Base with Azure Blob as Source

Now link the AI Search to your Blob Storage to automatically index the compliance documents.

1. Navigate to your AI Foundry project in the [AI Foundry portal](https://ai.azure.com).

2. In the left sidebar, select **Knowledge** → **+ New knowledge base**.

3. Fill in the **Basics**:
   - **Name:** `compliance-kb` (or keep the auto-generated name)
   - **Description:** `Compliance regulatory knowledge base for vendor risk, data protection, and cross-border operations`

4. Under **Knowledge sources**, click **+ Create new**.

5. In the **Create knowledge source** popup, you will see multiple options (Azure blob, Search index, SharePoint, etc.). Select **Azure blob (Indexed)**.

6. Configure the Azure Blob source:
   - **Name:** Keep the auto-generated name (or enter `compliance-kb-source`)
   - **Subscription:** Your subscription
   - **Storage account:** `compliancekb`
   - **Blob container:** `kb-documents`
   - **Content extraction Mode:** `Minimal`

7. Scroll down and check **Enable text vectorization** if available, and select your embedding model deployment (`compliance-embedding`).

8. Click **Create**.

> [!NOTE]
> The indexing process may take 2–5 minutes to complete. The system will:
> - Connect to your Blob Storage
> - Extract text from each Markdown file
> - Chunk the text into smaller segments
> - Generate vector embeddings using the embedding model
> - Create a searchable index

### 4.3 Verify the Search Index

1. Navigate back to your **Azure AI Search** resource in the Azure Portal.

2. Click on **Indexes** in the left sidebar.

3. You should see a new index (e.g., `knowledgesource-1773330398864-index`).

4. Click on the index to open it. Verify the statistics:
   - **Documents:** ~81 (chunks from 12 documents)
   - **Total storage:** ~3.5 MB
   - **Vector index quota usage:** ~743 KB

### 4.4 Test the Retrieval

1. In the index page, click the **Search explorer** tab.

2. In the search box, enter a test query:

   ```
   RBI data localization payment data India
   ```

3. Click **Search**.

4. Verify that the results return relevant chunks from `RBI_Data_Localization_2018_Guidelines.md`.

> [!TIP]
> Try additional test queries:
> - `GDPR cross-border transfer safeguards SCCs`
> - `vendor onboarding risk assessment`
> - `insider trading compliance SEBI`
>
> Each should return relevant document chunks from the Knowledge Base.

---

## Step 5: Verify All Resources

### Option A: Azure Portal

Open your Resource Group (`compliance-agent-rg`) in the Azure Portal and verify that all resources are present:

| Resource | Type | Purpose |
|---|---|---|
| `Compliance-Sentinel` | AI Foundry Hub | Hosts models and agent |
| `gpt-4o` | Model Deployment | Reasoning model |
| `compliance-embedding` | Model Deployment | Embedding model for vectorization |
| `compliancekb` | Storage Account | Stores compliance documents |
| `compliancesearch` | Azure AI Search | Indexes and retrieves documents |

### Option B: Azure CLI

```bash
# List all resources in the resource group
az resource list \
  --resource-group compliance-agent-rg \
  --query "[].{Name:name, Type:type, Location:location}" \
  --output table
```

**Verify blob documents were uploaded:**

```bash
az storage blob list \
  --account-name $STORAGE_ACCOUNT \
  --container-name kb-documents \
  --auth-mode login \
  --query "length(@)" \
  --output tsv
```

Expected output: `12` (the total number of compliance documents).

---

## Prerequisites Checklist

Before moving to Module III, confirm:

- [ ] Resource Group `compliance-agent-rg` created
- [ ] AI Foundry hub `Compliance-Sentinel` created with a project
- [ ] GPT-4o model deployed
- [ ] Embedding model deployed
- [ ] Storage Account created with `kb-documents` container
- [ ] All 12 Markdown documents uploaded to the container
- [ ] Azure AI Search resource created (Free tier)
- [ ] Knowledge index created and populated (~81 documents)
- [ ] Test query in Search Explorer returns relevant results

---

## Key Takeaways

- **Azure AI Foundry** serves as the brain of the system — it provides both the reasoning model (GPT-4o) and the embedding model for vectorization.
- **Azure Blob Storage** acts as the document repository — a simple, scalable way to store compliance policies.
- **Azure AI Search** bridges the gap between raw documents and intelligent retrieval — it chunks, vectorizes, and indexes the content for fast semantic search.
- The **Free tier** of Azure AI Search is sufficient for prototyping RAG agents with small document sets.

---

Click **Next** to proceed to [Module III: Designing the Agent in Foundry Toolkit for VS Code](./03_Agent_Design.md).
