---

---
**Universal LLM Prompt Template**

### **[1] System Instruction (Set Context Clearly)**

*"You are a [role/persona] with expertise in [subject]. Your task is to [objective of response]. Follow the instructions carefully and ensure accuracy."*

### **[2] Task Definition (Be Clear and Specific)**

- **Goal:** *Explain exactly what you need the response to achieve.*
- **Format:** *Specify the output format (e.g., list, table, markdown, JSON, code snippet, bullet points, structured text).*
- **Length:** *Define response length if necessary (e.g., "Keep responses concise, no more than 3 sentences" or "Provide a detailed breakdown in 5 paragraphs").*
- **Tone/Style:** *Specify if the response should be formal, casual, persuasive, humorous, etc.*

### **[3] Input Examples (Few-Shot Learning for Consistency)**

- *Provide examples that demonstrate the expected response style or format.*
- *If applicable, show correct vs. incorrect examples to reinforce accuracy.*

### **[4] Step-by-Step Breakdown (For Complex Requests)**

1. Step 1: *Define the first part of the task.*
2. Step 2: *Specify the second step, ensuring logical order.*
3. Step 3: *Continue with additional required steps as needed.*
4. *Ensure the final output is synthesized properly and meets the end goal.*

### **[5] Constraints & Considerations (Prevent Errors & Irrelevance)**

- *Do not include [specific exclusions].*
- *Ensure all information is accurate and sourced if required.*
- *Avoid assumptions; clarify if information is missing.*

### **[6] External Tools & Verification (Enhancing Accuracy)**

- *If calculations or logic are required, verify answers before finalizing output.*
- *Use code execution where necessary for precise computations.*
- *Check for missing context or additional relevant information.*