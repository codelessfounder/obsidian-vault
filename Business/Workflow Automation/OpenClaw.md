

OpenClaw is a hobby project and still in beta. Expect sharp edges.

By default, OpenClaw is a personal agent: one trusted operator boundary.
This bot can read files and run actions if tools are enabled. A bad prompt can trick it into doing unsafe things.

OpenClaw is not a hostile multi-tenant boundary by default.
If multiple users can message one tool-enabled agent, they share that delegated tool authority.

If you’re not comfortable with security hardening and access control, don’t run OpenClaw.
Ask someone experienced to help before enabling tools or exposing it to the internet.

**Recommended baseline**
- Pairing/allowlists + mention gating.
- Multi-user/shared inbox: split trust boundaries (ideally separate gateway/credentials, separate OS users/hosts).
- Sandbox + least-privilege tools.
- Shared inboxes: isolate DM sessions (session.dmScope: per-channel-peer) and keep tool access minimal.
- Keep secrets out of the agent’s reachable filesystem.
- Use the strongest available model for any bot with tools or untrusted inboxes.

**Run regularly**
`openclaw security audit --deep`
`openclaw security audit --fix`

**Learn more**
- [OpenClaw Docs](https://docs.openclaw.ai/gateway/security)

### Hybrid Model Configuration & Management

**The "Hybrid" Cost-Efficiency Strategy**
To balance intelligence and cost, OpenClaw is configured to use a high-reasoning model for orchestration and a lightweight model for repetitive sub-tasks.

- **Orchestrator (The Brain):** GPT-4o
- **Sub-agents (The Hands):** GPT-4o Mini

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
The Gateway manages Telegram webhooks, session memory, and tool execution.

**When to Restart (openclaw gateway restart)**
- Config Changes: After editing openclaw.json or changing models via CLI.
- Reboots: After a computer restart (if not set to auto-start).
- Ghosting: If the bot feels "stuck" on an old model or instruction set.

**Terminal Persistence**
- **Background Mode:** Use `openclaw gateway start`
- **Foreground/Debug Mode:** Use `openclaw tui`

### Core Command Reference

| Category       | Command                   | Purpose                                       |
|---------------|---------------------------|-----------------------------------------------|
| System         | openclaw gateway status   | Check if the engine is running.               |
| System         | openclaw doctor           | Run diagnostics.   |
| Interface      | openclaw tui              | Open the local Terminal User Interface.       |
| Session        | /reset or /new            | Clears cache. |
| Session        | /status                   | Shows current usage. |
| Config         | openclaw models list      | See all models.                 |

**Troubleshooting "Stuck" Models**
- Restart Gateway
- Clear Session
- Verify Configuration