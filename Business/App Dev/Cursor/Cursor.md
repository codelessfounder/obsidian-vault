---

---
## **Prompt Structure**

1. **Context** (Explain the broader task)
2. **File/Component Name** (Specify where changes should be made)
3. **Implementation Details** (Step-by-step instructions on what needs to be done)
4. **Constraints** (What should not be changed)
5. **Expected Output** (Define the ideal result)
6. **Additional Notes** (Edge cases, UX considerations, or design consistency)

---

## **Prompt Template**

```plain text
markdown
CopyEdit
You are a front-end developer working on **[Project Name]**. Your task is to **[specific task]** inside **[File/Component Name]**.

### **Implementation Details:**- **[Step 1]**: [Describe what should be implemented first]
- **[Step 2]**: [Describe the next step]
- **[Step 3]**: [Continue describing as needed]
- Ensure that the UI remains **consistent with [referenced UI elements/components]**.
- Maintain **responsiveness for mobile and desktop**.

### **Constraints:**- **Do not** modify the overall structure or functionality of **[Component/Feature]**.
- **Only** update the content inside **[Specific Area]**.
- The UI must **match the existing styling**.

### **Expected Output:**- When **[Trigger Action]**, **[What should happen]**.
- The feature should **[Expected UI/UX behavior]**.
- If there is an error, **display [error handling behavior]**.

### **Additional Notes:**- Use **[Technology/Framework-Specific Best Practices]** if applicable.
- Follow **[Any Special Considerations]** (e.g., animations, transitions, accessibility).

Do **not** modify unrelated components or files.


```

---

## **Example Prompt**

### **Task: Add Stripe Elements in **`**AlternateCheckoutModal.js**`

```plain text
markdown
CopyEdit
You are a front-end developer working on Discopay. Your task is to integrate **Stripe Elements** into the `AlternateCheckoutModal.js` component, allowing users to enter their payment details and process a payment.

### **Implementation Details:**- Import **Stripe Elements** (`CardElement`, `useStripe`, `useElements`) inside `AlternateCheckoutModal.js`.
- Wrap the modal content inside `<Elements stripe={stripePromise}>` using the provided publishable key.
- Add a **payment form** that includes:
  - **CardElement** for entering card details.
  - A **Submit button** labeled "Pay Now" that triggers `stripe.createPaymentMethod`.
  - Display **loading state** when processing.
  - Display **error messages** when payment fails.
- Keep the **existing UI design** and ensure that the modal remains **consistent with the checkout flow**.

### **Constraints:**- **Do not modify** the structure of `AlternateCheckoutModal.js`.
- **Only update** the content inside the modal to integrate Stripe Elements.
- The modal size should **remain exactly the same**.

### **Expected Output:**- When the **"Let’s Go" button** is clicked, the modal opens, and users can enter their payment details.
- Users can **submit their payment** by clicking "Pay Now".
- After successful payment, **show a success message**.
- If there is an error (e.g., invalid card), **display the error message in red**.

### **Additional Notes:**- Use `loadStripe("pk_test_...")` to initialize Stripe.
- The modal **must be responsive for both mobile and desktop**.
- **Do not modify any unrelated components or files.**

```

---

## **Prompt Rules**

7.  Don’t start from scratch

Cursor works best when it has something to build on.
Use V0/Lovable/Bolt to generate complete functional screens and trying building 80% of the MVP there
Then bring the code into Cursor for refinement + logic.

8. Define Prompt Parameters

Stop using .cursorrules. Set up output parameters instead

Project Rules let you:

- Apply different rules per filetype (e.g., SQL vs JS)
- Control AI tone and structure
- Sync across your team via GitHub

This makes Cursor feel like an AI dev trained on your stack.

9. Sync relevant docs for better suggestions
Go to

[@Docs](https://x.com/DocS)

→ Add new doc

Sync docs for:
- Next.js
- Supabase
- Stripe

This gives Cursor deeper context, improving both code accuracy and suggestions.

10. Use [@Codebase](https://x.com/codebase) to query the entire repo

Need to trace a bug or locate a function? ask:
- “Where is the payment flow handled?”
- “Which component renders the dashboard?”

Cursor will scan and answer based on your full project context.

11. Set up MCP for schema access + automation

Model Context Protocol (MCP) gives Cursor live access to your Supabase schema.

With MCP, you can:

- Fetch tables dynamically
- Automate schema edits
- Skip writing migration files manually

The database becomes AI-readable. Game changer. It has many other use cases as well.

12. Auto-generate Row-Level Security with AI

Most developers skip RLS because it’s tedious.

Now? Just tell Cursor:
“Generate RLS policy so users can only access their own data.”

It writes secure access rules in seconds.

13. Enable YOLO Mode for speed

Cursor normally asks before executing commands.

With YOLO Mode:

- Commands run instantly
- No confirmation prompts
- Perfect for trusted flows or power users

If used wisely, it saves hours.

14. Use screenshots to improve UI

If your UI feels off, take a screenshot.
Drag it into Cursor or click the image icon under chat.

Then prompt:
“Make this UI cleaner and more modern”

This visual feedback unlocks next-level UI iterations.

15. Save your best code in .md files + Notepad

Whenever Cursor writes something useful:

- Save it as a .md file for future prompting
- Store snippets in Notepad for reuse

This helps you build a personal AI library, your own internal Copilot.


Treat Cursor like a teammate, not a magic trick.
Guide it right, and it will ship faster than any junior dev you’ve hired.

If you found this helpful, bookmark it.

Let’s build better with AI.

---

Change code: Command + K

Query code: Command + L

Scan code: Command + enter

---

## Model Parameters

16. one of the items is missing when the product reveal finishes
17. discount % needs to be calculated and displayed based on the difference between product_original_price and product_final_price


![[Screenshot_2025-05-22_at_6.45.50_pm.png]]

---

Quick best-practice checklist:

1. Use a `.env` file for Supabase key and URL, and keep it in `.gitignore`.
2. Build baseline auth flow (sign up/log in/email verification) before feature work.
3. Ask the model for code context before asking it to make edits.
4. Integrate MCP where relevant for schema/context access.