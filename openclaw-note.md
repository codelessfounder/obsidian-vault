## OpenClaw Knowledge Base Note

### Hybrid Model Configuration & Management

**The "Hybrid" Cost-Efficiency Strategy**
To balance intelligence and cost, OpenClaw is configured to use a high-reasoning model for orchestration and a lightweight model for repetitive sub-tasks.

- **Orchestrator (The Brain):** GPT-4o (Handles planning and logic).
- **Sub-agents (The Hands):** GPT-4o Mini (Handles 90% of utility: scraping, file formatting, fetching data).

**Benefit:** Reduces output costs by ~3x and utility costs by ~98% compared to GPT-5.5.

**Implementation Commands**
Run these in the terminal to apply the hybrid stack:

```bash
# Set primary orchestrator
openclaw config set agents.defaults.model.primary "openai/gpt-4o"

# Set sub-agents to budget model
openclaw config set agents.defaults.subagents.model "openai/gpt-4o-mini"
```

### Gateway Operations
The Gateway is the background daemon that manages Telegram webhooks, session memory, and tool execution.

**When to Restart (openclaw gateway restart)**
- Config Changes: After editing openclaw.json or changing models via CLI.
- Reboots: After a computer restart (if not set to auto-start).
- Ghosting: If the bot feels "stuck" on an old model or instruction set.

**Terminal Persistence**
- **Background Mode:** Use openclaw gateway start. You can safely close the terminal; Telegram will stay active.
- **Foreground/Debug Mode:** Use openclaw tui to talk to the agent locally or watch logs.

### Core Command Reference

| Category       | Command                   | Purpose                                       |
|---------------|---------------------------|-----------------------------------------------|
| System         | openclaw gateway status   | Check if the engine is running.               |
| System         | openclaw doctor           | Run diagnostics on config and connectivity.   |
| Interface      | openclaw tui              | Open the local Terminal User Interface.       |
| Session        | /reset or /new            | (In Telegram) Clears cache and forces new model rules. |
| Session        | /status                   | (In Telegram) Shows current model and token usage. |
| Config         | openclaw models list      | See all available API models.                 |

**Troubleshooting "Stuck" Models**
- If the bot is still responding as GPT-5.5 after a config change:
  - Restart Gateway: openclaw gateway restart
  - Clear Session: Type /reset in the Telegram chat.
  - Verify: Run openclaw doctor to ensure the "Runtime" matches the "Config File."
