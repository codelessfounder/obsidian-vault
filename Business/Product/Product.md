---

---

[[Problem]]

[[Business/Product/Evangelism]]

[[Payments]]

[[Business/Product/Future products/Future products]]

[[Features]]

[[Business/Product/UI]]

[[Competitors]]

---

## Consolidated learnings

1. When a new user is created and they do not have a username/email/location/first name/last name, it means they did not proceed to finish account setup. The popup should keep those inputs mandatory.
2. (8 July 2025) Rob: prices were not being changed in inventory, and some data was static.

## Consolidated strategy notes

1. Target: 1000 dealers using Watchcrow to store inventory at $29/month.
2. Target: $1bn inventory managed.
3. Raise money and monetize.
4. How can we make the product so involved that users stay after the free trial ends?
5. How can we become a product that users can monetize for themselves?

## Consolidated bugs

- [ ] In edit mode, case material defaults to stainless steel instead of unknown, which can cause unintended data assumptions.

## Feedback loop cadence

| Stage | Actions | Timeframe |
| --- | --- | --- |
| Gather feedback | Aggregate in-app, support, social, and survey feedback; prioritize by impact/frequency | Ongoing |
| Plan improvements | Categorize quick wins vs medium vs long-term; align sprint goals | 1-2 days |
| Build solution | Implement + QA; share progress in demos/standups | 1-2 weeks |
| Launch updates | Ship changes and publish release notes | End of sprint |
| Share externally | Post improvements publicly with visuals/context | 1-2 days post-launch |
| Monitor response | Track outcomes and feed results into next cycle | 1 week post-launch |



**OKRs for Watchcrow**

| **Objective** | **Key Results** |
| --- | --- |
| **Eliminate inventory discrepancies between in-person and online sales to enhance dealer trust and customer satisfaction.** |   |
|   | Achieve 90% accuracy in preventing duplicate sales across platforms within 3 months of launch. |
|   | Onboard at least 10 dealers to test the integration within the first quarter of release. |
|   | Reduce customer complaints about duplicate sales by 75% within 6 months of launch. |

### **Solutions to test OKR**

| **Solution** | **Details** |
| --- | --- |
| **Real-Time Inventory API** | Build an API to enable real-time data sharing between Watchcrow and dealers' websites. |
| **Website Plugin/Integration** | Develop plugins for platforms like Shopify or provide integration guides for custom websites. |
| **Reserve-and-Hold Feature** | Add functionality to reserve items immediately upon online or in-person purchase initiation. |
| **Offline Sync for In-Person Sales** | Use mobile or desktop apps to log in-person sales directly into Watchcrow. |
| **Automated Alerts for Conflicts** | Create a notification system to inform dealers of inventory conflicts and guide resolution. |
|   |   |

---

### 

[Monday.com](http://monday.com/) has great ways to add customizable boxes and headings - how do I do that in Watchcrow?



two things to do next: 

1. Photos & videos (upload and display) 
    1. View a watch 
    2. shared_watch
    3. shared_inventory
    4. shared_inventory_mobile
2. Localise to UK, US, Europe, Asia

Product strategy: 


3. Notifications 
- [x] Team notes
- [ ] Invoices 
- [ ] Watchcrow API 
- [ ] QR Codes



Problem 

Misc updates

- [ ] Delete account
- [ ] Reusable elements
- [ ] *when X element is pressed* for better mobile experience
- [ ] conditions for when screen size is <992 but >767 (desktop UI)



Zaeger requirements:

4. Notes/Updates
    - photos
    - text
    - tag team members
![[Screen_Shot_2024-12-02_at_11.44.59_am.png]]

5. pre-owned, not used
6. Purchase date
7. warranty date
8. Serial number 
9. Price 
    1. other costs, total cost to dealer
10. Live on Website (Yes/No)
11. Inventory number
12. Check Chrono24 filters
13. Files 
14. Purchase (buyer details) -for invoice?



Watch dealers like to make notes about the watch in their inventory, so they can update their team members on the status of the watch

- notifications need to be sent out for each modification to the watch







To do: 

15. Define Feedback Loop 
- [x] Edit Photos (watch-details)
16. Download QR Code (watch-details)
17. Notifications 
18. Mobile Responsiveness 
19. Simplify ‘add to inventory’
20. teamspace (emails)

Shorten inventory add 

Email Notifications (inventory status, team notes)

Update payment popup (after 11 watches uploaded)

- [ ] onboarding tutorial & questionnaire 





Notifications: 

- in-app 
- email 



changes:

- inventory status not changing on mobile inventory 
- 



API

- wordpress
- WooCommerce
- Shopify


Questions for Mike:

- How do I sort this table?





Duolingo Gamified free trial 

- when you complete level 5, duolingo gives you a chest. inside that chest is “3 days access to super duolingo” the paid version 
- It makes it seem like you just won a prize, when in reality Duolingo have given you a reason to try the trial (preview)





to do: 





New add to inventory: 

21. Basic
- brand 
- model name 
- model number 
22. Condition (how would you describe the condition of your watch?)
23. Box and papers
    - Box scope 
    - Papers scope 
24. One photo 
25. Price 
- Buy price 
- Sell price 


Notes: 

‘share’ flow not clear - share to other 

graph not working 

Logo takes user to home page 

metrics look clickable (empty workflow?)

Change delete icon (bing)

Table to repeating group design 

close page in ‘add to inventory’ refreshes the page 




When onboarding a new user, do little things that will delight them and make them feel like they’re already using your product

- Change their avatar to their company logo 

{{ $json.Name.replace(/\n/g, '').trim() }}



![[Screen_Shot_2025-01-06_at_3.31.02_pm.png]]



bugs:

- [ ] analytics and graph (fine for now, leave it, doesnt matter)




Corize notes:

*I am an experience bubble dev looking to teach on corise *


- Landing page should be one sided - benefits for one of the users 
- 




![[Screen_Shot_2025-01-06_at_6.53.24_pm.png]]


- this is more of an ad - you could market this on social media to bring in teachers to sell their course 
- I stay on the landing page when I log in 
    - I want to be taken directly to a form that lets me create a classroom


![[Screen_Shot_2025-01-06_at_7.27.58_pm.png]]

- Need ‘create a class’ button here  - as a new user looking at my current classes, I have none so I want to create one 
![[Screen_Shot_2025-01-06_at_7.30.23_pm.png]]

- after I’ve filled in the ‘create a classroom popup’, i am taken here. It’s not overtly clear that this is a form to create my classroom.
    - at the very least you need a heading saying ‘create a classroom’
- save an continue button isnt visible without scrolling 
- Classroo
![[Screen_Shot_2025-01-06_at_7.41.13_pm.png]]

i dont think this is necessary - the course will be live straight away right?

- change basics to ‘class details’
- I don’t think class times should be an option during the ‘create a classroom process’ - teachers should have the option to do that when they 
    - adding a class confused me and disrupted my path in creating a classroom - cut it out 



New Features:

- Updated display for watch details
- Detailed watch details 
- basic cost analysis
- team notes and Teamspace 
- Detailed inventory updates
- Downloadable QR code

questions:

How do you currently upload and remove your watches from your website?

The actions we’re planning on building for the API are: mark as sold in Watchcrow when watch is sold on website, remove from website when watch is marked as sold in Watchcrow, make live to website 

Currently working on API. If we can get Zaeger using Watchcrow for your inventory it’ll prepare you for when we launch the API. we’ll have 48hr ticket turnarounds, so any problems will be fixed in two days.  


Offer group on individual watches to show offers for each watch 

to do for inventory sales: 



example listing on facebook:



![[Screen_Shot_2025-02-05_at_1.18.50_pm.png]]




How can shared (watches) feature enable watch sellers to sell more watches?

Hey - I’ve built some software to help watch dealers sell more watches, and I figure you’re a watch dealer so maybe you can help? Would be happy to give you the software for free…

USP: inventory management and marketplace



New Watchcrow Strategy: 

- build API: easy for dealers to toggle their watches from their website - no manual upload needed 
- Consider offers feature - build out offers into specific watches 
- Build marketplace for dealer watches to be shown 