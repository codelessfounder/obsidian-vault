---

---



![[Screen_Shot_2024-09-17_at_7.38.51_pm 1.png]]

Yes, you can turn your Bubble app into an API and allow external websites to embed a clickable element, which can redirect users to a payment screen in your app. To achieve this, here's a step-by-step guide:

### Step 1: Enable the API in Your Bubble App

1. **Go to Settings**:
    - In your Bubble editor, navigate to the **Settings** tab.
2. **Enable API**:
    - Under the **API** section, check the box to enable the Bubble API. This will allow external apps or websites to interact with your Bubble app.
3. **Define API Endpoints**:
    - In the **API Workflows** tab (under the "Backend" tab), set up API endpoints that can handle different actions, such as reserving and paying for a watch.
4. **Create Workflows**:
    - For example, you can create a workflow that generates a unique payment link for each dealer or watch listing. The endpoint will generate this link when called.

### Step 2: Design the Clickable Element

You want your users (watch dealers) to embed a clickable element on their websites, similar to "Pay with Afterpay". Here's how you can create the embedded link:

5. **Generate an Embedded Link (HTML Button)**:
    - You will need to generate a custom URL (or a button) for dealers that redirects to your Bubble app’s payment page. For example:
```html
html
Copy code
<a href="https://yourapp.bubbleapps.io/version-test/pay?watch_id=[WATCH_ID]&dealer_id=[DEALER_ID]" target="_blank">
    <button style="background-color:#4CAF50; color:white; padding:10px; border:none; cursor:pointer;">
        Pay with Watchcrow
    </button>
</a>


```
    - Replace `[WATCH_ID]` and `[DEALER_ID]` dynamically with the actual values when dealers embed it on their website.
6. **Custom Parameters**:
    - The link should contain parameters such as the `watch_id` and `dealer_id`. These parameters will be passed into your Bubble app when users click on the link, allowing your app to fetch details about the watch and proceed to the payment screen.

### Step 3: Create a Payment Screen

7. **Build a Payment Page**:
    - Design a payment page in Bubble where users land after clicking the embedded button. The page should read the URL parameters (`watch_id` and `dealer_id`), retrieve the relevant watch details, and allow customers to proceed with the payment.
8. **Connect to a Payment Gateway**:
    - Use Bubble’s Stripe plugin (or other payment plugins) to handle the actual payment transactions.

### Step 4: Provide Dealers with the Embed Code

9. **Create a Dealer Dashboard**:
    - In your app, create a dashboard for watch dealers where they can generate an HTML embed code for their watches. The code should include the correct `watch_id` and `dealer_id` parameters.
10. **Share the Embed Code**:
    - Dealers will then copy the embed code from their dashboard and place it on their website where they sell the watches.

### Example of the User Flow

11. A watch dealer embeds the clickable element on their website.
12. A customer clicks on "Pay with Watchcrow" on the dealer's site.
13. The customer is redirected to your Bubble app’s payment page, pre-filled with the watch details, and proceeds to pay securely.

By turning your Bubble app into an API and allowing dealers to embed this element, you're offering a seamless experience for them and their customers, similar to how "Pay with Afterpay" works.
