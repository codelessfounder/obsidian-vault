---

---
[[Guide Selling N8N Workflows]]

Tutorial video:[https://www.youtube.com/watch?v=4BVTkqbn_tY&list=PLlET0GsrLUL59YbxstZE71WszP3pVnZfI](https://www.youtube.com/watch?v=4BVTkqbn_tY&list=PLlET0GsrLUL59YbxstZE71WszP3pVnZfI)

[[N8N Job Post]]

- Automated feedback loop 
- Automated add to calendar 


automation #1

Text to google calendar event automation


Benefits of N8N:

![[Screenshot_2025-05-05_at_11.03.19_am.png]]


“a predictable set of predetermined actions that transfer data from one point to another”


Workflow parameters:

1. Trigger (When, frequency)
2. Filter (Condition, “*Only when…”)*
3. Action (Update a google sheet, send an email)


Steps to create a workflow:

4. Mapping 
    - Feasibility testing 
    - Tools needed
    - Estimation of workload 
    - Human intervention needed

![[Screenshot_2025-05-05_at_11.54.22_am.png]]



# Webhooks and APIs:

components of a request:

5. URL 
![[Screenshot_2025-05-05_at_12.46.45_pm.png]]
6. Method (GET, POST, DELETE, PUT, PATH)
7. Header (Gives context to the request - location, language, device type)
    - E.g. accept:application/json - tells the server it would like the response in JSON format 
8. Body (Optional)
    - Only exists for POST requests 
    - Information to send to the server
    - E.g. first_name, last_name, email

9. Credentials
    - Credentials let the application know that we are allowed to make this request
    - E.g. 
        - Query parameter: ?api_key: 0000_000_000
        - Header: Authorization: Bearer 000_000_000



Components of a response:

10. Status code 
    - 3 digit number on the success of the requests 
    - E.g. 
        - 200: OK
        - 401: Unauthorized
        - 404: Not found 
        - 500: Internal server error 
11. Header 
    - Gives more context to the request 
    - E.g.
        - content-length 
        - content-type 
        - expires
12. Body 
    - The data returned 
        - JSON 
        - HTML 
        - Data 


Webhooks:

A way for one system to automatically send real-time data to another system when a specific event occurs 

e.g. Stripe: every time a payment is made in Stripe, a webhook is sent to us to let us know a new payment has been made 


# Nodes

3 categories:

13. Entry points (triggers)
14. Function (filters)
15. Exit points (applications)

See also:

- flow
- files
- advance 


Node actions:

16. Parameters 
    - Credentials 
    - Resource
    - Operation 
    - Action settings
17. Settings 
    - Notes 
    - Visual settings 
    - Execution settings




# N8N Data Concepts

There are two main data structures:

18. JSON
    - Format used for communicating information digitally
    - Written with braces {}
    - Contain key:value pairs
    - Can be embedded when the value of another key:pair value is another JSON
        - Allows for organized storing of complex information
![[Screenshot_2025-05-05_at_3.52.10_pm.png]]

- you can access the JSON with the standard notation*:
    - Note the extra “.” to access embedded JSON

![[Screenshot_2025-05-05_at_3.54.22_pm.png]]


19. Lists
    - Collection of objects of the same or different type 
    - Written between brackets []
    - Lists can be lists on JSONs:

![[Screenshot_2025-05-05_at_3.59.15_pm.png]]


- There is a 1:1 correspondence between JSONs and tables
    - E.g. one JSON is equal to one Row in a table 
    - Each JSON is called an item 
    - Nodes use items and inputs and outputs



Item execution:

- Each node executes once per item (with some exceptions)
- e.g:
![[Screenshot_2025-05-05_at_4.17.47_pm.png]]

- Execution Schema:

![[Screenshot_2025-05-05_at_4.25.02_pm.png]]


- Expressions
    - Expressions can be a combination of:
        - Plain text 
        - item variables 
        - JavaScript
    - E.g.: Expression:

![[Screenshot_2025-05-05_at_4.31.11_pm.png]]

Priority list:

- [x] Filter Company size (11-200)
- [x] Industry column 
- [x]  Clean the job role 
- [x] Clean the company name 
- [ ] Find decision maker name and email 
- [ ] Edit existing/replace content in sheets, not create new
- [ ] remove duplicate leads 




Workflow limitations:

- Job posts with no employee count are currently being filtered out 
- the letters “co” are filtered out of company names (bad for construction)



Ben scope of work:


20. Search specific industry sectors hiring for BDMs (change linkedin link)
21. Provide email retrieval into google sheet (new Apollo workflow)
22. Set up scheduling for Monday
23. Optimise workflow
24. Evaluate lead volume
25. Plug google sheet into Reachinbox (aka instantly) automatically


| Closed scope | Optimising  |
| --- | --- |
| Search specific industry sectors hiring for BDMs   | Evaluate lead volume |
| Provide email retrieval into google sheet | Optimise workflow |
| Set up scheduling for Monday |   |
| *Plug google sheet into Reachinbox (aka instantly) automatically* |   |


## Advanced course notes

### Lesson 1: Complex data flows

---

LinkedIn SDR lead scraper workflow:

1. Scrape companies hiring for SDRs.
2. Find email addresses.
3. Enrich lead data.
4. Clean names for personalization.
5. Send leads to outbound email provider.

Reddit customer feedback workflow:

- Source: Reddit discussions + app reviews.
- Capture mention content, source, author, and timestamp.
- Summarize and suggest response handling with an LLM.
- Push records into tracking table with status lifecycle.
- Notify ops team via webhook for rapid follow-up.



