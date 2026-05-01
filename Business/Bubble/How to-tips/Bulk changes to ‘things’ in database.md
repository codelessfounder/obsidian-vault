---

---

Okay so let's say that I change a thing's data in the data type (backend) - what happens to the things that current users have already created? The will be legacy products that don't benefit from the changes the app creator has made. For example, I added a status of 'completed' or 'sold' to my Watch in the database, but all the Watches I had previously created now do not have a status feature. How do I get around this?

### ChatGPT said:

When you make a change to a data type in Bubble.io (like adding a new field such as "status" to your "Watch" data type), existing entries (or "things") won't automatically have this new field populated. However, these legacy entries will still function, but without the new field filled in.

To get around this, you have a few options for handling legacy data:

### 1. **Assign a Default Value to the New Field**

You can assign a default value for all the existing entries. Here’s how:

- **Backend Workflow or Bulk Operation**: Create a workflow that updates all existing entries with the new field. For example, you could assign a default status like "Pending" or "Incomplete" to all existing Watches.

**Steps**:

- Go to **Data > App Data**.
- Click on the **Watch** data type.
- Use the **Bulk Operation** or create an API Workflow to modify all existing entries by setting a default value for the "status" field.
    - This ensures all legacy Watches will have the "status" field populated without users having to manually update them.

### 2. **Use Conditions to Handle Missing Fields**

When displaying or using this data in your app, you can check if the "status" field is empty and provide fallback behavior.

- For instance, when displaying the status of a Watch, you can conditionally show "Unknown" or "No status set" if the field is empty.

**Steps**:

- In your app's elements or workflows, add conditional logic:
    - **When Watch's Status is empty → Show 'No Status'**.

### 3. **Manually Update Data in the Editor**

You could also manually update the entries in the **Data** tab if there are only a few legacy items. This is only recommended for small datasets.

### 4. **Create a Migration Workflow**

Set up a **Backend Workflow** that runs through all existing Watch entries and sets a default status for each, allowing you to control and automate the process.

**Steps**:

- Go to **Backend Workflows**.
- Create a new API endpoint to update the "status" field.
- Use a "Schedule API Workflow on a List" action to run this on all existing Watches, applying a default or calculated value for the new field.

This approach ensures that both existing and new Watches in your app will benefit from the added "status" field without data inconsistencies.