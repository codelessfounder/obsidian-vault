
### CORE CLI COMMANDS:

- `openclaw gateway` — Starts the main server daemon (`--port` to change port).
    
- `openclaw gateway start|stop|restart` — Runs/manages the server in the background.
    
- `openclaw channels login` — Generates QR code to link WhatsApp.
    
- `openclaw channels add` — Connects a bot (`--token` for Telegram/Discord/Slack).
    
- `openclaw channels status --probe` — Tests connection health of active chat apps.
    
- `openclaw onboard` — Runs setup wizard (`--install-daemon` for auto-boot).
    
- `openclaw doctor` — System diagnostics (`--deep` to auto-fix errors).
    
- `openclaw config get|set|unset` — Reads/writes global settings variables.
    
- `openclaw models list|set|status` — Switches LLMs and checks API key status.
    
- `openclaw models auth setup-token` — Handles Anthropic API key authentication.
    

### ⚙️ Global Flags (Append to any command)

- `--dev` — Uses isolated sandbox environment (`~/.openclaw-dev`).
    
- `--profile <name>` — Loads a separate custom config profile.
    
- `--json` — Outputs clean JSON instead of text (ideal for pipeline integration like `n8n`).
    
- `--no-color` — Strips ANSI colors from terminal output.
    

## 💬 CHANNEL MANAGEMENT

- **WHATSAPP** (`channels login`) — Links account via terminal QR code scan.
    
- **TELEGRAM** (`channels add --channel telegram`) — Connects via Botfather token.
    
- **DISCORD** (`channels add --channel discord`) — Connects via Discord developer token.
    
- **IMESSAGE** (`macOS bridge`) — Hooks directly into native Mac iMessage database.
    
- **SLACK** (`channels add --channel slack`) — Connects via Slack App bot token.
    

## 📂 WORKSPACE ANATOMY (`~/.openclaw/workspace`)

- `AGENTS.md` — **System Prompts**: Core logic, operational boundaries, and rules.
    
- `SOUL.md` — **Persona**: Behavioral traits, tone of voice, and speech cadence.
    
- `USER.md` — **User Profile**: Your personal preferences, habits, and background data.
    
- `IDENTITY.md` — **Branding**: Bot name, custom styling, and UI themes.
    
- `MEMORY.md` — **Long-Term Memory**: Persistent, high-level structural facts.
    
- `memory/YYYY-MM-DD.md` — **Daily Logs**: Automated chronological conversation history.
    
- `HEARTBEAT.md` — **Checklist**: Validation routines evaluated during background tasks.
    
- `BOOT.md` — **Startup**: Automation scripts executed instantly on server boot.
    

## ⚡ IN-CHAT SLASH COMMANDS (Bypasses LLM)

- `/status` — Prints system health and currently active context.
    
- `/context list` — Shows exactly which files/memories are fed into the current prompt.
    
- `/model <m>` — Quick-swaps the active AI model mid-chat.
    
- `/compact` — Prunes older messages from history to free up token context window.
    
- `/new` — Clears all current chat history to start a fresh session.
    
- `/stop` — Hard-kills a running generation cycle or infinite loop.
    
- `/tts on|off` — Toggles Audio/Speech generation on the fly.
    
- `/think` — Toggles visibility of deep reasoning tokens (e.g., for debugging).
    

## 🗺️ ESSENTIAL PATH MAP

- `~/.openclaw/openclaw.json` — **Main Config**: Global API keys and flags.
    
- `~/.openclaw/workspace/` — **Workspace Directory**: Location of active markdown persona files.
    
- `~/.openclaw/agents/<cid>/` — **Session States**: History data unique to individual chat IDs.
    
- `~/.openclaw/credentials/` — **Auth Tokens**: Encrypted API keys and platform access tokens.
    
- `~/.openclaw/memory/<cid>.sqlite` — **Vector DB**: Local RAG semantic memory file.
    
- `~/.openclaw/skills/` — **Global Tools**: Custom tools/code shared across all instances.
    
- `/tmp/openclaw/x.log` — **Server Logs**: Raw runtime output logs for backend debugging.
    

## 🔧 TROUBLESHOOTING PLAYBOOK

- **No DM Reply** ➡️ Run `PAIRING LIST -> APPROVE` (Whitelist inbound user ID).
    
- **Silent in Group** ➡️ Fix `MENTIONPATTERNS CONFIG` (Regex for bot mentions is broken).
    
- **Auth Expired** ➡️ Run `MODELS AUTH SETUP-TOKEN` (Refresh expired API handshakes).
    
- **Gateway Down** ➡️ Run `DOCTOR --DEEP` (Cleans lockfiles and restarts broken daemons).
    
- **Memory Bug** ➡️ Run `MEMORY INDEX` (Rebuilds and repairs corrupted SQLite vectors).
    

## 🌐 AUTOMATION & RESEARCH

- **BROWSER** (`browser start/screenshot`) — Launches headless browser to scrape pages/capture UI.
    
- **SUBAGENTS** (`/subagents list/info`) — Deploys/tracks child agents executing background jobs.
    
- **CRON JOBS** (`cron list/run <id>`) — Manages scheduled automations and periodic scripts.
    
- **HEARTBEAT** (`heartbeat.every: "30s"`) — Dictates frequency of background task evaluations.
    

## 🔊 VOICE & TTS

- **OpenAI / ElevenLabs** — Paid, premium-quality synthetic voice engines.
    
- **Edge TTS (Free)** — Built-in, zero-cost voice engine (no API key needed).
    
- `messages.tts.auto: "always"` — Forces audio generation for _all_ out-bound messages.