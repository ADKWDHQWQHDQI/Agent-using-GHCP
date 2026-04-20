# Module III — Designing the Agent in Foundry Toolkit for VS Code

> [!NOTE]
> **Duration:** ~10 minutes
> In this module, you will use the Foundry Toolkit for VS Code extension in VS Code to design and prototype the Compliance Compass agent. You will configure the agent's name, model, instructions, and connect it to Azure AI Search for RAG retrieval. Finally, you will test the agent in the Playground and save it to Foundry.

---

## Objectives

- Open Foundry Toolkit for VS Code and connect to the Foundry project
- Create a new Prompt Agent with the appropriate model
- Write and refine the agent's system instructions
- Add Azure AI Search as a tool for document retrieval
- Test the agent in the Playground
- Save the agent to Microsoft Foundry

---

## Step 1: Open Foundry Toolkit for VS Code and Verify Connection

1. In VS Code, click the **Foundry Toolkit for VS Code** icon in the left Activity Bar.

2. In the Foundry Toolkit for VS Code panel, you should see:
   - **Local Resources**
   - **Compliance-Sentinel** (your Foundry project) under the project section

3. Expand **Compliance-Sentinel** to verify the following sections are visible:
   - **Models** — Should list `gpt-4o` and `compliance-embedding`
   - **Prompt Agents**
   - **Workflows**
   - **Hosted Agents (Preview)**
   - **Tools**
   - **Knowledge**
   You should see:
   - **Local Resources**
   - **Compliance-Sentinel** (your Foundry project) with subsections for **Models**, **Prompt Agents**, **Workflows**, **Hosted Agents (Preview)**, **Tools**, **Knowledge**, and **Classic**.

4. Expand **Models** to verify both deployed models are accessible:
   - `compliance-embedding`
   - `gpt-4o`

> [!TIP]
> If you do not see your models, click the **+** button next to **Models** to add a model from your Foundry Hub. Select the Azure AI Foundry connection and choose the models you deployed in Module II.

---

## Step 2: Create a New Prompt Agent

1. In the Foundry Toolkit for VS Code panel, navigate to **Prompt Agents**.

2. Click the **+** button to create a new agent.

3. The **Agent Builder** will open in a new tab with the **Playground** view.

### Configure Basic Information

4. Fill in the **BASIC INFORMATION** section:

   - **Agent name:** `ComplianceAgent`
   - **Model:** Select `gpt-4o` from the dropdown

---

## Step 3: Write the Agent Instructions

The **Instructions** field defines the agent's behavior, personality, and response format. This is the system prompt that guides every interaction.

### Option A: Write Instructions Manually

Enter the following instructions in the **Instructions** text area:

```
You are ComplianceAgent, a regulatory compliance and risk assessment assistant. 
You help compliance teams evaluate vendor risks, data protection requirements, 
and cross-border regulatory obligations.

When a user describes a compliance scenario, you must:
1. Identify the relevant jurisdictions and regulations.
2. Search the compliance knowledge base to retrieve applicable policies.
3. Analyze the risks based on retrieved documents.
4. Produce a structured compliance report.

Your output must always follow this format:

## Compliance Compass Report

**Scenario:** [Brief description of the scenario]
**Generated:** [Current date]
**Confidence:** [High/Medium/Low based on KB coverage]

### Risk Overview
- **Risk Score:** [X / 10]
- **Risk Level:** [Critical/High/Medium/Low]
- [Summary of key risks in 2-3 sentences]

### Key Regulatory Findings
- [List each applicable regulation with a brief finding]

### Retrieved Knowledge Base References
- [Quote relevant passages from retrieved documents with source attribution]

### Recommended Actions
**Immediate Actions:**
- [Action 1]
- [Action 2]

**Medium-Term Actions:**
- [Action 1]

**Escalation Option:**
- [If applicable, suggest escalation path]

### Next Steps
End with: "For further analysis, provide additional scenario details as needed."

# Rules:
- Strictly adhere to information from the retrieved compliance knowledge base.
- If retrieved documents do not cover the scenario, clearly state the limitation.
- Always provide source references for every claim.
- Never fabricate regulations or policy details.
- Risk scores must be justified based on the severity and number of regulatory conflicts found.
```

### Option B: Use the Generate Feature

Alternatively, you can write a brief description and let the AI generate polished instructions:

1. In the **Instructions** field, type a brief description:

   ```
   A compliance and risk assessment agent that helps evaluate vendor risks, 
   data protection requirements, and cross-border regulations. It retrieves 
   policies from a knowledge base and produces structured compliance reports 
   with risk scores, regulatory findings, and recommended actions.
   ```

2. Click the **Generate** button below the Instructions field.

3. The AI will expand your description into comprehensive system instructions.

4. Review the generated instructions and edit as needed to match the output format described above.

> [!TIP]
> The **Generate** feature uses a language model to transform your high-level description into detailed, well-structured instructions. This is especially useful when you are unsure about the exact wording for system prompts.

---

## Step 4: Add Azure AI Search as a Tool

This is the critical step that connects your agent to the compliance Knowledge Base for RAG retrieval.

1. Scroll down to the **TOOL** section in the Agent Builder.

2. Click **+** to add a new tool.

3. A **Select a tool** popup will appear with three tabs: **Configured**, **Catalog**, and **Custom**.

4. In the **Configured** tab, you will see the built-in tools:
   - **Web search**
   - **Code Interpreter**
   - **File Search**
   - **Grounding with Bing Search**
   - **Azure AI Search** ← Select this one

5. Click **Azure AI Search**, then click **Add Tool**.

### Connect to Your Search Index

6. In the **Connect to Azure AI Search index** dialog:

   - **Azure AI Search connection:** Select `compliancesearch` from the dropdown.

7. After selecting the connection, the available indexes will appear.

8. Select the index that was created in Module II (e.g., `knowledgesource-1773330398864-index`).

9. Click **Add**.

> [!NOTE]
> You also have the option to create a new index directly from the Foundry Toolkit for VS Code. If you click **Create New Azure AI Search Index**, you will see a form to:
> - Enter an **Index Name**
> - Select a **Storage account** and **Container**
> - Choose an **Embedding model deployment**
>
> For this workshop, we use the index already created in Module II.

---

## Step 5: Test the Agent in the Playground

Now test the agent to verify it correctly retrieves compliance documents and generates structured reports.

### Test 1: Vendor Risk Assessment

In the **Playground** chat panel (right side of Agent Builder), enter:

```
Assessing risks for a new AI analytics vendor based in Singapore that will 
process our customer transaction data. Are there any RBI localization concerns?
```

**Expected behavior:**
- The agent should invoke the Azure AI Search tool to retrieve relevant documents.
- The response should reference `RBI_Data_Localization_2018_Guidelines.md`.
- A structured report with a risk score should be generated.

### Test 2: Cross-Border Data Transfer

```
We are onboarding a cloud vendor based in China to handle customer personal data 
for our EU operations. What are the compliance risks?
```

**Expected behavior:**
- The agent should retrieve documents related to GDPR Article 44, EU-China data flows, and RBI data localization.
- The risk score should be high (7-9/10) due to multiple regulatory conflicts.

### Test 3: Contract Clause Review

```
Review this contract clause: "All customer financial data will be stored on 
servers located in Frankfurt, Germany, with backup copies in Mumbai, India." 
Are there any compliance issues?
```

**Expected behavior:**
- The agent should analyze the clause against GDPR and RBI requirements.
- It should note that the arrangement may be acceptable if proper safeguards are in place.

### Refining Instructions

If the agent's responses do not match the expected format or miss important policies:

1. Return to the **Instructions** field in the left panel.
2. Add more specific guidance (e.g., "Always check RBI data localization requirements when payment data is mentioned").
3. Re-test in the Playground.

> [!TIP]
> Iterate on the instructions until the agent consistently produces well-structured, policy-grounded reports. This is the core of prompt engineering for RAG agents.

---

## Step 6: Save the Agent to Foundry

Once you are satisfied with the agent's responses:

1. Click the **Save to Foundry** button at the top-right of the Agent Builder.

2. The agent configuration (name, model, instructions, tools) will be saved to your AI Foundry project.

3. After saving, you will see the agent listed under **Prompt Agents** in the Foundry Toolkit for VS Code panel.

> [!IMPORTANT]
> Saving to Foundry is a critical step — it persists your agent configuration in the cloud and enables the **View Code** feature you will use in Module IV.

---

## Prerequisites Checklist

Before moving to Module IV, confirm:

- [ ] Foundry Toolkit for VS Code connected to the Foundry project
- [ ] Agent `ComplianceAgent` created with `gpt-4o` model
- [ ] System instructions configured and tested
- [ ] Azure AI Search tool added with the compliance index
- [ ] Agent tested in the Playground with at least 2 test queries
- [ ] Agent saved to Foundry

---

## Key Takeaways

- **Foundry Toolkit for VS Code Agent Builder** provides a visual, no-code interface for designing AI agents with tools and instructions.
- **System instructions** (the prompt) define the agent's behavior — clear, structured instructions produce better outputs.
- **Azure AI Search as a tool** enables RAG retrieval — the agent searches the compliance Knowledge Base before generating responses.
- **The Playground** allows rapid iteration on instructions and tool configuration before moving to code.
- **Saving to Foundry** persists the agent configuration and enables code export.

---

Click **Next** to proceed to [Module IV: Exporting Code and Debugging with GitHub Copilot](./04_Code_Export_Debug.md).
