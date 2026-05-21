---

---

you're essentially delivering an automated system that either:

- Runs on **their n8n instance** (self-hosted or cloud)
- Or you **host it for them** and deliver the results

Here’s exactly how it works — broken into 3 clear models:

---

## ✅ **Model 1: Build & Transfer (One-Time Setup)**

### 💼 What you do:

- Build the full workflow in your own n8n
- Export it as a `.json` file
- Deliver documentation + setup steps
- Support setup on *their* n8n Cloud or self-hosted instance

### 🛠 What they need:

- Their own n8n account (Cloud or hosted)
- API keys (Apify, Clearbit, etc.)
- A Google Sheet or Airtable for export

### ✅ Ideal if:

- They want full ownership
- You're selling a **one-off product** or **custom build**

---

## ✅ **Model 2: Managed Workflow (You Host It)**

### 💼 What you do:

- Host the workflow in *your* n8n (e.g. on a VPS or n8n Cloud)
- Manage API keys, executions, and automations
- Share output (e.g. CSVs, Sheets, Airtable) with them weekly
- Charge them monthly or per lead

### 🛠 What they need:

- Access to the output (e.g. Google Sheet, Airtable, Notion)
- Optional: read-only dashboard

### ✅ Ideal if:

- You want to charge **monthly** or per-lead
- They don’t want to manage infrastructure

---

## ✅ **Model 3: White-Label Service**

### 💼 What you do:

- Create a version of the workflow you can clone per client
- Deliver data as a **service** (leads, enrichment, etc.)
- Optionally white-label output (e.g. their email sender)

### ✅ Ideal if:

- You plan to scale this across multiple clients
- You offer it as a **productized service**

---

## 📦 How to Package the Workflow

- Export workflow from n8n via the top-right “Export” button
- Give them a:
    - `.json` file
    - List of needed credentials + where to add them
    - Example Google Sheet template
    - Optional: screen recording or step-by-step doc

---

## 💸 Licensing / Terms

If you're selling the workflow:

- Include **licensing terms** in a doc or contract (e.g. one-time use, not for resale)
- If hosting it, define **how often** you'll run it, SLA for delivery, and API usage limits

---

### ⚡ Bonus Tip:

Add a **“Client Config” node** (e.g. Set node with their role targets, industry, and region) so you can reuse the core structure with new parameters.

---

Would you like me to give you:

1. A reusable template export for lead scraping?
2. A Notion-style handoff doc you can give to clients with instructions?