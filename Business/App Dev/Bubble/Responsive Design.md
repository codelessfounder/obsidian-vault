---

---


Preventing desktop/mobile overlap: 

explain this: Ensure URLs are linked correctly:

Use dynamic links (Go to page → select mobile or desktop page) so users don’t accidentally navigate back to a desktop page while on a phone.

Great question! Let's dive into **why linking correctly is important** and how you can use **dynamic links** to avoid issues where users accidentally switch between mobile and desktop versions of your Bubble app.

---

### **Why Proper Links Matter:**

Imagine this scenario:

- A user on **mobile** is redirected to your `home_mobile` page.
- But if you have a button or link on that mobile page that points to the **desktop version** (e.g., `yourapp.com/home`), the user will accidentally land on the **desktop page**.This breaks the mobile experience because it forces them into a layout that’s not designed for their device.

To avoid this issue, it’s crucial to set up **smart/dynamic links** that automatically take the user to the **correct version of the page** (either mobile or desktop).

---

### **How to Set Up Correct Links in Bubble:**

### **Approach 1: Use “Go to Page” Navigation with Conditional Logic**

When adding buttons or workflows that **send users to another page**, make sure to account for **which device they are using**. Here’s how:

1. **Create a Button** → Go to its Workflow.
2. **Add a Workflow Action**:
    - Action type: **Navigation → Go to Page**.
3. In the **Go to Page Action**, select the **destination page**.
4. Use **conditions** to ensure the correct page version is used:
    - Example:**When Current Page Width < 800** → Go to `home_mobile`**Otherwise** → Go to `home` (desktop version).

This ensures that **the correct page opens** based on the user's screen size every time they click a button or link.

---

### **Approach 2: Use Dynamic Links to Redirect Based on Screen Size**

- Instead of **hardcoding links** to specific pages, use **dynamic logic** to redirect users. You can use a **“Link” element** or **Go to Page** action in workflows.

### Example of a Dynamic Link Workflow:

5. **Add a workflow with a conditional step**:
    - Step 1: If `Current Page Width < 800`, navigate to the mobile version.
    - Step 2: If width ≥ 800, navigate to the desktop version.

This way, **all links/buttons will behave correctly** whether the user is on a phone or computer.

---

### **Bonus Tip: Use States or URL Parameters to Maintain Context**

- If you want to **remember the user’s page state** (e.g., a search query or scroll position) across versions, use **URL parameters** like this:
    - Desktop: `yourapp.com/home?query=abc`
    - Mobile: `yourapp.com/home_mobile?query=abc`

That way, if the user switches between versions, they won’t lose context.

---

### **Summary:**

Using **dynamic links** and **conditional workflows** ensures that:

- Users always stay on the appropriate version of your app (mobile or desktop).
- They don’t accidentally switch to a desktop page while on a phone, breaking the UX.

This makes your app feel more seamless and avoids jarring layout shifts across devices. Let me know if you’d like a step-by-step on setting up these workflows!