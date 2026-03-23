# Module V — Adding Interactive Input

> [!NOTE]
> **Duration:** ~10 minutes
> In this module, you will use GitHub Copilot to upgrade `run_agent.py` from a single hardcoded query into an interactive loop that accepts keyboard input — directly in the same file. This is the foundation for the web UI you will build in Module VI.

---

## Objectives

- Use GitHub Copilot Agent mode to modify `run_agent.py` in-place
- Replace the hardcoded query with a continuous interactive input loop
- Maintain conversation context across queries using the same thread
- Test the agent interactively before moving to the web UI

---

## Step 1: Understand the Current Limitation

The current `run_agent.py` has a **hardcoded user query** — it sends one pre-written message, prints the response, and exits. A real compliance agent must accept multiple queries from the user in a session, maintain conversation context, and handle exits gracefully.

This module upgrades `run_agent.py` itself. No new file is created — the same script that debugged in Module IV becomes the interactive agent.

---

## Step 2: Use Copilot to Add Interactive Input

1. Open **GitHub Copilot Chat** (`Ctrl+Alt+I`) and switch to **Agent mode**.

2. Open `run_agent.py` in the editor so it is in context, or reference it explicitly with `#file:run_agent.py`.

3. Send the following prompt:

   ```
   I am working on run_agent.py — the Azure AI Foundry compliance agent 
   that uses Azure AI Search for RAG retrieval.

   Modify run_agent.py in-place to replace the hardcoded query with an 
   interactive input loop. Do NOT create a new file.

   Requirements:

   1. WELCOME BANNER — Print this banner at startup before the loop:
      ╔══════════════════════════════════════════════════╗
      ║      🛡️  Compliance Compass Agent  🛡️            ║
      ║   Regulatory Risk Assessment & Policy Analysis   ║
      ╠══════════════════════════════════════════════════╣
      ║  Describe your compliance scenario to begin.     ║
      ║  Type 'exit' or press Ctrl+C to quit.            ║
      ╚══════════════════════════════════════════════════╝

   2. INTERACTIVE LOOP — After creating the agent and thread, enter 
      a loop that:
      - Prompts: "🔍 Compliance Query > "
      - Reads user input from stdin
      - Skips empty inputs silently (user just pressed Enter)
      - Sends the input to the agent on the existing thread
      - Waits for the run to complete (use create_and_process)
      - Prints the latest assistant message
      - Loops back for the next query

   3. CONVERSATION CONTEXT — Reuse the same thread.id for every message 
      in the session so follow-up queries have access to prior context.

   4. EXIT HANDLING — End the loop cleanly when:
      - User types "exit", "quit", or "bye" → print farewell message
      - User presses Ctrl+C → print farewell message
      Farewell: "Thank you for using Compliance Compass. Stay compliant! 👋"

   5. Keep all existing logic unchanged: agent creation, Azure AI Search 
      tool configuration, DefaultAzureCredential, and any gzip/decompression 
      patch already present in the file.

   Apply the changes directly to run_agent.py.
   ```

4. Review the diff Copilot proposes — you should see the hardcoded query block replaced with the interactive loop while everything above it stays the same.

5. Click **Accept** to apply the changes.

---

## Step 3: What Changed in run_agent.py

After Copilot applies the changes, the structure of `run_agent.py` should look like this:

```
run_agent.py
├── Imports (unchanged)
├── DecompressPolicy patch (unchanged, if present)
├── load_dotenv / credentials (unchanged)
├── Agent creation with Azure AI Search tool (unchanged)
├── Thread creation (unchanged)
├── print_banner()          ← NEW: prints the welcome banner
└── while True: loop        ← NEW: replaces single hardcoded query
    ├── input("🔍 Compliance Query > ")
    ├── skip empty input
    ├── exit check
    ├── client.agents.messages.create(thread_id=thread.id, ...)
    ├── client.agents.runs.create_and_process(...)
    └── print latest assistant message
```

> [!NOTE]
> The thread is created **once** before the loop. Every query in the session uses `thread_id=thread.id`, which preserves the full conversation history. This is what makes follow-up queries work.

---

## Step 4: Run and Test the Interactive Agent

```bash
python run_agent.py
```

You should see the banner, then the prompt:

```
╔══════════════════════════════════════════════════╗
║      🛡️  Compliance Compass Agent  🛡️            ║
║   Regulatory Risk Assessment & Policy Analysis   ║
╠══════════════════════════════════════════════════╣
║  Describe your compliance scenario to begin.     ║
║  Type 'exit' or press Ctrl+C to quit.            ║
╚══════════════════════════════════════════════════╝

🔍 Compliance Query >
```

### Test Scenario 1: Vendor Risk

```
🔍 Compliance Query > Assessing risks for a new AI analytics vendor based in 
Singapore that will process our customer transaction data. RBI concerns?
```

**Expected:** Structured compliance report with RBI data localization findings and risk score.

### Test Scenario 2: Follow-Up (Context Persistence)

Without restarting, immediately enter:

```
🔍 Compliance Query > Based on the previous assessment, what contract clauses 
should we include in the vendor agreement?
```

**Expected:** The agent references the Singapore scenario from the previous turn and suggests clauses from the Mitigation Templates KB document.

### Test Scenario 3: Cross-Border Transfer

```
🔍 Compliance Query > We are transferring EU customer personal data to our 
India headquarters for payroll processing. What GDPR safeguards are required?
```

**Expected:** References to GDPR Article 44, Schrems II SCCs, and DPDP Act provisions.

### Test Scenario 4: Exit

```
🔍 Compliance Query > exit
```

```
Thank you for using Compliance Compass. Stay compliant! 👋
```

---

## Step 5: Troubleshooting with Copilot

If the interactive loop has issues, share the error with Copilot in Agent mode:

| Symptom | Copilot Prompt |
|---|---|
| Follow-up queries lose context | `"The agent does not remember prior queries. Check that thread_id is reused across all messages in the loop in run_agent.py. Fix it."` |
| Empty response after query | `"The agent returns an empty response. Confirm that create_and_process is completing and that the response extraction is reading the latest assistant message. Fix run_agent.py."` |
| Response prints raw objects | `"The agent response is printing a raw object instead of text content. Fix the message extraction in the loop in run_agent.py to print message.content[0].text.value."` |

---

## Prerequisites Checklist

Before moving to Module VI, confirm:

- [ ] `run_agent.py` modified with interactive input loop (in-place, no new file)
- [ ] Welcome banner displays at startup
- [ ] Multiple queries accepted in sequence without restarting
- [ ] Conversation context persists (follow-up query works)
- [ ] Exit commands (`exit`, `quit`, `bye`) and Ctrl+C work cleanly

---

## Key Takeaways

- GitHub Copilot Agent mode can **surgically modify existing code** — the prompt specifies "modify in-place" and Copilot respects that constraint.
- Reusing the same **thread ID** across all queries is how you preserve conversation context in Azure AI Foundry agents.
- The interactive `run_agent.py` is now the foundation for the **Streamlit web UI** in Module VI — the agent logic stays identical, only the interaction layer changes.

---

Click **Next** to proceed to [Module VI: Building a Professional Web UI](./06_Web_UI.md).
- Add a continuous input loop that accepts user queries from the keyboard
- Add graceful exit handling and conversation context persistence
- Test the interactive agent with multiple compliance scenarios

---

## Step 1: Understand the Current Limitation

The current `run_agent.py` script has a **hardcoded user query**. When you run it, it:

1. Creates the agent
2. Sends a single pre-written query
3. Prints the response
4. Exits

This is fine for testing, but a real compliance agent needs to accept **multiple queries** in an interactive session.

---

## Step 2: Use Copilot to Add Interactive Input

1. Open **GitHub Copilot Chat** (`Ctrl+Alt+I`).

2. Switch to **Agent mode** using the mode selector.

3. Make sure `run_agent.py` is referenced as context (open it in the editor or use `#file:run_agent.py`).

4. Send the following detailed prompt:

   ```
   Modify run_agent.py to accept user input interactively instead of using 
   a hardcoded query. 

   Requirements:
   1. After creating the agent and thread, enter an interactive loop that:
      - Displays a prompt "🔍 Compliance Query > " and waits for user input
      - Sends the user's input to the agent
      - Prints the agent's response
      - Loops back to accept the next query
   
   2. The conversation should maintain context across queries within the 
      same session (use the same thread ID for all messages).
   
   3. Add graceful exit handling:
      - User can type "exit", "quit", or "bye" to end the session
      - Display a farewell message: "Thank you for using Compliance Compass. 
        Stay compliant! 👋"
      - Handle Ctrl+C gracefully with the same farewell message
   
   4. Add a welcome banner at the start:
      ```
      ╔══════════════════════════════════════════════════╗
      ║         🛡️  Compliance Compass Agent  🛡️         ║
      ║   Regulatory Risk Assessment & Policy Analysis   ║
      ╠══════════════════════════════════════════════════╣
      ║  Type your compliance scenario to get started.   ║
      ║  Type 'exit' to quit.                            ║
      ╚══════════════════════════════════════════════════╝
      ```
   
   5. Add input validation:
      - Skip empty inputs (just pressing Enter)
      - Strip whitespace from queries
   
   6. Save the interactive version as run_agent_interactive.py so the 
      original run_agent.py is preserved.

   Keep the same agent creation logic, Azure AI Search tool configuration, 
   and the gzip decompression fix (if present). Only change the query 
   execution section from a single hardcoded call to an interactive loop.
   ```

5. Review the changes Copilot proposes. You should see a new file `run_agent_interactive.py` being created.

6. Click **Accept** to apply the changes.

---

## Step 3: Review the Generated Code

The generated `run_agent_interactive.py` should include the following key sections:

### Welcome Banner

```python
def print_banner():
    print("╔══════════════════════════════════════════════════╗")
    print("║         🛡️  Compliance Compass Agent  🛡️         ║")
    print("║   Regulatory Risk Assessment & Policy Analysis   ║")
    print("╠══════════════════════════════════════════════════╣")
    print("║  Type your compliance scenario to get started.   ║")
    print("║  Type 'exit' to quit.                            ║")
    print("╚══════════════════════════════════════════════════╝")
    print()
```

### Interactive Loop

```python
# After agent and thread creation...
print_banner()

while True:
    try:
        user_input = input("🔍 Compliance Query > ").strip()
        
        if not user_input:
            continue
        
        if user_input.lower() in ("exit", "quit", "bye"):
            print("\nThank you for using Compliance Compass. Stay compliant! 👋")
            break
        
        # Send message to the agent using the same thread
        message = client.agents.messages.create(
            thread_id=thread.id,
            role="user",
            content=user_input
        )
        
        # Process the run and get response...
        run = client.agents.runs.create_and_process(
            thread_id=thread.id,
            agent_id=agent.id
        )
        
        # Retrieve and print the response...
        messages = client.agents.messages.list(thread_id=thread.id)
        # Print the latest assistant message
        
    except KeyboardInterrupt:
        print("\n\nThank you for using Compliance Compass. Stay compliant! 👋")
        break
```

> [!NOTE]
> The exact code structure will depend on what Copilot generates. The key elements are:
> - Same thread ID across all messages (conversation context persists)
> - Input validation and exit handling
> - Welcome banner display

---

## Step 4: Test the Interactive Agent

1. Run the interactive agent:

   ```bash
   python run_agent_interactive.py
   ```

2. You should see the welcome banner:

   ```
   ╔══════════════════════════════════════════════════╗
   ║         🛡️  Compliance Compass Agent  🛡️         ║
   ║   Regulatory Risk Assessment & Policy Analysis   ║
   ╠══════════════════════════════════════════════════╣
   ║  Type your compliance scenario to get started.   ║
   ║  Type 'exit' to quit.                            ║
   ╚══════════════════════════════════════════════════╝
   ```

### Test Scenario 1: Vendor Risk Assessment

Enter the following query:

```
🔍 Compliance Query > Assessing risks for a new AI analytics vendor based in Singapore that will process our customer transaction data. Are there any RBI localization concerns?
```

**Expected:** A structured compliance report with RBI data localization findings.

### Test Scenario 2: Follow-Up Query (Context Persistence)

Without restarting the agent, enter a follow-up query:

```
🔍 Compliance Query > Based on the previous assessment, what specific contract clauses should we include in the vendor agreement?
```

**Expected:** The agent should reference the previous Singapore vendor scenario and suggest clauses based on the mitigation templates and RBI vendor onboarding documents.

### Test Scenario 3: Cross-Border Transfer

```
🔍 Compliance Query > We are transferring customer personal data from our EU subsidiary to our India headquarters. What GDPR safeguards are required?
```

**Expected:** A report referencing GDPR Article 44, Schrems II, and Standard Contractual Clauses.

### Test Scenario 4: Exit

```
🔍 Compliance Query > exit
```

**Expected:**

```
Thank you for using Compliance Compass. Stay compliant! 👋
```

---

## Step 5: Troubleshooting with Copilot

If the interactive agent has issues (e.g., conversation context not persisting, responses being empty), use Copilot to troubleshoot:

```
The interactive agent is running but the follow-up query does not seem to 
reference the previous conversation. Check that the same thread ID is being 
used across all messages and that the message history is being maintained 
correctly. Fix the issue in run_agent_interactive.py.
```

> [!TIP]
> Common issues and their causes:
> - **No response:** The agent run may not be completing. Check that `create_and_process` is used instead of just `create`.
> - **Context lost:** Each query is creating a new thread. Ensure the same `thread.id` is reused.
> - **Formatting issues:** The response extraction may be printing raw message objects instead of text content.

---

## Prerequisites Checklist

Before moving to Module VI, confirm:

- [ ] `run_agent_interactive.py` created with interactive input loop
- [ ] Welcome banner displays correctly
- [ ] Multiple queries can be sent in sequence
- [ ] Conversation context persists across queries
- [ ] Exit commands (`exit`, `quit`, `bye`) work correctly
- [ ] Ctrl+C exits gracefully

---

## Key Takeaways

- GitHub Copilot Agent mode can **extend existing code** with new features from a single detailed prompt.
- **Detailed prompts** with numbered requirements produce better results than vague descriptions.
- Maintaining **thread/conversation context** across queries is essential for follow-up analysis in RAG agents.
- The original file is preserved (`run_agent.py`) while the new interactive version is saved separately — this is a good practice for incremental development.

---

Click **Next** to proceed to [Module VI: Building a Professional Web UI](./06_Web_UI.md).
