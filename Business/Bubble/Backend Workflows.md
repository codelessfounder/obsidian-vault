---

---

1. Bulk update records
2. Scheduled data maintenance
3. Recurring Workflows
4. Processing lists
5. External API integrations
6. Sending notifications or emails

### **What are Backend Workflows?**

Backend workflows (also called API workflows) are workflows that run server-side and can handle operations that:

- Don’t require immediate user interaction.
- Affect multiple database records.
- Run on a schedule or are triggered via external events.

---

### **Why Use Backend Workflows?**

7. **Performance**: Avoid running large workflows on the client side, which can slow down the user's experience.
8. **Automation**: Handle recurring tasks, updates, or scheduled changes without manual intervention.
9. **Scalability**: Process large lists or complex calculations in batches.

---

### **Key Ways to Implement Backend Workflows**

### 1. **Bulk Update Records**

If you need to update multiple entries in your database (e.g., assigning `Status Priority` to all Watches):

- **Use Case**: Assign priority values to all existing watches based on their inventory status.

**Steps**:

10. **Enable Backend Workflows**:
    - Go to **Settings > API** and enable **Backend workflows**.
11. **Create a Backend Workflow**:
    - Navigate to **Backend Workflows** in the Page Selector dropdown.
    - Create a new workflow (e.g., "Update Status Priority").
    - Add a **"Make changes to a thing"** action.
    - Use dynamic logic like:
        - If `Inventory Status = Available`, set `Status Priority = 1`.
        - If `Inventory Status = Sold`, set `Status Priority = 4`.
12. **Trigger Bulk Operation**:
    - Go to **Data > App Data**.
    - Select the data type (e.g., Watches).
    - Run a bulk operation that triggers this backend workflow for all records.

---

### 2. **Scheduled Data Maintenance**

You can schedule workflows to perform routine maintenance tasks, such as:

- Deleting old data.
- Updating the status of expired listings.

**Example**: Automatically set watches to "Sold" if they remain "On Hold" for 30 days.

**Steps**:

13. Create a backend workflow to:
    - Search for Watches with `Inventory Status = On Hold` and `Created Date < Current Date - 30 days`.
    - Change their status to `Sold`.
14. Schedule this workflow to run daily via **Schedule/Recurring Events**.

---

### 3. **Recurring Workflows**

Run recurring processes on a specific interval.

**Example**: Send a reminder email to users with "On Hold" inventory.

**Steps**:

15. Create a backend workflow:
    - Search for Watches with `Inventory Status = On Hold`.
    - Send an email to their respective users.
16. Schedule this workflow to repeat (e.g., every day).

---

### 4. **Processing Lists**

Run actions on a list of things to avoid slow workflows on the client side.

**Example**: Mark multiple Watches as "Available" after a batch upload.

**Steps**:

17. Upload the watches and store them in a temporary data type.
18. Create a backend workflow to:
    - Process each item in the temporary list.
    - Set the inventory status to "Available" for each Watch.
19. Trigger the workflow when the upload is complete.

---

### 5. **External API Integrations**

Backend workflows are ideal for interacting with external APIs.

**Example**: Fetch live market pricing data for watches.

**Steps**:

20. Create a backend workflow that:
    - Calls an external API to get pricing data.
    - Updates your `Watch` database with the fetched prices.
21. Use a button or schedule to trigger the workflow.

---

### 6. **Sending Notifications or Emails**

You can use backend workflows to send notifications or emails triggered by specific events.

**Example**: Notify users when a new "Available" watch is added.

**Steps**:

22. Create a backend workflow:
    - Search for users to notify.
    - Send an email with details about the new watch.
23. Trigger the workflow whenever a new watch is created with status "Available."

---

### **How to Get Started Without Overwhelming Yourself**

24. **Start Small**: Begin with tasks that don’t require user interaction, such as updating records or scheduled maintenance.
25. **Use Bulk Operations**: Try updating your database using backend workflows for repetitive tasks.
26. **Experiment with Scheduled Workflows**: Schedule a simple workflow like sending a notification or email.
27. **Test Your Workflows**: Use Bubble’s **Debug Mode** to verify that workflows run as expected.

---

### **When Should You Use Backend Workflows?**

- When dealing with large datasets (e.g., thousands of watches).
- When processing must happen independently of the user (e.g., scheduled updates).
- When external APIs are involved.
- For actions that repeat regularly (e.g., recurring tasks).