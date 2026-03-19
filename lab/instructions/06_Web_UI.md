# Module VI — Building a Professional Web UI

> [!NOTE]
> **Duration:** ~15 minutes
> In this module, you will use GitHub Copilot Agent mode to generate a complete web UI for the Compliance Compass agent using **Streamlit**. This transforms the command-line agent into a professional, browser-based application suitable for compliance teams.

---

## Objectives

- Use GitHub Copilot Agent mode to generate a complete Streamlit web application
- Create a professional chat interface with compliance branding
- Integrate the existing agent logic with the web UI
- Test the application in the browser with real compliance scenarios

---

## Step 1: Generate the Web UI with Copilot

1. Open **GitHub Copilot Chat** (`Ctrl+Alt+I`).

2. Switch to **Agent mode** using the mode selector.

3. Ensure `run_agent.py` (or `run_agent_interactive.py`) is referenced as context.

4. Send the following detailed prompt:

   ```
   Using the Compliance Compass agent code in run_agent.py as the foundation, 
   create a complete web-based chat UI for the compliance agent.

   Requirements:
   - Use Streamlit as the UI framework
   - Create the UI file as app_ui.py in the same directory as run_agent.py
   
   UI Design:
   - Professional, clean design suitable for an enterprise compliance tool
   - Header with "🛡️ Compliance Compass" branding and a subtitle: 
     "Regulatory Risk Assessment & Policy Analysis"
   - Sidebar with:
     - "About" section explaining what the tool does
     - "Sample Queries" section with 3-4 clickable example prompts:
       1. "Assess vendor risk for an AI company in Singapore processing 
          payment data"
       2. "GDPR compliance requirements for transferring data to China"
       3. "Review contract clause: Customer data stored on servers in 
          Frankfurt with backups in Mumbai"
       4. "What RBI regulations apply to third-party fintech vendors?"
     - "Session Info" showing the number of queries in the current session
   
   Chat Interface:
   - Full chat history display with user messages and agent responses
   - Agent responses should render Markdown (headers, bold, lists, tables)
   - User input text box at the bottom with a "Send" button
   - Loading spinner with message "Analyzing compliance scenario..." 
     while the agent processes
   - Each response should show a timestamp
   
   Functionality:
   - Maintain conversation context across messages using the same thread
   - Clicking a sample query in the sidebar should populate the input 
     and send it
   - Add a "Clear Chat" button to start a fresh session
   
   Technical:
   - Reuse the exact same agent creation logic, Azure AI Search tool 
     configuration, and any patches from run_agent.py
   - Use Streamlit session_state to maintain the agent, thread, and 
     chat history
   - Handle errors gracefully (show user-friendly messages)
   - Add the Azure authentication (DefaultAzureCredential) setup
   
   Also update requirements.txt to include streamlit as a dependency.
   ```

5. Copilot will generate the `app_ui.py` file and update `requirements.txt`.

6. Review each proposed change:
   - **`app_ui.py`** — Complete Streamlit application
   - **`requirements.txt`** — Updated with `streamlit` dependency

7. Click **Accept** to apply all changes.

---

## Step 2: Review the Generated UI Code

The generated `app_ui.py` should contain the following key sections:

### Page Configuration

```python
import streamlit as st
from datetime import datetime

st.set_page_config(
    page_title="Compliance Compass",
    page_icon="🛡️",
    layout="wide"
)
```

### Sidebar

```python
with st.sidebar:
    st.image("🛡️", width=50)  # or a logo
    st.title("Compliance Compass")
    st.markdown("---")
    
    st.subheader("📋 About")
    st.markdown("""
    Compliance Compass is a RAG-powered compliance agent that helps 
    risk teams evaluate regulatory requirements across jurisdictions.
    """)
    
    st.subheader("💡 Sample Queries")
    sample_queries = [
        "Assess vendor risk for an AI company in Singapore processing payment data",
        "GDPR compliance requirements for transferring data to China",
        "Review contract clause: Customer data stored on servers in Frankfurt with backups in Mumbai",
        "What RBI regulations apply to third-party fintech vendors?"
    ]
    for query in sample_queries:
        if st.button(query, key=f"sample_{hash(query)}"):
            st.session_state.pending_query = query
    
    st.markdown("---")
    st.subheader("📊 Session Info")
    st.metric("Queries This Session", st.session_state.get("query_count", 0))
```

### Chat Interface

```python
st.title("🛡️ Compliance Compass")
st.caption("Regulatory Risk Assessment & Policy Analysis")

# Display chat history
for message in st.session_state.get("messages", []):
    with st.chat_message(message["role"]):
        st.markdown(message["content"])
        if "timestamp" in message:
            st.caption(f"🕐 {message['timestamp']}")

# User input
if prompt := st.chat_input("Describe your compliance scenario..."):
    # Add user message to history
    # Send to agent
    # Display response with Markdown rendering
    pass
```

> [!NOTE]
> The exact code will vary based on what Copilot generates. The key elements are:
> - Streamlit session state for chat history and agent context
> - Markdown rendering for agent responses (compliance reports)
> - Sample queries in the sidebar for quick testing

---

## Step 3: Install Dependencies and Run the UI

1. Install the updated dependencies:

   ```bash
   pip install -r requirements.txt
   ```

   This will install `streamlit` and any other new dependencies.

2. Run the Streamlit application:

   ```bash
   streamlit run app_ui.py
   ```

3. Streamlit will display a URL in the terminal:

   ```
   Local URL: http://localhost:8501
   Network URL: http://192.168.x.x:8501
   ```

4. Open the URL in your browser (`http://localhost:8501`).

   > You should see the Compliance Compass web application with a sidebar (About, Sample Queries, Session Info) and a main chat area with the header "🛡️ Compliance Compass".

---

## Step 4: Test the Web UI

### Test 1: Direct Input

1. In the chat input box at the bottom, type:

   ```
   Assessing risks for a new AI analytics vendor based in Singapore 
   that will process our customer transaction data. Are there any 
   RBI localization concerns?
   ```

2. Click **Send** (or press Enter).

3. You should see:
   - A loading spinner with "Analyzing compliance scenario..."
   - The agent's structured compliance report rendered as Markdown
   - Risk score, regulatory findings, references, and recommended actions

### Test 2: Sample Query from Sidebar

1. In the left sidebar, click one of the **Sample Queries** buttons.

2. The query should automatically populate and send.

3. Verify the agent responds with a relevant compliance report.

### Test 3: Follow-Up Query

1. After receiving the first response, type a follow-up:

   ```
   Based on the previous assessment, what specific DPA clauses should 
   we include in the vendor contract?
   ```

2. The agent should reference the previous conversation context and provide relevant DPA clauses from the Mitigation Templates document.

### Test 4: Multi-Jurisdiction Scenario

1. Enter a complex scenario:

   ```
   Our company (headquartered in India, with operations in EU and US) 
   is onboarding a cloud infrastructure vendor based in China. The vendor 
   will process: (1) customer payment data, (2) employee personal data, 
   and (3) proprietary manufacturing technology specifications. 
   What are all applicable regulatory risks?
   ```

2. The agent should produce a comprehensive report covering:
   - RBI data localization (payment data)
   - GDPR cross-border transfers (EU employee data to China)
   - DPDP Act (Indian personal data)
   - Export controls (manufacturing technology)

---

## Step 5: Troubleshooting the UI

If you encounter issues, use Copilot to troubleshoot:

### Issue: Agent Connection Error

```
The Streamlit app shows an error when trying to create the agent. 
The error is: "DefaultAzureCredential failed to retrieve a token."
Fix the authentication in app_ui.py. I am logged in with az login.
```

### Issue: Chat History Not Persisting

```
The chat history resets after each message in the Streamlit app. 
Ensure st.session_state is correctly managing the message history 
and the agent thread ID persists across reruns. Fix app_ui.py.
```

### Issue: Markdown Not Rendering

```
The agent responses are showing raw Markdown text instead of 
rendered formatting. Ensure the agent responses are displayed 
using st.markdown() instead of st.text() or st.write(). 
Fix the display logic in app_ui.py.
```

> [!TIP]
> Streamlit reruns the entire script on each interaction. All state (agent, thread, messages) must be stored in `st.session_state` to persist across reruns.

---

## Prerequisites Checklist

Before moving to Module VII, confirm:

- [ ] `app_ui.py` created with Streamlit-based chat UI
- [ ] `requirements.txt` updated with `streamlit` dependency
- [ ] Application launches successfully at `http://localhost:8501`
- [ ] Chat interface displays with compliance branding
- [ ] Sample queries work from the sidebar
- [ ] Agent responses render as formatted Markdown
- [ ] Conversation context persists across messages
- [ ] Multiple test scenarios produce relevant compliance reports

---

## Key Takeaways

- GitHub Copilot Agent mode can generate a **complete web application** from a single detailed prompt — including layout, styling, session management, and backend integration.
- **Detailed UI requirements** (branding, sidebar contents, sample queries, Markdown rendering) produce better results than vague "create a UI" prompts.
- **Streamlit** is ideal for rapid prototyping of AI agent UIs — it handles chat interfaces, session state, and Markdown rendering with minimal code.
- The same agent logic from the command-line version is reused in the web UI — only the interaction layer changes.

---

Click **Next** to proceed to [Module VII: Containerization and Testing](./07_Containerize_Test.md).
