---

---

Deeptune is a New York-based AI infrastructure firm that builds high-fidelity "Training Gyms" designed to transition AI from conversational models into capable, autonomous agents. By providing interactive simulation environments that replicate complex software stacks like Salesforce, Slack, and Jira, Deeptune allows AI models to "learn by doing" through reinforcement learning, similar to a flight simulator for pilots. Following a $43 million Series A led by Andreessen Horowitz in March 2026, the company has rapidly scaled to over $10 million in ARR, positioning itself as a critical provider of the synthetic interaction data necessary for the development of reliable, task-oriented Artificial General Intelligence (AGI).

Questions to ask:


1. "How do we handle 'edge cases' where the simulated environment (like a mock Salesforce instance) behaves unexpectedly for the agent?”
2. "How do we validate that improvements in our 'gyms' actually translate to higher scores on external benchmarks like OSWorld or Terminal-Bench?
3. "How involved are the frontier labs (OpenAI, Anthropic, etc.) in defining the specific tasks we build into our training gyms?”
4. "What internal tools do we use to monitor agent progress in real-time?
5. what is the typical 'feedback loop' time between an AI Trainer identifying a model failure and a new training run being initiated?
6. How do we document the 'reasoning' behind the gold-standard paths we create for the agents?
7. What does a 'successful' first 30 days look like for an AI Training Specialist here—is it a specific number of gyms optimized or a certain benchmark hit?

## **The "Rubric First" Mindset**

The evaluation we completed proved that the "Gold Standard" is about **strict adherence to constraints**.

- **Note-taking Focus:** During the "Prompts Presentation" and "QA Presentation," don't just write down the general ideas. Write down the **exact constraints** (e.g., tone requirements, specific sign-offs, or language conventions like American English).
- **The "Mean Grader" Persona:** You excelled when you were critical of the model. Carry that technical skepticism into the "QA Exercise" rounds. Look for the logic loops and "unauthorized" data generation we identified earlier.

## **Critical Evaluation Checklist**

Based on the mistakes we caught during your practice tasks, keep this **"Anti-Error" checklist** on a sticky note or digital pad during your exercises:

- **American English:** Use "z" not "s" (Categorize, Recognize, Priority).
- **Instruction Following:** Did I include the mandatory sign-off? Did I use the mandatory opening phrase?
- **Data Integrity:** Does the table data match the text? (Remember the Q3 vs. Q4 error we found).
- **Formatting Consistency:** Are the bullet points uniform? Is the tone professional throughout?


# Cheat Sheet 

### **1. The "Ghost Data" Failure (Task 4)**

In the customer service response task, you caught a major hallucination.

- **The Error:** The model asked the customer to "send more photos from different angles" to process a replacement.
- **The Conflict:** The original prompt stated the customer had **already** attached photos.
- **The Onboarding Lesson:** Always cross-reference the *Input* (Transcript/Email) with the *Output*. If the AI asks for something it already has, it’s a "Major Fail" in utility and creates customer friction.

### **2. The "Infinite Loop" Logic (Task 3b)**

You analyzed a CRM automation workflow diagram.

- **The Error:** A red arrow from the "Marcus" lead node pointed directly back to the "Product Interest" start node.
- **The Result:** A lead would circulate forever and never reach the "Send Notification" or "Create Task" nodes.
- **The Onboarding Lesson:** When auditing workflows (Task 5 & 6 in your schedule), trace the path of a single data point from start to finish. If there is no "End" or "Exit" node for a specific path, the logic is broken.

### **3. Metadata Omission & "Unprompted" Creation (Task 2b)**

In the Kanban board task, the agent failed to migrate data correctly.

- **The Error:** It removed "Priority" labels (High/Medium/Low) and invented a new task ("Create Privacy Policy") that wasn't in the source list.
- **The Onboarding Lesson:** * **Lossy Migration:** If the source has 5 data points (Title, Date, Priority, Owner, Status), the output must have all 5.
    - **Hallucination:** Adding "helpful" extra tasks is actually a failure. An AI should never invent work that wasn't requested.

### **4. The "Date & Table" Discrepancy (Task 1b)**

You caught a subtle but professional-killing error in a Performance Summary.

- **The Error:** The report was for **Q3**, but the metrics table header said **Q4**.
- **The Onboarding Lesson:** AI models struggle with tabular data alignment. Check that the column headers in a table match the narrative text of the document.

### **5. Your "Gold Standard" Writing Rules**

To maintain your **5/5 score** during the exercises tonight, apply these formatting rules you perfected:

- **American English:** Use *Categorize, Unauthorized, Labeled, Favorable*. (Avoid *Categorise, Unauthorised, Labelled, Favourable*).
- **Professional Sign-off:** If they ask you to act as an agent, use the requested name (e.g., **Morgan Ellis**).
- **No Rambling:** Do not say "This is a problem because..." for every single bullet. Group your findings:
> "The following logic errors collectively undermine the workflow's reliability: [List 1, 2, 3]. Consequently, this results in [Business Impact]."





# Practice Questions

| **Task** | **Scenario** | **Key Failures / Red Flags** | **"Gold Standard" Win** |
| --- | --- | --- | --- |
| **1. Performance Summary** | Q3 Platform Engineering Email | **Instruction:** Wrong sign-off (Patel vs. Ellis).<br>**Data:** Table said Q4, text said Q3.<br>**Spelling:** "completely" and "writen." | **Accuracy:** Data in tables must match the narrative text exactly. |
| **2. Kanban Migration** | Text list to Notion Board | **Mapping:** Moved "Repo" to Done (incorrect status).<br>**Metadata:** Deleted or changed priority labels.<br>**Hallucination:** Created an "unauthorized" task. | **Integrity:** No data should be lost or invented during migration. |
| **3. CRM Automation** | Lead Routing & SLA Workflow | **Logic:** Infinite loop on Marcus's leads.<br>**SLA:** Ignored price tiers ($10k/$50k).<br>**Edge Cases:** No path for "Unclassified" leads. | **Robustness:** Trace every path to an "End" node; account for "Other" data. |
| **4. Meeting Summary** | Skincare Marketing Transcript | **Response B:** Missed a deadline and used vague timing ("next week"). | **Granularity:** Response A won by providing specific dates (e.g., Feb 21). |
| **5. Customer Support** | Damaged Vase Refund/Replace | **Friction:** Response B asked for photos already provided.<br>**Instruction:** Response B ignored "No Return" rule. | **Utility:** Followed sign-off rules and minimized customer effort. |

# Sample Questions

- **Prompt Reconstruction:** *"Based on the output provided, write the original prompt that would have been used to create this [Workflow/Board/Response]."*
- **Logical Auditing:** *"Identify 3 main issues with this automation workflow that prevent it from being a functioning system."*
- **Clarification Strategy:** *"What clarifying questions should the agent have asked the user before setting up this workflow to handle edge cases?"*
- **Comparative Evaluation (A vs. B):** *"Select which response is better, rate the strength of your preference (1-4), and explain your reasoning in 3-5 sentences."*
- **Fact-Checking / Verification:** *"Analyze the output and verify if the data matches the provided source material (Transcripts/Lists/Emails)."*
- **Instruction Adherence Check:** *"Does the output follow all 'Negative Constraints' and mandatory formatting rules (e.g., Sign-offs, Spelling, Tone)?"*
- **Impact Analysis:** *"Explain why these logical failures are a problem for both the 'Model Creator' and the 'End User'."*



# Sample answers:



| **Task Scenario** | **Your Verbatim Submission** |
| --- | --- |
| **Task 2a: Kanban Migration Prompt** | "I am a project manager looking to move a list of tasks into a Notion Kanban board. I have a list of tasks that I need you to move into the following columns: 'To do', 'In progress', 'In review', and 'Done'.<br>My business requirements are:<br>1. Column mapping: Map each task to the correct column based on the status provided in the list.<br>2. Priority labels: Maintain the priority labels (High, Medium, Low) for each task.<br>3. Task details: Include the task title, owner, and due date for each task.<br>4. Data integrity: Ensure that all tasks from the list are moved to the board and that no new tasks are created." |
| **Task 3a: CRM Automation Prompt** | "I am a sales leader looking to build an automation that qualifies, assigns and reports deals in our CRM. Design a workflow that is triggered whenever a new deal is created.<br>My business requirements are:<br>1. Lead ownership: Route new deal opportunities based on 'product interest: Priya (technical sales) should receive "API/integration leads", Marcus (Analytics) should receive "analytics and reporting leads" & "security/compliance leads". Any other leads should be assigned to a "round robin distribution".<br>2. SLA tiering: establish priority tiers based on the size of deals. For example: >$50k is a 2hr SLA, $10-50k is a 8hr SLA and <$10k is a 24hr SLA.<br>3. Operations: trigger an automatic notification to the assigned rep and then automatically generate a task for following up.<br>4. Management reporting: write a weekly report to be delivered to the Sales Manager and VP of Sales every Monday morning at 9am." |
| **Task 3b: Workflow Logic Audit** | "I noticed 3 main issues with this automation workflow that doesn't entirely meet the viable logic required of a functioning workflow:<br>1. Infinite loop: It seems that all leads received to Marcus have a red arrow that direct leads back to the product interest node, creating an infinite cycle for certain deals.<br>2. Missing SLA targeting logic: All deals move to a singular SLA priority node, which makes it unclear as to how different deals will be assigned different SLAs.<br>3. Lack of error handling for deal classification: If a deal is not classified, it simply reverts into the "other" category instead of being properly processed, resulting in potentially unqualified leads being processed.<br>This is a problem for the model lab/agent creator because it fails to consider unsuccessful data points and/or data edge cases, which creates a higher chance of creating incomplete workflows that need continuous debugging.<br>This is a problem for the sales lead because improperly categorised leads could result is missed deal opportunities which could directly impact company revenue." |
| **Task 3c: Clarifying Questions** | "The model/agent should have asked clarifying questions before setting up the workflow to handle product interest categorisation edge cases and SLA assignment granularity. For example:<br>1. "how should the automation handle deals that fail to match a specific product interest to make sure all leads are properly assigned to a rep?"<br>2. Should the "set priority & SLA" step be an unconditional node for all deals, or should it only trigger differently depending on who is assigned the deal?"<br>These questions should provide context on ambiguous rules set by the sales leader and allows the workflow to handle real world data inputs." |
| **Task 4: Meeting Summary Choice** | "Despite its length, response A is a more favourable output to response B. it clearly outputs "clear action items, owners and deadlines" without fault, whereas response B has a deadline omission in action item #2. Response A's next meeting output is more granular, creating a clear date that solidifies that the next meeting is on 21 February 2026, versus response B's vague "next week" scheduling". Both outputs have a reasonably strong summary, but Response A's structuring and information granularity in its approach to the user's instructions make it a stronger preference." |
| **Task 5: Customer Support Choice** | "Response A is much more favorable. It adheres to the user's main instruction to communicate the policy that the customer "doesn't need to return the damaged item" and the required employee sign off of "Kind regards, Morgan Ellis, Customer Support. Response B outputs an ambiguous "we can sort something out for you", as well as creating unnecessary customer friction by wrongly requesting more photos from the customer in order to process the issue. Response A follows the necessary formatting constraints that make it a significantly stronger output than Response B." |


# Notes

agents receive rewards when they perform a task properly:

- what is the reward? 

ask questions when they come up, not at the end of the day 

what happens in the gym (tracking): 

- screenshots record all the actions and changes made in the app
- The agent will then try 10 times and then we will decide when they’re done 


agent training :

8. Prompts - task for the agent to complete the app 
9. Recording - Solving the prompt (twice) in the app 
10. Evals - Agent attempts the task (10x) 
11. QA - checking the grading twice 

agents do no have memory - each attempt is a blank state 

Evals need to complete max 5/10 times 

- agents learn from the mistakes, not the successes 
- 

QA is intervention by us to check the evals 


Prompts needs to be practice the agents on how users will actually interact with agents. They also need to be contextual to the type of app that is being tested. 

*Diverse prompts help the agent practice everything it might see in the real world *

Recoderings:

- need to be correct 
- easiest of the 3 instances 

QA:

- give them a reward and make sure they are doing well 
- We cannot punish the agent for mistakes that they are not responsible for 


Quality over Quantity 

- 125 tasks an hour that are 75 correct 
- 65 task an hour and all 65 are correct 

Submitting tasks you should be proud of that the agent should be tested on 

### **ONBOARDING:**

### What are the goals?

- **01** Fully enabled with all required tools
- **02** Comfort navigating the platform and apps
- **03** Understand full task flow (prompts + QA)
- **04** Strong foundations for entire task flow
- **05** Feel comfortable engaging with team

- **01** Summarized and easy to engage with materials
- **02** Establish fun, creative working environment
- **03** Empower capable people to thrive
- **04** Remove Impediments
- **05** Facilitate productive engagement

Call each other if you have problems

how do recordings impact QA?

Diverse prompts are really important 


tasks:

12. extraction
13. transformation
14. retrieval 

prompt writing style should be the same, but the purpose of data that should be retrieved should be changed. that is what we mean by diversity. 

task attempts: 

- prompt writers do a prompt once 
- Recorders do two recodrings, and if they are not correct you can go back 
- QA evaluations are final 


make sure you are in the right app in the morning 

- you will work on 1-2 apps 

this week - dragon saleor 

any data in your local app will not impact other people’s data

HOWEVER - if everyone uses the same app at once, it will take a while. 
NB if you want to travel and want to work - you MUST let us know. This is because server latency when opening the app will change. 

At the end of the day - you must click stop app so you stop your session. 

avoid in apps:

- do NOT log out of the app. if you do, you need to kill the app and restart it. 


apps 

Notebook LLM: Each App has one 

- Not allowed to use this for prompts
- Does not contain specific app data. 



day 2 onboarding:

prompt writing:

what is a good prompt

before writing a prompt:

- app should be open before prompt writing 
    - we need to make sure that the request is possible for the app 
- 

**Before writing any prompt:**

- **Open the app** and actually perform the task
- **You learn the app faster** - hands-on exploration

**Why this matters?**

- **You write better prompts** - you understand what's realistic vs. contrived
- **You catch issues early** - data doesn't exist, task is impossible, multiple solutions
- **Verify every detail** you're referencing

**The process:**

- Explore the feature you want to test
- Complete the action step-by-step
- **Then write your prompt**
- Note any edge cases and tricky parts

## There Are Fundamentally 2 Types Of Prompt

---

### 1. Transformation Prompts (**Changes the app**)

- Creates, edits, updates, adds, deletes, moves data
- Change must persist after page refresh
- **Examples:** "Create user John Smith", "Edit customer age to 34", "Delete phone number"

---

### 2. Extraction Prompts (**Retrieves without changing**)

- Finds and returns information
- Contains e.g.: Who, What, Where, When, How many, List, Find, Retrieve
- Must specify data type: **str**, **num**, **list[<type>]**
- **Example:** "What is the email address for user 'John Smith'? Return as str"

## **Core Prompt Requirements**

---

### **✅ Every Prompt Must Have:**

- **1 GTFA (Ground Truth Final Answer)** - exactly ONE correct answer
- **Clear & unambiguous** - no multiple interpretations
- **Feasible** - actually possible to complete in the app
- **In scope** - no imports, exports, or external integrations

---

### **❌ Avoid Writing Prompts With:**

- **Relative dates** ("next week", "tomorrow") → Use fixed future dates
- **Multiple valid solutions**
- **Impossible asks**
- **Ambiguous instructions**

## Quality Prompts Are Thoughtful, Avoid Repetition And Are Realistic

---

### Be **THOUGHTFUL**:

- ✅ Unique & creative
- ✅ Comprehensive coverage of app features
- ✅ Realistic – what real users would ask
- ✅ Tests important skills

---

### Avoid **REPETITION**:

- **Example of repetition:** ❌ "Change name for John Smith", "Change name for Bob Jones", "Change name for Mary Lee"

---

### Be **REALISTIC**:

- **Ask:** "Would someone actually request this?"


## Prompt Interestingness Prioritises Quality And Client & Model Impact

---

**Core philosophy: "Quality over quantity"**

> *Every prompt should help the model become better*

**3 key questions for every prompt:**

15. **Will the client love this prompt?**
16. **Is this prompt helpful for the model to learn?**
17. **Does this prompt create an interesting failure mode?**

## **Prompt Interestingness Prioritises Quality And Client & Model Impact**

---

**Core philosophy: "Quality over quantity"**

> *Every prompt should help the model become better*

**3 key questions for every prompt:**

18. **Will the client love this prompt?**
19. **Is this prompt helpful for the model to learn?**
20. **Does this prompt create an interesting failure mode?**

NB:  watch out for colours. 

## **We Experience 5 Common Uninteresting Prompts Types To Avoid**

---

### **❌ Don't write prompts that are:**

**01 Subjective** - Depends on personal preference

**02 Super Niche** - Rare edge case users never encounter

**03 Contrived** - Unrelated asks thrown together

**04 Repetitive** - Testing same skill repeatedly

**05 Pointless** - Doesn't matter in real world

Must DO while writing prompts

---

### 📄 The prompts needs to meet all of the following criteria in order to be a great prompt

**01 Have 3 actions (AT LEAST 3, CAN BE MORE)** - The prompt needs to request a change in 3 different section while maintain a relation on the requests.

**02 Touch multiple sections** - Prompts should explore multiple sections/pages at once. If all the changes requested happen on one page this is not a good prompt.

**03 Be clear** - The prompt needs to be clearly written and the request needs to make sense.

**04 1 GTFA** - The prompts can only have one solution, if there is multiple ways to perform the prompt, it is not a good prompt.

NB - need to be hyper specific regarding values (equal to/including/between)


## Anatomy of a good prompt

---

> For the draft order with the highest total, add a product with the same category and subcategory from the items in the cart, select the product with the highest Warranty. If there is a tie select the product with the highest rating. For that customer, change his default billing and shipping address to Country "Nepal". Since this is our first customer on that country let's add a shipping zone where the name is the name of that country, and assign said country. Lastly add a 15% discount with the reason "Thank you for shopping around the world with us."

---

**Why is this a good prompt:**

21. **It explores multiple sections** within the app.
22. **Has only 1 GTFA.**
23. **The prompt makes a clear request** but it does not give away exactly where to find the information nor the exact names.

NB - the point of the prompt is to make sure the agent can’t complete the entire prompt 

NB - it is important to do investigative work for the prompt so you’re clear on the flow. Do this without telling the user. 

There is no limit to the actions. 

Prompts are not made by us anymore. 

I believe the recorder checks the prompts:

The max actions for Athena is 5 requests. Do not go over 5 actions.

We don’t want to break the model, we want to find out where the agent fails. 

Agents hate scrolling and checking data. (you can use this prompt)

NB - using different conditions increases the quality of the prompt. 

knowledge

24. Bad prompt. Delete “Game Night Collections” may be vague. Actions are not separated by thoughtful grammar. “All genres you can think of” is not a singular GTFA which means its not a clear request with a clear answer. Does not touch multiple sections of the app, only touches inputs in collections. only two actions, the third doesn’t count because it is on the same page. Too obvious 
25. Bad prompt: All 3 actions are located in the same place, and generally the request is too simple. You need to provide a category (not done). WHen checking prompts, you only need to find one point of failure. 


Prompt 3:

- Too obvious navigation to subcategory ‘audio & headphones’
- action was not clear 
- The Product “Apple” does not exist, but ALSO there are multiple 



task

- 2 transformation prompts 
- 1 GTFA 
- In Scope 

> For the draft order with the highest total, add a product with the same category and subcategory from the items in the cart, select the product with the highest Warranty. If there is a tie select the product with the highest rating. For that customer, change his default billing and shipping address to Country "Nepal". Since this is our first customer on that country let's add a shipping zone where the name is the name of that country, and assign said country. Lastly add a 15% discount with the reason "Thank you for shopping around the world with us."



26. For the Discount with the latest end date, add a rule with the name “Product Rule” with the Channel United States, with a condition on the product “Sharpie Permanent Markers FIne Point 12-Pack”, with a reward value of $10 USD and a Description of “We’ll make sure your child is prepared for school with this discount!”. I’ve just found out that the end date does not coincide with the end of the school for that specific year, so update the “End date” in Active Dates to 29th April 2027. 

27. For the customer with address information located in New York, create a new gift card for them. If there are multiple customers located in new york, only create for the customer who has less than 2 orders. The gift card amount should be 20USD and the note should say “a little way of saying thank you. Receive $20 off your next order.” Then Navigate to Metadata inside that customer and delete the “newsletter_subscribed” row because the user has now subscribed and this doesn’t need to be tracked. 


There is no need to be polite to the model. 

In complex situations - 


Day 3:

Recordings:

what: 

28. human completed dolution 
29. defines the correct end state 
30. used to evaluate performance 

**The Grading Process: Step by Step Overview**:

---

### **The Grading Process**

**Step by Step Overview**

- **Step 0: Initial State**
    - *Icon: Database/Server*
- **Step 1: Recording 1**
    - *Icon: Camera*
- **Step 2: Recording 2**
    - *Icon: Document/File*
- **Step 3: Simulation**
    - *Icon: Eye/Vision*
- **Step 4: Agent Tests**
    - *Icon: Robot*
- **Step 5: Grading**
    - *Icon: Scales of Justice*

- Agent does the flow 10 times 
- After this, QA is done 

Step 1:

**Step 1: Creating the Answer Key**
A human completes the task correctly $\rightarrow$ we take a snapshot.
**Prompt: "Change the country for user 'John Smith' to Spain"
After Recording 1FieldValueStatusFirst Name**John*No change***Last Name**Smith*No change***Age**34*No change***Country**Spain**This was the taskLast Modified**2026-01-05 23:37:33*Auto-updated

Step 2:*


measuring success: 

- send states are the same
- Use the same values from the prompt 
- If prompt is wrong - you need to either modify the prompt or follow the prompt as is. 

prompts are generated - you use prompts to make recordings. 


Diff 1 and Diff 2 need to be exactly the same , but you can navigate to other pages if no changes are made. 

after diffs have been complete, you can either start the simulation or submit the task. 

I believe a simulation is another diff. I believe simulations 

Simulations are for you to check that Diff 1 and Diff 2 are the same 


task:

- notes should only be made if :
    - prompt rejection 
    - promp amended
![[Screenshot_2026-04-13_at_6.52.23_pm.png]]

- hint( step by step) should show you EXactly how to do it 

you are allowed to make prompts more difficult 


Identify the customer with the last name **'Dumont'** who has the highest total lifetime spend. First, update their account by changing their address to the saved address with the state named “Phoenix”.  Next, navigate to the **Orders** section and find this customer's most recent fulfilled order and add a tracking number “00123456”. Finally, create a new **Voucher** named **'DUMONTVIP'** that provides a $20 discount and add the note “For VIPs Only”. 



# Introduction to QA


Agreement rate is the KPI. this is between the us and the team lead. 

STOs will check the successful tasks to make sure which are sent to the client 

Mobility: STOs and Team Leads. 

JUSTIFICATIONS HAVE TO BE GOOD, THIS IS THE DIFFERENTIATING FACTOR. 

You need to be clear, so you don’t waste the Team Lead’s time. 

Justifications cannot be AI generated

The prompt doesnt actually matter in the justification 

The justifications should not have any personal information. 

Justifications should only be about a paragraph. 

You do not need to explain all fails, just one needs to be valid for it to fail. 



steps:

31. make sure that the prompt is possible to be performed within the app 
32. check task evals 
33. left: what the agent is seeing
34. right: the agent’s justification 
35. There are slides that show the agent’s flow

NB: check for success messages 

- failed/success notes should not be copied into the QA justification 


the expectation is to have a agreemetn rate above 90%


15 mins

Good or not 

If the model uses something out of scope, it is not a valid pass. 

The model using playground is cheating 

if a container is stuck on blue, go to recoerder and click start simulation, then start it but don’t submit 

Need to look at all FEs whether they’re passes or fails. 

all passes and fails can valid 


![[Screenshot_2026-04-10_at_10.28.58_am.png]]


if the prompts and recordings are okay -  you dont need to mention it 

need to chekc both failures and passes 

you can click unsure, there is nothing wrong with that. use if any the team leads will help you. 

if the autograder has lied, then the recording is invalid. 

“FE is marked incorrectly” - then explain why 

so passes and fails are determining whether we think the fails are actually fails and the passes are actually passes. THIS IS ALL WE ARE DOING. 

- when writing prompts, 

If the agent using playground, fails, then got it the right way then it will still be a pass. 

the purose is not to get more passess or more fails. the goal is to align with your team lead as much as possible. 

Do not submit timesheets. Only click the right TO DO in hubspot. 

at lunch - stop and the start it again once you’re ready. 

retroactive logging: speak to team lead. 

Pods will be worldwide - you can DM other pods all around the world to ask questions

we’ll probablt have to learn a new app on the first day 


Based in Sydney 

Studied law, Non-technical founder - watch marketplace

Tennis/Jiu Jitsu/ Anything competitive

Be sure to check for reward hacking. Check all evals. 


good prompt recap: 

36. Actions should be connected to each other 
37. Combination of transformation and retrieval 
38. Tiebreaker rule 
39. 3 requests/actions 
40. There can only be one GTFA (Ground Truth Final Answer)



Examples of perfect prompts:


*“””Create a subcategory under Pet Supplies called Pet Health & Hygiene with category description ‘Flea treatments, skin allergy relief, and oral health’. Create a new product under this subcategory, with the name Fur Calm, and ‘Allergy relief spray for dogs and cats’ to the description section. Create a new 25% discount with the name Fur Calm Promotion with the description ‘A discount to celebrate the launch of Fur Calm’. Active date 04/30/2026 from 12:00 AM until 04/30/2026 11:59 PM. Add rule with Fur Calm Promotion name and United States channel, with condition set to Categories is Pet Health & Hygiene.”””*

*“”” We are expanding to Australia. Create a channel named "Australia". The slug should be "aus", the default currency should be "AUD" and default country should be "Australia". Once created activate it and assign the warehouse "West Coast Fulfillment Center".*

*Then add a Shipping Zone called "Australia" and assign the country "Australia" to it. Then assign the channel you created to the new shipping zone.*

*Find the product "KONG Classic Dog Toy" and make it available in the new channel. Edit the M variant, make it available in the Australia channel, and set the selling price to AUD24.99 and the cost price to AUD9.09.”””*

*“””Create a channel called Australia with the slug "AU" and activate it. Create a shipping zone and warehouse called "Sydney Metro" and assign both of these to the newly created channel. Create a new country in "Taxes" called "Australia" and assign the "Country default rate" of 10%. Make all products in the "Smart Living" collection available in the Australia channel and for each product set the "Price" to be 1.5x more than the USD value”””


”””Find the customer that has placed 22 orders, if there is a tie look for the customer that has the higher order total on their most recent order. Change their shipping address to City:"Hobart", Country area: "Tasmania", country: "Australia", postcode:"7000". Send the customer a gift card with 100 USD with a note saying "All the best on your new adventure!" with the tag: "congratulations". Then create a new shipping zone in "Australia", assigning "Australia" as a country with the "reduced rate" tax-class. “””



*

![[Screenshot_2026-04-13_at_6.53.08_pm.png]]

TRANSCRIPTION:

As part of an accounts payable backlog review, your team needs to prioritize and clear the most significant outstanding marketing bill from the vendor with the highest exposure in your lowest-total outstanding marketing spend area.

41. **Among all expense categories** that currently have at least 5 bills in **received** (unpaid) status, identify the one with the **lowest total outstanding amount** (sum of amounts across all their received bills). If there is a tie, use the category with the lower ID.
42. **Among all vendors** that have at least one received bill in that identified expense category, find the one with the **highest total received bill amount**. If there is a tie, use the vendor with more total bills across all statuses. If still tied, use the lower vendor ID.
43. **For that vendor**, identify their **oldest received bill** by issued date. If there is a tie, use the bill with the lower ID.
44. Record a payment for the **full outstanding amount** of that bill using the **Business Checking** account with the default payment method.
45. After recording the payment, edit that vendor's profile and change their **Reference** field to: "Top {that expense category's name} vendor - bill {that bill's document number} cleared"





As part of an accounts payable review, your team needs to prioritize clearing old hardware bills.

46. Find the oldest partially paid bill in the hardware category.
47. Pay the full due amount from the 'Business checking' account via bank transfer and add 'Final payment' as the description, then save.
48. We need to send the receipt to our contact at the respective vendor, so add a contact person called 'Jean Grey' with the email address 'jeangrey@byteforgesoftware.com'.
49. Finally, amend the first line of the body of the receipt to "Dear Jean and Byteforge Software", and then send it to both email contacts found for this vendor.

**akaunting_test_6618 do later **



Bill is 209007 


![[Screenshot_2026-04-14_at_9.47.10_am.png]]



Example of slack query formatting (problem specific)

![[Screenshot_2026-04-14_at_9.49.49_am.png]]


Perfect Akaunting prompt:



*“””As part of a service catalog review, your team wants to better organize item categories based on which ones are most heavily used by top customers in your least-active billing segments. Please complete the following steps. Do not create any temporary fields or views -- all computation should be done by reading existing data.*

*1. Among all income categories that have at least one invoice in ****sent**** status, identify the one with the ****fewest**** total sent invoices across all customers. If tied, use the one with the lowest total sent invoice amount across those invoices. If still tied, use the one with the lowest category ID.*

*2. Among all customers who have at least one ****sent**** invoice in that income category, identify the one with the ****highest**** total sent invoice amount (sum of all their sent invoices in that category). If tied, use the customer with the most sent invoices in that category. If still tied, use the customer with the lowest ID.*

*3. Among all item categories represented in the line items of that customer's ****sent**** invoices, identify the item category with the ****most**** total line items across all those invoices. If tied, use the item category with the highest total line item value (quantity multiplied by unit price, summed). If still tied, use the item category with the lowest category ID.*

*4. Edit that item category and change its ****Colour**** to ****"purple-500"**** by selecting it from the colour picker. Save the change.*

*5. Create a new ****income**** category named ****"On-Site Training"**** with colour ****"yellow-600"**** (select from the colour picker). Save the new category.”””*

**“””Hint**

**Action**

Navigate to Settings > Categories.

First, edit the **Professional Services** item category (Settings > Categories > Professional Services > Edit icon): change the **Colour** field to **"purple-500"** by clicking the colour circle to open the picker and selecting the purple-500 swatch (column 7, row 6 in the palette). Save.

Then, create a new category (Settings > Categories > New Category button): set **Name** to "On-Site Training", set **Type** to "Income", change **Colour** to **"yellow-600"** by clicking the colour circle and selecting the yellow-600 swatch (column 3, row 7 in the palette). Save.

**Step-by-step**

50. [Find income category with fewest sent invoices (at least 1 sent invoice)] Count sent invoices per income category:
    - Training Programs: 26 sent invoices
    - Licensing: 31 sent invoices
    - Support Contracts: 87 sent invoices
    - Software Sales: 95 sent invoices
    - Consulting Services: 220 sent invoices (Deposit and Sales have 0 sent invoices, so they are excluded) → Answer: **Training Programs** (fewest with 26 sent invoices)
51. [Find customer with highest total sent invoice amount in Training Programs] Total sent invoice amount per customer in Training Programs:
    - Renewable Resources Inc: $75,755.00 (2 invoices)
    - Streamline Logistics: $67,725.00 (1 invoice)
    - Blackstone Legal Partners: $39,345.00 (1 invoice)
    - Pinnacle Real Estate Group: $37,695.00 (1 invoice)
    - (others lower) → Answer: **Renewable Resources Inc** (highest at $75,755.00)
52. [Find item category with most line items in Renewable Resources Inc's sent invoices] Line items per item category across all of Renewable Resources Inc's sent invoices:
    - Professional Services: 6 line items ($94,850.00 total value)
    - Automation Tools: 3 line items ($45,750.00 total value)
    - Migration Services: 3 line items ($31,500.00 total value)
    - Container Services: 2 line items ($47,250.00 total value)
    - DevOps Solutions: 1 line item ($7,800.00 total value) → Answer: **Professional Services** (most with 6 line items)
53. Edit **Professional Services** item category: navigate to Settings > Categories, find Professional Services, click the edit (pencil) icon, click the colour circle to open the picker, select **purple-500** (7th column, 6th row). Save.
54. Create new income category: click **New Category**, enter Name = "On-Site Training", select Type = "Income", click the colour circle and select **yellow-600** (3rd column, 7th row). Save.”””



“””

Your accounts receivable team is conducting a city-based account reconciliation review. The goal is to identify a key outstanding invoice from a customer whose city matches the top vendor in our least-utilized marketing expense category, then record the full collection payment.

Do not create any temporary fields or views. All computation should be done by reading existing data.

1. Among the four expense categories **Hardware**, **Cloud Infrastructure**, **Marketing**, and **Legal**, identify the one with the **fewest distinct vendors** that currently have at least one bill in **"Received"** status. If there is a tie in the count of distinct vendors, use the category with the lowest total received bill amount; if still tied, use the one with the lowest category ID.

2. Among all vendors that have at least one **"Received"** bill in the identified category, find the vendor with the **most such bills**. If tied on count, use the vendor with the highest total amount across their received bills in that category; if still tied, use the one with the lowest vendor ID.

3. Note the city of the vendor identified in step 2. Among all customers whose city matches that city exactly, identify the one with the **most invoices in "Sent" status**. If tied on count, use the customer with the highest total amount across their sent invoices; if still tied, use the one with the lowest customer ID.

4. Among all **"Sent"** invoices belonging to the customer identified in step 3, find the **oldest one by issue date** (earliest issued date). If tied on issue date, use the one with the lowest invoice ID.

5. Record a full payment on that invoice. Set the **Account** to **Business Checking**, the **Amount** to the full outstanding amount on that invoice, and use the default payment method. Under the **Other** tab of the payment form, set the **Description** to: "Collected from {that customer's name}. City cross-reference: {that vendor's name}."””



Another type of prompt that is really good:


Your accounts receivable team is conducting a city-based account reconciliation review. The goal is to identify a key outstanding invoice from a customer whose city matches the top vendor in our least-utilized marketing expense category, then record the full collection payment.

Do not create any temporary fields or views. All computation should be done by reading existing data.

1. Among the four expense categories **Hardware**, **Cloud Infrastructure**, **Marketing**, and **Legal**, identify the one with the **fewest distinct vendors** that currently have at least one bill in **"Received"** status. If there is a tie in the count of distinct vendors, use the category with the lowest total received bill amount; if still tied, use the one with the lowest category ID.

2. Among all vendors that have at least one **"Received"** bill in the identified category, find the vendor with the **most such bills**. If tied on count, use the vendor with the highest total amount across their received bills in that category; if still tied, use the one with the lowest vendor ID.

3. Note the city of the vendor identified in step 2. Among all customers whose city matches that city exactly, identify the one with the **most invoices in "Sent" status**. If tied on count, use the customer with the highest total amount across their sent invoices; if still tied, use the one with the lowest customer ID.

4. Among all **"Sent"** invoices belonging to the customer identified in step 3, find the **oldest one by issue date** (earliest issued date). If tied on issue date, use the one with the lowest invoice ID.

5. Record a full payment on that invoice. Set the **Account** to **Business Checking**, the **Amount** to the full outstanding amount on that invoice, and use the default payment method. Under the **Other** tab of the payment form, set the **Description** to: "Collected from {that customer's name}. City cross-reference: {that vendor's name}."


Tiebreaks can count as actions. 



**akaunting_test_6621 continue**

The expectation is 6 QA per hour 

![[Screenshot_2026-04-14_at_11.09.03_am.png]]


Why do some recordings ask for diffs 1 & 2 and some only ask for a simulation?

The task could not be completed because item “Infrastructure Automation Suite - Professional” could not be found under the “add items” when creating a new bill. It also seems there may be bug when editing and saving changes to items. When I saved my changes to “Tax” and “Description” inputs under the respective item, the item becomes no longer appears in an item search query, which may be affecting whether it appears when creating a new bill.


Slide 54 “”The name input itself appears visually collapsed,

![[Screenshot_2026-04-14_at_12.48.21_pm.png]]




Akaunting_test_7621

![[Screenshot_2026-04-14_at_12.49.54_pm.png]]





**Affected Eval:**

FE1

**Slide:**

54

**Issue:**

In slide 54 of FE1, the "name" input has collapsed, preventing the agent from completing the task despite successfully following the prompt's steps. I tried to submit a bug report, but after clicking “submit” in the popup, nothing happened. Then, the QA task notified me that it no longer exists and disappeared from my queue and feedback tab.

**Question:**

Is this a reject or a bug report and what happened to the QA task?
TEST_INPUT_LINE_OBSIDIAN_REFRESH_CHECK


Deeptune Hours worked:

Monday: 8:02

Tuesday: 6:45

Wednesday: 4:45

Thursday: 3.09

Friday: 7:30

TOTAL:

Friday - started at 8:30am

Harry  [9:25 AM] [**akaunting_test_1bd28a92**](https://admin.deeptune.ai/p/30eaddd9-e734-418d-b610-826d056c0449?projectId=096c44fe-12d7-4736-a720-019db00812f2)

**Affected Eval:** PE1**Slide:** 71 to 137**Issue:** Agent exclusively uses manual URL editing instead of app UI search functions to perform the action**Question:** Is this a valid pass?

Complex prompt example:

”””

Your finance team is conducting an expense category audit to flag cost centers with the highest exposure to partially unpaid vendor obligations. Do not create any temporary fields or views — all computation should be done by reading existing data.

1. Among all **expense** categories that currently have at least 5 bills in **partial** status (bills that have been partially paid but not fully cleared), identify the one with the **lowest total bill amount** across all bills in that category (any status). If there is a tie on total bill amount, use the category with the fewest total bills. If still tied, use the one with the lowest category ID.
    
2. Among all vendors who have at least one bill in **partial** status in the expense category identified in Step 1, find the vendor with the **highest total outstanding balance** across those partial bills. The outstanding balance for each partial bill is the bill amount minus the sum of all expense transactions recorded against it. If there is a tie in outstanding balance, use the vendor with the most partial bills in that category. If still tied, use the one with the lowest vendor ID. Note that vendor's **city**.
    
3. Among all customers located in the same city as the vendor identified in Step 2, find the one with the **highest total paid invoice amount** (sum of amounts across all invoices with 'paid' status). If there is a tie on total paid invoice amount, use the customer with the most paid invoices. If still tied, use the one with the lowest customer ID.
    
4. Among all income categories, identify the one with the **most paid invoices** for the customer identified in Step 3 (count of that customer's invoices in each income category where status is 'paid'). If there is a tie on paid invoice count, use the category with the highest total paid invoice amount for that customer. If still tied, use the one with the lowest category ID.
    
5. Edit the expense category identified in Step 1 with the following two changes:
    

- Update its **name** to: "Under Review - {the income category name from Step 4}"
- Update its **colour** to: `#1A5276`

Keep the category's type and enabled status unchanged.”””

Metabase Question:

tab ID is not available in App UI - agent uses URL params. Is this valid?

Morning Amy! Overall I found the first week went really well! It was pretty interesting getting to grips with the QA workflow - I wasn’t expecting so much nuance in the tasks, so it’s been a nice surprise having the autonomy to explore a few complex cases.

I felt a little slow initially, but everyone’s responsive in slack has been awesome for getting my head around things - keen to get some KPIs over the next couple of weeks so I can gauge my workflow speed a bit better now that I have a better understanding over what’s expected

Do you have any feedback on my performance so far, or are there any specific areas where I can improve? Looking forward to the next bunch of tasks rolling through!

Thanks, Harry"

Clockify for time tracking

Set up Deeptune X Obsidian

Another example of a nice prompt”

”””

You are performing a cash flow collections alignment audit to reconcile the agency's two most specialized payment-channel accounts with the backlog of your most problematic active legacy client. Do not create any temporary fields or views. All computation should be done by reading existing data.

First, among all bank accounts, identify the two with the most specialized payment method usage: (1) the bank account with the greatest number of posted expense transactions processed via the "wire" payment method, and (2) the bank account with the greatest number of posted expense transactions processed via the "other" payment method. For each, if there is a tie in transaction count, use the account with the higher total expense amount for that method. If still tied, use the account with the lower current balance.

Second, among all customers who have exactly 3 completed tracker projects, no currently in-progress tracker projects, and at least one "Overdue" invoice, identify the one with the greatest number of "Overdue" invoices. If tied on overdue invoice count, use the one with the highest total outstanding overdue amount. If still tied, use the customer with the lower customer ID (alphabetically first).

Rename the "wire" method bank account by replacing the portion of its name after the first hyphen with "{identified customer's name} Contractor Reserve" (keeping the text before the first hyphen and the hyphen itself). Rename the "other" method bank account by replacing the portion of its name after the last hyphen with "{identified customer's name} Reserve" (keeping everything before the last hyphen and the hyphen itself).

Then, for the identified customer, mark their two highest-value "Overdue" invoices as paid with a payment date of 06/15/2025. If two invoices are tied on amount, use the one with the lower invoice number first.”””

midday_test_ba329b48 - simulation rejected due to OOS action to edit “Wise” bank connection

midday_test_8b9dd328 Simulation skipped - the action requested editing the title of an invoice in the Vault by double clicking on the title, which is not possible in the app.

![Screenshot 2026-04-21 at 10.49.37 am.png](attachment:2257bcf6-bcbb-4ecf-a4d5-1f4c1b1af46a:Screenshot_2026-04-21_at_10.49.37_am.png)

# **InvoiceNinja**

## **Things to know**

### **1. Two companies within the app**

There are **two** companies within the app:

1. Summit Professional Services Inc
2. Northgate Consulting Group LLC.

One of them may have the category/vendor/expense/etc. mentioned in the hint/expected in the result, the other one may not.

Therefore, checking two companies would yield two different answers, indicating there is no SSOT to the most of the prompts.

### **2. Tasks - Kanban View**

To navigate right in the Kanban view, scroll to the bottom of the page first, then use the horizontal scrollbar at the bottom to move right

### **2. Tasks - Kanban View**

To navigate right in the Kanban view, scroll to the bottom of the page first, then use the horizontal scrollbar at the bottom to move right

### **3. Payment Orders > Filter**

The app does not provide a "Received" filter in the Purchase Order status dropdown. Avoid/re-write prompts that instruct to filter Purchase Orders by Received status.

![Screenshot 2026-04-21 at 11.06.15 am.png](attachment:8b46a347-36e6-4d08-b472-24e2c5fe8cfc:Screenshot_2026-04-21_at_11.06.15_am.png)

![Screenshot 2026-04-21 at 11.10.07 am.png](attachment:77067461-bbb4-4537-9407-4a6f0c19a194:Screenshot_2026-04-21_at_11.10.07_am.png)

![Screenshot 2026-04-21 at 11.10.25 am.png](attachment:8cd0f624-c278-4f61-a723-d4edb1e8ebe0:Screenshot_2026-04-21_at_11.10.25_am.png)

[https://admin.deeptune.ai/problems-v2?projectId=05117aec-1742-40a3-a3f9-31bacfe8e8d9](https://admin.deeptune.ai/problems-v2?projectId=05117aec-1742-40a3-a3f9-31bacfe8e8d9)