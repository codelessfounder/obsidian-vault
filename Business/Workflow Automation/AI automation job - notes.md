---

---

quick notes:

Strategy

1. Send out an emial at the end of each week - a “weekly automation digest” highlighting one new thing you built and how much time it saved 
2. At the end of Month 3, present a slide deck to the partners showing
- **Hours Reclaimed:** "We saved the Associate team 40 hours a month on data entry."
- **Speed to Lead:** "Our response time to hot deals decreased from 3 days to 4 hours."
- **Data Integrity:** "100% of our CRM entries are now enriched with real-time market data."

3. friction audit: ask every employee “what is the one task you do every week that you absolutely dread?”
4. data bottleneck: Identify where data is being manually copied from Typeform/Pitchbook into the CRM (Affinity/Salesforce etc). 


“quick win” roadmap:

5. 

## Success Metrics

### **1. Internal Efficiency: "The Capacity Multiplier"**

*Focus: Proving you’ve freed up high-value M&A and HQ staff to do more deals.*

- **FTE Reclaim (Hours Saved):** Tracking the total hours saved on manual data entry, CRM logging, and report generation (Target: **20+ hours/week** across the HQ team).
- **Pipeline Velocity:** Measuring the reduction in time from "Initial Pitch Deck Received" to "First Draft Investment Memo" (Target: **>70% speed increase**).
- **Data Integrity Score:** The percentage of CRM records in **Attio** that are automatically enriched with **Clay/Apollo** data vs. manual entry.

### **2. Portfolio Growth: "The Valuation Driver"**

*Focus: Making the 13 portfolio companies more profitable and scalable.*

- **CAC Reduction (Cost of Acquisition):** Lowering the cost of generating a qualified lead by automating outbound workflows across **Instantly** and **HeyReach**.
- **Churn Mitigation (LTV):** The number of "At-Risk" customers identified by the **AI Sentinel** before they actually cancel (Target: **5% increase in retention**).
- **Tool Adoption Rate:** The percentage of the 13 Portfolio CEOs and Growth Leads actively using your centralized automation templates.

### **3. M&A Intelligence: "Proprietary Edge"**

*Focus: Using AI to find better deals faster than other venture firms.*

- **Signal Accuracy:** The conversion rate of "AI-Identified Leads" to "Active M&A Conversations" (Targeting higher quality, not just higher volume).
- **Knowledge Retrieval Speed:** Reducing the time it takes for an Executive to find historical data (term sheets, past deal notes) from minutes to seconds via your **Supabase RAG** system.
- **Automation ROI Dashboard:** The creation of a live, transparent dashboard for the ExCo that quantifies exactly how much money/time your workflows are saving the firm.


Tools:

- Orchestration: N8N
- Orchestration: [Make.com](http://make.com/) 
- Orchestration: Zapier 
- Data enrichment: Clay
- Database/CRM: Affinity 
- Database/CRM: Airtable 
- Slack
- Intelligence: Claud/Gemini/OpenAI 



I will be automating for the HQ and for the companies 



AI Automation Workflows:


6. Company Knowledge base 
7. Internal VC Automation: “Investment Committee Copilot
8. LTV Churn Sentinel 


I’m very interested in this role because it allows me to do build purposeful workflow automations within the context of a firm where success metrics matter. I’ll be applying my antural curiosity about pushing the boundaries of AI agents to a role where I’ll be able to see direct impact within the internal team and potentially the startups. I’ll effectively be treating it like a startup.

Plan:

## 3-Month "High Impact" Roadmap

### Month 1: Internal Efficiency (The IC Copilot)

**The Build:** A Slack-based Agent powered by an **n8n + Supabase MCP** setup.

- **Reasoning:** VCs hate data entry. When they drop a deck into Slack, your n8n workflow triggers a Supabase Edge Function that scrapes the deck, hits the Clay API for competitor funding, and checks your internal Supabase "Knowledge Base" for similar past deals.
- **The "Flex":** Show them how you use **Vector Embeddings** to find "Semantic Matches"—e.g., *“We looked at a company similar to this in 2023; here is why we passed.”*

### Month 2: Portfolio Scale (The LTV/Churn Sentinel)

**The Build:** A "Retention-as-a-Service" template for the 13 portfolio companies.

- **Reasoning:** This is where you prove you can scale. You build a standardized Supabase schema that any of the 13 startups can "plug into."
- **The Flow:** n8n monitors their Stripe/HubSpot webhooks → stores events in Supabase → runs an AI "Risk Scoring" script → alerts their CS team via Slack if a big account is drifting.
- **The "Flex":** You aren't building 13 separate tools; you are building one **multi-tenant architecture** they can all use.

### Month 3: The "Company Brain" (Knowledge Base)

**The Build:** A RAG (Retrieval-Augmented Generation) system for the entire firm.

- **Reasoning:** VCs have "lost knowledge" in Notion, Slack, and Email.
- **The Flow:** Use n8n to crawl their Notion/Google Drive, chunk the text, and store it in **Supabase pgvector**.
- **The "Flex":** Create an **MCP Server** for this. Now, when a Partner is in ChatGPT or Claude, they can use your custom tool to ask: *"What is our standard term sheet for Series A in the EU?"* and get an answer based *only* on their private data.

---

## Why your "Supabase + MCP" approach wins

In your interview, lean into these three points to address the "Experimental Hire" anxiety:

9. **Security:** *"By using Supabase and n8n, we keep the firm's sensitive deal data in our own VPC, not scattered across 50 different third-party AI apps."*
10. **Scalability:** *"I’m building an 'Automation Engine' that our 13 portfolio companies can subscribe to, essentially acting as an internal CTO-as-a-Service."*
11. **Speed:** *"Because I use MCP, I can give our AI models direct, secure access to our GTM tools (Salesforce/HubSpot) without writing brittle, custom integrations every time."*

---

### Your Next Step

Since you’re comfortable with Supabase, would you like me to draft a **technical "One-Pager"** you can hand over during the interview? It would outline exactly how the **IC Copilot** moves from a Slack upload to a Vector search in Supabase.



Questions: 

12. “Work from our office regularly”
13. “you’ll work across Finance, Sales, Marketing, and 13 portfolio companies.” - what the split between systems administrator and automation/innovation? I want to confirm it will be automation engineering and not IT Support. 
14. What is the single source of truth for data in HQ and for the companies? I want to be aware of how long I will be cleaning data. 
15. Some of these tools I haven;t used before, like CLay, even though I’m familiar - while I’m very interested in being involved in the GTM strategy, I just want to confirm that I’ll be employing these tools to create automations, rather than expected to be an expert in the native feature in these products. 
16. What are some of the short term and long term goals of this role? What does Undeinable success look like? Is it a specific ROI from the portfolio, or is it the creation of a proprietary internal AI platform?
17. Who will be defining my priority backlog, for example if lots of stakeholders all want something at once. 
18. Does the firm have a centralised Data Lake, or will I be responsible for consolidating these data pipelines. 


Notion

EA Games 

Immutable - reach out to recruiters 
















