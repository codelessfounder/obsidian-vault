---
tags:
  - diary
  - stories
---

# Stories

## Stories (Merged)
1. Forgetting a piano song at a performance in front of the whole school (February, 2012)
2. I *almost* got stabbed in Narrabeen (April, 2024)
3. I got punched in the face by a girl after she asked me to pay to have sex with her (March, 2021)
4. Having to tell my mum that the best option for her right now is to go to Brazil for a few months (May, 2024)
5. Bike stolen after Jiu Jitsu and not getting the Luxury escapes job (April, 2024 - same day)
6. A software engineer promised to complete an MVP in exchnage for equity, only to never complete it
7. My ex-boss at a jewellers threatens to punch me. It was 1 year after I finished working there
8. I lived in Shanghai for 4 months to learn Mandarin
9. Buying a Mercedes B180 CDI for $2600 after not having a car for two years (May, 2025)

Codeless Founder:

10. Found out another startup was doing exactly the same thing as me (getbezel)
11. Raised $60,000 for Watchcrow @ $600,000 , pre-product and pre-revenue (2022)
12. Finding my first co-founder (Mike Basckin) for Discopay

price_1QLHJkFPCSr4PtFxIP773q7K

---

Mastery draft:

Harry was on a string of bad luck. The same night he got rejected from a four-stage product-role process, his bike was stolen outside his Jiu Jitsu gym.

He had spent investor capital on initiatives that never materialized. Despite support from his father through tuition and living costs, outcomes still lagged behind effort.

After inconsistent traction running a patient-acquisition agency, he shifted focus to building software products that created genuine customer value.

As AI entered the mainstream, he built an assistant for a social-justice organization and prepared to test its real impact.

An early company experience ended with paying $20,000 to a software firm that delivered nothing. A later rejection for a product role due to "lack of experience" became the catalyst to master app-building for first-time founders.

Novel seed:

The novel explores how family hardship emerges from broader political and economic forces, and why people who escape hardship often do not return to address the same burden for others.

---

## Founder / startup story seeds

1. Losing out on $240,000 investment, and the investor going missing
2. Losing 20,000 to an app agency who failed to deliver on our MVP
3. Relying on an engineer to build an app for me for 8 month
4. I spent 10k on terrible UI designs
5. Meeting Mike on reddit
6. Creating account for users without them knowing, then email notificaitons being sent to them

## Video ideas

7. I am not a successful founder
8. 5 mistakes I made so you don’t have to
9. Stigma around no-code
10. OpenAI documentation on prompt engineering

## Distribution channels

11. Instagram
12. Facebook
13. TikTok
14. Email
15. Reddit

---

## LE Presentation Notes (Merged)

- Booking process objective: improve conversion in tours/cruises by aligning search and comparison with customer preference patterns.
- Core problem: current flow over-standardizes outcomes and under-emphasizes preference-driven selection early in the journey.
- Tours hypothesis: users should select experience type earlier (the "what") before date/location narrowing.
- Cruise hypothesis: users need earlier, clearer comparison of price + perks/OBC bundles to improve confidence and completion.
- Measurement: use objective-led metrics (conversion, completion time, satisfaction signals, repeat behavior) and iterate with both qualitative + quantitative inputs.
## OpenClaw: Hybrid Model Configuration & Management

The "Hybrid" Cost-Efficiency Strategy

To balance intelligence and cost, OpenClaw is configured to use a high-reasoning model for orchestration and a lightweight model for repetitive sub-tasks.

Orchestrator (The Brain): GPT-4o (Handles planning and logic).

Sub-agents (The Hands): GPT-4o Mini (Handles 90% of utility: scraping, file formatting, fetching data).

Benefit: Reduces output costs by ~3x and utility costs by ~98% compared to GPT-5.5.

Implementation Commands

Run these in the terminal to apply the hybrid stack:

Bash# Set primary orchestrator

openclaw config set agents.defaults.model.primary "openai/gpt-4o"

# Set sub-agents to budget model

openclaw config set agents.defaults.subagents.model "openai/gpt-4o-mini"

Gateway Operations

The Gateway is the background daemon that manages Telegram webhooks, session memory, and tool execution.

When to Restart (openclaw gateway restart)

Config Changes: After editing openclaw.json or changing models via CLI.

Reboots: After a computer restart (if not set to auto-start).

Ghosting: If the bot feels "stuck" on an old model or instruction set.

Terminal Persistence

Background Mode: Use openclaw gateway start. You can safely close the terminal; Telegram will stay active.

Foreground/Debug Mode: Use openclaw tui to talk to the agent locally or watch logs.

Core Command Reference

CategoryCommandPurpose

Systemopenclaw gateway statusCheck if the engine is running.

Systemopenclaw doctorRun diagnostics on config and connectivity.

Interfaceopenclaw tuiOpen the local Terminal User Interface.

Session/reset or /new(In Telegram)

Clears cache and forces new model rules.

Session/status(In Telegram)

Shows current model and token usage.

Configopenclaw models listSee all available API models.

Troubleshooting "Stuck" Models

If the bot is still responding as GPT-5.5 after a config change:

Restart Gateway: openclaw gateway restart

Clear Session: Type /reset in the Telegram chat.

Verify: Run openclaw doctor to ensure the "Runtime" matches the "Config File."

