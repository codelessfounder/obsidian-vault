---

---
[Bubble x Stripe Part 1: App setup & pricing page (SaaS Payments Course)](https://www.youtube.com/watch?v=UGg72yvwiAM&list=PLoNVJrdvQQYlHQF8v0t32UCUCQ5NKr4b4&index=2)

[Bubble x Stripe Part 2: Subscribing users (SaaS Payments Course)](https://www.youtube.com/watch?v=6oxbet-wqwc&list=PLoNVJrdvQQYlHQF8v0t32UCUCQ5NKr4b4&index=3)

1. Configuring stripe 
2. Building in bubble 
3. Utilising webhooks 
4. Understanding API docs

Functionality

- [ ] Create a subscription
- [ ] Update customer details 
- [ ] Download invoices 
- [ ] Cancel subscription 
- [ ] Delete subscription 
- [ ] Dunning 
- [ ] Update card details 
- [ ] Upgrade/downgrade a subscription 

- Creating the products option sets in bubble 
- Creating the products in stripe 
- Copy & pasting the product ID from stripe into the product option set’s attributes in bubble 
- Downloading Bubble API Connector 
- Stripe ‘secret key’ input into bubble’s API connector (development key value) 

![[Screen_Shot_2024-09-17_at_4.26.56_pm.png]]

- Creating a checkout session 
- Pasting the Stripe API checkout sessions link into the bubble API connector
- Inputting parameters
    - mode
    - customer_email
    - line_items[0][quantity]
    - line_items[0][price]
    - metadata[plan]
    - success_url
    - cancel_url
- Initialising the call 
- Build pricing UI in bubble editor 
- Add FE workflows to CTA
    - Stripe checkout-session 
    - Open an external website 
- API backend workflow 
    - Create a new subscription 
    - Make changes to User (Search for Users:first item)
- Remove “initialise” from Stripe endpoint 
- remove “version-test” from webhook when app is ready to be deployed
- Create ‘payment’ data type
- Create a new thing (payment) in backend workflow (API workflow, [checkout-session]
- Retrieve invoice
    - API call in bubbe API connector (retrieve invoice)
    - Paste Stripe invoice URL from documentation into bubble
        - Change end of URL to a dynamic expression [id]
    - input value [find this in modify values, backend workflow]
    - Initialise call
- Checkout session workflows:
- Retrieve invoice 
- Success popup
- Customer account page 
- 

![[Screen_Shot_2024-09-18_at_4.50.15_pm.png]]

- Create backend API workflow 
    - “checkout session”
- Retrieve Subscription 
    - API call 
- Build UI in billing 
- Make edits to a user’s billing account (email and password) 
- Retrieve invoices
- Cancelling a plan 
- Webhook security 
    - Use option sets and conditional expressions to match Stripe’s IP addresses with the ones in your option set 
    - Conditional expression to secure API workflows is *very important. *
- Deleting a subscription 
- Invoice paid 
- Automatic dunning 
    - Use Stripe’s tools - under settings→ billing
    - Email & Stripe Email is best for dunning. - not everyone is going to be logging in to your app everyday to check notifications 
- User updates card details ‘manage plan’
- Stripe customer portal 
- Downgrading a plan 


