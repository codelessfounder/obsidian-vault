---

---

- **The Scalable Architect:** "I build reusable frameworks, like my RAG 'Second Brain' app, that can be standardised and deployed across multiple business units."
- **The GTM Builder:** "I’ve built end-to-end GTM pipelines using n8n, Apify, and Apollo to automate the entire funnel from lead scraping to email outreach."
- **The Constraint Solver:** "I’m highly cost-conscious with automation; I use techniques like pinning test data to debug complex API workflows without wasting expensive credits."
- **The Impact Specialist:** "I focus on measurable ROI, such as shipping an Inventory API that reduced discrepancies by 25% and facilitated over 1,500 transactions."
- **The Full-Stack Owner:** "I have a 'maker' mindset and own the entire lifecycle, from designing React frontends to writing server-side logic for high-stakes PWA applications."
- **The Cross-Functional Partner:** "I thrive on working across departments to translate messy business problems into structured technical plans and clear OKRs."

AI & Automation Experience
Can you describe an AI or automation workflow you’ve built end-to-end, including the tools used (e.g., n8n, LLMs, Relevance AI) and the problem it solved?
I built an end-to-end automated lead generation pipeline using n8n to replace manual prospecting. The workflow begins by using Apify to scrape high-intent job posts from LinkedIn. I then integrated the Apollo API to programmatically extract specific decision-maker contact information based on the scraped company data. The final stage involves an API POST request to Instantly to automatically enrol these leads into tailored email sequences. This creates a closed-loop system that moves from raw web data to active outreach without manual intervention.

Business Impact
What measurable results did your AI/automation projects deliver (e.g., time saved, cost reduced, increased efficiency, revenue impact)?
The implementation of a custom Inventory API directly addressed critical operational inefficiencies. By discovering that manual sales tracking was a primary user pain point, I designed a technical solution that synchronised real-time marketplace data with internal stock records. This deployment resulted in a measurable 25% reduction in inventory discrepancies and mismanaged sales. This improvement stabilised the marketplace's reliability, contributing to the successful facilitation of over 1,500 transactions.

End-to-End Ownership
Have you taken a project from ideation through to deployment? If so, please describe your role and how you managed the process.
For the Disco iGaming PWA, I owned the entire project lifecycle from initial architecture to production deployment. My role involved building the frontend with React and TypeScript, utilising Vite for optimised builds and lazy loading to ensure high performance. I managed the backend by implementing Supabase for secure JWT-based authentication and session handling. Additionally, I developed the core server-side Edge Function logic, which handles provably fair outcome generation and cost scaling based on configurable win probabilities.

Collaboration & Adoption
How have you worked with teams to implement your AI/automation solutions, and how did you ensure adoption and effectiveness?
To ensure technical solutions were adopted effectively, I focused on aligning development with business OKRs and specific user feedback. During my tenure as Product Lead, I identified that inventory mismanagement was the highest friction point for early users. I worked cross-functionally to translate this qualitative feedback into a technical roadmap, leading to the deployment of the Inventory API. By demonstrating how the tool directly solved a revenue-draining problem, I secured immediate adoption and improved overall marketplace efficiency.

Experimentation & Problem-Solving
Can you give an example of a workflow or AI solution that didn’t work initially? What did you learn, and how did you iterate to improve it?
During the development of the n8n lead generation workflow, I encountered a significant cost constraint involving the Apollo API, where frequent calls for debugging were depleting the client's expensive credit balance. To solve this, I iterated on the workflow by pinning test data to the nodes. This technique allowed me to simulate successful API responses and validate the downstream logic—such as data formatting and email enrolment branches—without triggering actual API charges. This approach enabled exhaustive testing and refined the logic to be production-ready while keeping the development process cost-effective.