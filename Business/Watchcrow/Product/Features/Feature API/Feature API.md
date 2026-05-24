---

---

[[User website considerations]]

[[Requirements]]

problem: *The issue of ****double-selling watches**** reveals a significant operational problem for watch dealers: ****a lack of real-time inventory synchronisation and visibility across sales channels and team members.***



1. setting up endpoints

data to send: 

Expose data types in Bubble Data API so dealer websites can read required inventory fields.

Iframe note:

- White-label service embedding can help dealers transition from current systems without full migration on day one.

2. Brand 
3. Title (type text)
4. Model name 
5. Model number 
6. Box scope (type text)
7. Bracelet (type text)
8. Bracelet links (type text)
9. Brand (type watch brand (option set list of brands))
10. Case diameter (type number)
11. Case material (type text)
12. Crystal (option set list of crystals))
13. Dial colour (type text)
14. Movement (option set list of movements))
15. Papers scope (type text)
16. Photos (list of images)
17. Sell price (type number)
18. Serviced status (option set list of service statuses))
19. Year (type number)


### **Updated High-Level Workflow**

20. **API Connection**:
    - Your **Bubble app** (acting as the Watchcrow inventory) communicates with the dealer’s website API.
    - The dealer’s website and your Bubble app exchange inventory updates for actions like marking watches as sold, publishing them live, or removing them.
21. **Key Features**:
    - **Mark Sold on Watchcrow (Bubble app)**: Listen for updates from the dealer's website when a watch is sold and update the watch status in your Bubble app.
    - **Publish Inventory to Website**: When a dealer marks a watch as "live" in the Bubble app, send the watch data to their website to make it live.
    - **Remove Inventory from Website**: When a watch’s status in your Bubble app changes to "sold," notify the dealer’s website to remove the watch.
22. **Webhooks and Endpoints**:
    - Your **Bubble app provides API endpoints** that the dealer’s website calls to notify about events (e.g., sold watches).
    - Your **Bubble app sends API requests** to the dealer’s website to publish or remove inventory.

---

### **Step-by-Step Configuration**

### **1. Configure the API to Listen for "Sold" Events from Dealer Websites**

- **What This Does**: Your app listens for updates from the dealer's website (via API calls or webhooks) when a watch is sold and updates the Bubble database.
- **How to Implement**:
    1. **Create an API Endpoint in Bubble**:
        - Go to **Backend Workflows** in Bubble and create an API endpoint, e.g., `/api/1.1/wf/mark_sold`.
        - Set the endpoint to accept incoming POST requests with the following fields:
            - `watch_id`: The unique ID of the sold watch.
            - `status`: Status update (e.g., "sold").
    2. **Process the Incoming Request**:
        - Parse the incoming data to find the `watch_id` and update the corresponding watch’s status in your Bubble database.
        - Example: Update the watch's `status` field to "sold."
    3. **Send Confirmation (Optional)**:
        - Respond to the dealer’s website with a success message (e.g., `{"status": "success"}`).
- **Example Workflow**:
    - Trigger: Dealer’s website sends a POST request to your Bubble API endpoint when a watch is sold.
    - Action: Update the watch's status in your Bubble database.

---

### **2. Publish Inventory to Dealer Websites**

- **What This Does**: When a dealer marks a watch as "live" in the Bubble app (your Watchcrow inventory), your app sends the watch data to the dealer’s website to make it live.
- **How to Implement**:
    1. **Create a Workflow for Publishing**:
        - Add a "Make Live" button in your Bubble app that updates a watch’s status to "live."
    2. **Send Data to the Dealer’s Website**:
        - Use the Bubble API Connector to send a POST request to the dealer’s website API.
        - Include watch details in the request (e.g., `watch_id`, `title`, `price`, etc.).
    3. **Validate the Response**:
        - Check for a success response from the dealer’s website and update your Bubble database to reflect that the watch is now live.
- **Example Workflow**:
    - Trigger: User clicks "Make Live" in the Bubble app.
    - Action: Send a POST request to the dealer’s website to add the watch.

---

### **3. Remove Inventory from Dealer Websites**

- **What This Does**: When a watch’s status in your Bubble app changes to "sold," your app notifies the dealer’s website to remove the watch from its listing.
- **How to Implement**:
    1. **Watch for Status Changes**:
        - Use Bubble workflows to detect when a watch’s `status` field changes to "sold."
    2. **Send a Request to Remove the Watch**:
        - Use the API Connector to send a DELETE request (or similar) to the dealer’s website API to remove the watch listing.
    3. **Validate the Response**:
        - Confirm the dealer’s website acknowledges the removal and log the response.
- **Example Workflow**:
    - Trigger: Watch status in your Bubble app changes to "sold."
    - Action: Send a DELETE request to the dealer’s website to remove the watch.

---

### **Key Distinction: Webhooks vs. Endpoints**

23. **Webhooks**:
    - A **webhook** is when an external system (e.g., dealer’s website) sends data to your Bubble app automatically when an event happens (e.g., a watch is sold).
    - **Use Case Here**: The dealer’s website sends a webhook to your Bubble app (via an API endpoint) to notify you that a watch has been sold.
24. **Endpoints**:
    - An **endpoint** is a URL your Bubble app provides to receive or send data (e.g., the URL for your app’s webhook).
    - **Use Case Here**: Your Bubble app provides API endpoints for receiving data (e.g., sold notifications) or sending data (e.g., publishing or removing inventory on the dealer’s website).
**Relationship**: A webhook requires an endpoint to deliver its data. For example, the dealer’s website webhook will call your Bubble app’s API endpoint to notify it of sales.

---

### **Database Structure in Your Bubble App**

Here’s how your database should be structured to support the workflows:

25. **Watches**:
    - Fields:
        - `watch_id` (unique identifier)
        - `title`
        - `price`
        - `status` (e.g., "live," "sold," "removed")
        - `dealer_website_id` (if needed to identify which website the data is synced with)
26. **Webhooks Logs (Optional)**:
    - Fields:
        - `event_type` (e.g., "sold", "removed")
        - `watch_id`
        - `timestamp`
        - `response_status`

---

### **What Your Users Need**

27. **Website API Credentials**:
    - Each dealer needs to provide their website’s API credentials (e.g., API keys, URLs) to connect their website to your Bubble app.
28. **Set Up Their Website to Notify Your App**:
    - Dealers must configure their website to send **webhooks** (or API calls) to your Bubble app’s endpoint when a watch is sold.
29. **Use Your App for Inventory Management**:
    - Dealers should manage their inventory exclusively in your Bubble app (mark items as "live" or update status) to ensure syncing works smoothly.

---

### **Next Steps**

30. **Set Up API Endpoints in Bubble**:
    - For receiving updates from dealer websites.
31. **Configure API Connector**:
    - To send requests to dealer websites for publishing or removing inventory.
32. **Test End-to-End Integration**:
    - Simulate all workflows (e.g., marking items live, removing items, receiving sold notifications) to confirm everything syncs properly.
33. **Create Onboarding for Dealers**:
    - Provide a simple setup process for dealers to input their website API details and start syncing.



Setting up documentation:

[How to Write API Documentation: Best Practices and Examples](https://www.altexsoft.com/blog/api-documentation/)

- use google API doc as a reference
- Stripe Tour of API 

34. Version 1.0.0
35.  How can this APi be helpful to them? About the Watchcrow API
36. How can they acccess it? Authentication process? how do they get a key?
37. How do they start? 
38. Specific API functions, examples and errors


stick to the known layout 

- 3 column layout:
    - contents, document body, code examples 
- contents to the side 
- code snippets in different languages

Keep docs updated at all times 

Employ a technical writer

 




