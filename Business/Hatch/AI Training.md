---
tags:
  - ai-training
  - playbook
status: draft
source: deeptune-derived
---

# AI Training

This is my single-file playbook for AI training roles.

It captures reusable methods for prompt writing, recording, evaluation, QA judgment, and operational execution across different apps and clients.

Deeptune references are included as contextual examples, not the focus of this document.

---

## Migration Protocol

- Source note: `Business/Hatch/Deeptune.md`
- Rule: keep the source note unchanged until this file is complete and approved.
- Process: extract, rewrite, and normalize content here first; delete the legacy note only after final review.

---

## Overview

Purpose:
- Capture reusable AI training methods for prompt writing, recording, evaluation, QA, and operations.
- Keep this as a practical playbook that transfers across tools, clients, and app domains.

How to use:
- Use this file as the default checklist before writing prompts, recording runs, and submitting QA decisions.
- Update this file whenever a new failure mode, pattern, or decision rule appears in real work.

---

## Core Principles

- Quality over quantity.
- One clear GTFA (Ground Truth Final Answer) where required.
- Strict instruction adherence and data integrity.
- Realistic, feasible, in-scope tasks over contrived tasks.
- Agents learn from measurable, well-diagnosed failures.
- Ask clarifying questions early when ambiguity blocks quality.
- Be skeptical of outputs: verify with evidence, not assumptions.
- Prefer complete and correct work over fast but noisy work.

### Rubric-First Mindset

- Capture exact constraints, not just broad intent.
- Treat required wording, formatting, sign-offs, and scope rules as hard requirements.
- Grade the output against the prompt and source material line-by-line when needed.
- If one critical requirement is violated, treat that as decisive.

---

## Prompt Design Framework

### Prompt Types

- Transformation prompts: create/edit/update/delete/move data with persistent state changes.
- Extraction prompts: retrieve data without changing app state.

### Prompt Quality Rules

- Require clear, unambiguous instructions.
- Avoid relative dates; use fixed dates.
- Avoid multiple valid solutions unless tie-breakers are explicit.
- Keep prompts realistic to user behavior and platform constraints.
- Use explicit values and precise conditions.
- Keep tasks in scope (no external integrations, imports, exports, or out-of-band tooling unless explicitly allowed).
- Ensure the task can actually be executed in the current app state.

### Action and Scope Design

- Prefer connected multi-step actions that test reasoning across multiple sections.
- Keep action complexity intentional; avoid pointless difficulty.
- Use tie-breakers to preserve a single correct resolution path.
- Avoid trivial repetition that tests the same skill repeatedly.
- Prefer prompts that force careful reading, filtering, and decision quality.
- If there is a platform-specific action cap, respect that cap.

### Prompt Quality Filters

Reject or rewrite prompts that are:
- Subjective (preference-based, no objective grading path).
- Super niche (unlikely real-world use case).
- Contrived (disconnected requests joined artificially).
- Repetitive (same operation with different names only).
- Pointless (low model-learning value or low user relevance).

### Prompt Design Questions

Before finalizing a prompt, ask:
- Will a client find this task realistic and useful?
- Will this task teach a model something transferable?
- Does this create an interesting, diagnosable failure mode?
- Can I defend one clear end-state as the answer key?
- Is this prompt hard in a meaningful way, not just long?

---

## Recording and Evaluation Workflow

- Prompt creation and feasibility check in-app.
- Recording pass 1 (gold path candidate).
- Recording pass 2 (must match intended end state).
- Simulation and agent attempts.
- QA review and final pass/fail justification.

### Recording Quality Standards

- End state must match prompt intent exactly.
- Diff outputs should align across recordings where required.
- Correctness beats speed when recordings define grading outcomes.
- If recordings diverge, debug before submitting.
- Do not rely on memory; each run should be reproducible from app state.
- Use simulation to validate that answer-key logic is stable.

### Practical Recording Notes

- Open the app and perform the workflow before finalizing the prompt.
- Verify entities exist before writing hard constraints around them.
- If a prompt is impossible, amend or reject based on policy and document the reason.
- Keep internal notes only when required by process (for example: amended prompt or rejection reason).
- Keep recordings clean: no unnecessary detours that can confuse grading.

---

## Failure Modes Library

- Hallucination/Ghost data: invents or re-asks for already provided information.
- Logic defects: loops, dead ends, or broken routing.
- Data integrity: dropped fields, altered values, or mismatched tables/text.
- Instruction/format: misses required sign-off, phrasing, locale, or structure.
- Scope/tooling: uses prohibited methods or bypasses required workflow.
- Environment/platform: blocked by UI bugs, missing records, or unstable app state.

---

## QA Decision Framework

- Validate whether the observed outcome matches prompt requirements and scope.
- A single valid critical failure is enough for a fail decision.
- Do not rely blindly on autograder outputs when evidence conflicts.
- Keep justifications concise, evidence-based, and free of personal data.

### QA Justification Standard

- State the key failure or success condition.
- Explain why it materially affects task validity.
- Reference observable behavior rather than assumptions.
- Keep it concise (short paragraph), specific, and policy-aligned.
- Do not include personal data or irrelevant narrative.

### QA Review Flow

1. Confirm prompt feasibility and scope.
2. Inspect evaluation evidence (slides, actions, end-state).
3. Compare required state vs actual state.
4. Check for prohibited behavior and policy violations.
5. Decide pass/fail/unsure with one defensible rationale.

### QA Guardrails

- Do not optimize for more passes or more fails; optimize for agreement with rubric and leads.
- Check both passes and fails carefully; both can be wrong.
- If automation contradicts visible evidence, trust evidence and explain.
- Use "unsure" when evidence is ambiguous or blocked by platform issues.
- Separate "agent failed" from "environment failed" before deciding.

---

## Operational Heuristics

- Open and test app flows before writing prompts.
- Ask blocking questions early, not at the end.
- Track app-state and performance issues that affect task validity.
- Prioritize stable execution over rushed throughput.
- Escalate blockers clearly when platform bugs prevent completion.
- Verify you are in the correct app and environment before starting.
- Avoid actions known to break state (for example, logging out if session design discourages it).
- Keep work restartable in case of app stalls, queue drops, or container issues.

---

## Deeptune-Derived Learnings

This section captures lessons learned from Deeptune-context workflows while keeping guidance generalized for future roles and teams.

### Contextual Examples

- Complex prompt design benefits from explicit tie-break hierarchies.
- Agents often fail on scrolling, lookup, and data verification tasks more than basic edits.
- High-quality prompts are connected workflows, not isolated clicks.
- The strongest QA notes identify one concrete policy or state mismatch and explain impact.
- Platform instability can mimic model failure; always separate environment issues from agent behavior.

### Questions to Ask in Any New AI Training Role

- How are edge cases defined and handled in this environment?
- How is improvement measured (internal rubric vs external benchmarks)?
- What is the loop time from failure detection to retraining or policy update?
- What evidence is required for pass/fail in QA?
- What behaviors are explicitly out of scope?
- What does success in the first 30 days look like?
- What is the flow of tasks like? My previous role was poor in setting KPIs and workload expectations (lack of, inconsistent)

---

## Reusable Checklists

### Pre-Prompt Checklist

- Is the task feasible in the live app?
- Is there one clear GTFA (when required)?
- Are constraints explicit and testable?
- Are dates, values, and tie-breakers specific?
- Is there any hidden ambiguity that could create multiple valid solutions?
- Would a real user plausibly ask for this?
- Is this prompt teaching a meaningful skill, not just generating activity?

### Pre-Recording Checklist

- Is the app in the expected starting state?
- Are all target entities present and selectable?
- Can each action be completed without out-of-scope behavior?
- Did I verify every referenced object exists before hard-coding values?
- Can I repeat this flow and get the same result?

### Pre-QA Checklist

- Does the result match required state and scope?
- Is the pass/fail rationale based on direct evidence?
- Is one valid decisive issue identified (if failing)?
- Did I separate agent error from environment/platform error?
- Is my justification concise, specific, and free of personal details?
- If I mark fail, can another reviewer verify it quickly from evidence?

---

## Fast Anti-Error Checklist

- Instruction following: mandatory phrase/sign-off/format present?
- Data integrity: text and tables consistent?
- Completeness: all requested fields/actions addressed?
- Scope: no prohibited tools/workarounds used?
- Logic: any loop, dead-end, or unhandled edge case?
- Evidence: can I point to exact proof for my verdict?

---

## Interview and Role Transfer

- Convert this playbook into concise stories that show judgment, rigor, and reliability.
- Emphasize how you design tasks, detect failures, and defend QA decisions with evidence.
- Use concrete examples of preventing hallucination, enforcing data integrity, and handling ambiguity.

### Story Bank Prompts

- "Describe a time you prevented a false pass by catching a single decisive mismatch."
- "Describe how you redesigned a weak prompt into one clear GTFA with tie-breakers."
- "Describe a case where platform instability looked like model failure and how you separated the two."
- "Describe your QA philosophy in one paragraph."

### One-Paragraph QA Philosophy

I treat QA as evidence-based state verification, not opinion scoring. I compare prompt requirements to observed outcomes, enforce scope and policy constraints, and use one decisive valid issue to justify a fail when needed. I avoid overfitting to automation signals, separate platform defects from agent mistakes, and prioritize clear, concise justifications that another reviewer can quickly validate.

---

## Appendix: Deeptune Artifacts

### Prompt Transcripts 

#### Prompt A: Draft Order 

```text
For the draft order with the highest total, add a product with the same category and subcategory from the items in the cart, select the product with the highest Warranty. If there is a tie select the product with the highest rating. For that customer, change his default billing and shipping address to Country "Nepal". Since this is our first customer on that country let's add a shipping zone where the name is the name of that country, and assign said country. Lastly add a 15% discount with the reason "Thank you for shopping around the world with us."
```

#### Prompt B: Latest Discount Rule Update

```text
For the Discount with the latest end date, add a rule with the name "Product Rule" with the Channel United States, with a condition on the product "Sharpie Permanent Markers Fine Point 12-Pack", with a reward value of $10 USD and a Description of "We'll make sure your child is prepared for school with this discount!". I've just found out that the end date does not coincide with the end of the school for that specific year, so update the End date in Active Dates to 29th April 2027.
```

#### Prompt C: New York Customer Gift Card + Metadata Cleanup

```text
For the customer with address information located in New York, create a new gift card for them. If there are multiple customers located in New York, only create for the customer who has less than 2 orders. The gift card amount should be 20USD and the note should say "a little way of saying thank you. Receive $20 off your next order." Then navigate to Metadata inside that customer and delete the "newsletter_subscribed" row because the user has now subscribed and this doesn't need to be tracked.
```

#### Prompt D: Dumont Customer Workflow

```text
Identify the customer with the last name 'Dumont' who has the highest total lifetime spend. First, update their account by changing their address to the saved address with the state named "Phoenix". Next, navigate to the Orders section and find this customer's most recent fulfilled order and add a tracking number "00123456". Finally, create a new Voucher named 'DUMONTVIP' that provides a $20 discount and add the note "For VIPs Only".
```

#### Prompt E: AP Backlog Review (Marketing Received Bills)

```text
As part of an accounts payable backlog review, your team needs to prioritize and clear the most significant outstanding marketing bill from the vendor with the highest exposure in your lowest-total outstanding marketing spend area.

1. Among all expense categories that currently have at least 5 bills in received (unpaid) status, identify the one with the lowest total outstanding amount (sum of amounts across all their received bills). If there is a tie, use the category with the lower ID.
2. Among all vendors that have at least one received bill in that identified expense category, find the one with the highest total received bill amount. If there is a tie, use the vendor with more total bills across all statuses. If still tied, use the lower vendor ID.
3. For that vendor, identify their oldest received bill by issued date. If there is a tie, use the bill with the lower ID.
4. Record a payment for the full outstanding amount of that bill using the Business Checking account with the default payment method.
5. After recording the payment, edit that vendor's profile and change their Reference field to: "Top {that expense category's name} vendor - bill {that bill's document number} cleared".
```

#### Prompt F: AP Review (Old Hardware Bills)

```text
As part of an accounts payable review, your team needs to prioritize clearing old hardware bills.

1. Find the oldest partially paid bill in the hardware category.
2. Pay the full due amount from the Business Checking account via bank transfer and add "Final payment" as the description, then save.
3. Add a contact person called "Jean Grey" with the email address "jeangrey@byteforgesoftware.com" for the respective vendor.
4. Amend the first line of the body of the receipt to "Dear Jean and Byteforge Software", and then send it to both email contacts found for this vendor.
```

#### Prompt G: Service Catalog Review (Akaunting)

```text
As part of a service catalog review, your team wants to better organize item categories based on which ones are most heavily used by top customers in your least-active billing segments. Please complete the following steps. Do not create any temporary fields or views -- all computation should be done by reading existing data.

1. Among all income categories that have at least one invoice in sent status, identify the one with the fewest total sent invoices across all customers. If tied, use the one with the lowest total sent invoice amount across those invoices. If still tied, use the one with the lowest category ID.
2. Among all customers who have at least one sent invoice in that income category, identify the one with the highest total sent invoice amount (sum of all their sent invoices in that category). If tied, use the customer with the most sent invoices in that category. If still tied, use the customer with the lowest ID.
3. Among all item categories represented in the line items of that customer's sent invoices, identify the item category with the most total line items across all those invoices. If tied, use the item category with the highest total line item value (quantity multiplied by unit price, summed). If still tied, use the item category with the lowest category ID.
4. Edit that item category and change its Colour to "purple-500" by selecting it from the colour picker. Save the change.
5. Create a new income category named "On-Site Training" with colour "yellow-600" (select from the colour picker). Save the new category.
```

#### Prompt H: City-Based AR Reconciliation

```text
Your accounts receivable team is conducting a city-based account reconciliation review. The goal is to identify a key outstanding invoice from a customer whose city matches the top vendor in our least-utilized marketing expense category, then record the full collection payment.

Do not create any temporary fields or views. All computation should be done by reading existing data.

1. Among the four expense categories Hardware, Cloud Infrastructure, Marketing, and Legal, identify the one with the fewest distinct vendors that currently have at least one bill in "Received" status. If there is a tie in the count of distinct vendors, use the category with the lowest total received bill amount; if still tied, use the one with the lowest category ID.
2. Among all vendors that have at least one "Received" bill in the identified category, find the vendor with the most such bills. If tied on count, use the vendor with the highest total amount across their received bills in that category; if still tied, use the one with the lowest vendor ID.
3. Note the city of the vendor identified in step 2. Among all customers whose city matches that city exactly, identify the one with the most invoices in "Sent" status. If tied on count, use the customer with the highest total amount across their sent invoices; if still tied, use the one with the lowest customer ID.
4. Among all "Sent" invoices belonging to the customer identified in step 3, find the oldest one by issue date (earliest issued date). If tied on issue date, use the one with the lowest invoice ID.
5. Record a full payment on that invoice. Set the Account to Business Checking, the Amount to the full outstanding amount on that invoice, and use the default payment method. Under the Other tab of the payment form, set the Description to: "Collected from {that customer's name}. City cross-reference: {that vendor's name}."
```

#### Prompt I: Pet Supplies Launch Workflow

```text
Create a subcategory under Pet Supplies called Pet Health & Hygiene with category description "Flea treatments, skin allergy relief, and oral health". Create a new product under this subcategory, with the name Fur Calm, and "Allergy relief spray for dogs and cats" in the description section. Create a new 25% discount with the name Fur Calm Promotion with the description "A discount to celebrate the launch of Fur Calm". Active date 04/30/2026 from 12:00 AM until 04/30/2026 11:59 PM. Add rule with Fur Calm Promotion name and United States channel, with condition set to Categories is Pet Health & Hygiene.
```

#### Prompt J: Australia Channel + Shipping + Variant Pricing

```text
We are expanding to Australia. Create a channel named "Australia". The slug should be "aus", the default currency should be "AUD" and default country should be "Australia". Once created activate it and assign the warehouse "West Coast Fulfillment Center".

Then add a Shipping Zone called "Australia" and assign the country "Australia" to it. Then assign the channel you created to the new shipping zone.

Find the product "KONG Classic Dog Toy" and make it available in the new channel. Edit the M variant, make it available in the Australia channel, and set the selling price to AUD24.99 and the cost price to AUD9.09.
```

#### Prompt K: Australia Channel + Tax + Collection Repricing

```text
Create a channel called Australia with the slug "AU" and activate it. Create a shipping zone and warehouse called "Sydney Metro" and assign both of these to the newly created channel. Create a new country in Taxes called "Australia" and assign the Country default rate of 10%. Make all products in the Smart Living collection available in the Australia channel and for each product set the Price to be 1.5x more than the USD value.
```

#### Prompt L: 22-Orders Customer + Gift Card + Shipping Zone

```text
Find the customer that has placed 22 orders, if there is a tie look for the customer that has the higher order total on their most recent order. Change their shipping address to City "Hobart", Country area "Tasmania", country "Australia", postcode "7000". Send the customer a gift card with 100 USD with a note saying "All the best on your new adventure!" with the tag "congratulations". Then create a new shipping zone in Australia, assigning Australia as a country with the reduced rate tax-class.
```

#### Prompt M: Expense Category Audit (Partial Bills)

```text
Your finance team is conducting an expense category audit to flag cost centers with the highest exposure to partially unpaid vendor obligations. Do not create any temporary fields or views — all computation should be done by reading existing data.

1. Among all expense categories that currently have at least 5 bills in partial status (bills that have been partially paid but not fully cleared), identify the one with the lowest total bill amount across all bills in that category (any status). If there is a tie on total bill amount, use the category with the fewest total bills. If still tied, use the one with the lowest category ID.
2. Among all vendors who have at least one bill in partial status in the expense category identified in Step 1, find the vendor with the highest total outstanding balance across those partial bills. The outstanding balance for each partial bill is the bill amount minus the sum of all expense transactions recorded against it. If there is a tie in outstanding balance, use the vendor with the most partial bills in that category. If still tied, use the one with the lowest vendor ID. Note that vendor's city.
3. Among all customers located in the same city as the vendor identified in Step 2, find the one with the highest total paid invoice amount (sum of amounts across all invoices with paid status). If there is a tie on total paid invoice amount, use the customer with the most paid invoices. If still tied, use the one with the lowest customer ID.
4. Among all income categories, identify the one with the most paid invoices for the customer identified in Step 3 (count of that customer's invoices in each income category where status is paid). If there is a tie on paid invoice count, use the category with the highest total paid invoice amount for that customer. If still tied, use the one with the lowest category ID.
5. Edit the expense category identified in Step 1 with the following two changes: update its name to "Under Review - {the income category name from Step 4}" and update its colour to #1A5276. Keep the category's type and enabled status unchanged.
```

#### Prompt N: Cash Flow Collections Alignment Audit

```text
You are performing a cash flow collections alignment audit to reconcile the agency's two most specialized payment-channel accounts with the backlog of your most problematic active legacy client. Do not create any temporary fields or views. All computation should be done by reading existing data.

First, among all bank accounts, identify the two with the most specialized payment method usage: (1) the bank account with the greatest number of posted expense transactions processed via the wire payment method, and (2) the bank account with the greatest number of posted expense transactions processed via the other payment method. For each, if there is a tie in transaction count, use the account with the higher total expense amount for that method. If still tied, use the account with the lower current balance.

Second, among all customers who have exactly 3 completed tracker projects, no currently in-progress tracker projects, and at least one Overdue invoice, identify the one with the greatest number of Overdue invoices. If tied on overdue invoice count, use the one with the highest total outstanding overdue amount. If still tied, use the customer with the lower customer ID (alphabetically first).

Rename the wire method bank account by replacing the portion of its name after the first hyphen with "{identified customer's name} Contractor Reserve" (keeping the text before the first hyphen and the hyphen itself). Rename the other method bank account by replacing the portion of its name after the last hyphen with "{identified customer's name} Reserve" (keeping everything before the last hyphen and the hyphen itself).

Then, for the identified customer, mark their two highest-value Overdue invoices as paid with a payment date of 06/15/2025. If two invoices are tied on amount, use the one with the lower invoice number first.
```

### Sample Answers 

#### Artifact 4: Workflow Logic Audit Response
A strong failure diagnosis format that links specific technical defects to operational/business impact.

```text
I noticed 3 main issues with this automation workflow that doesn't entirely meet the viable logic required of a functioning workflow:
1. Infinite loop: It seems that all leads received to Marcus have a red arrow that direct leads back to the product interest node, creating an infinite cycle for certain deals.
2. Missing SLA targeting logic: All deals move to a singular SLA priority node, which makes it unclear as to how different deals will be assigned different SLAs.
3. Lack of error handling for deal classification: If a deal is not classified, it simply reverts into the "other" category instead of being properly processed, resulting in potentially unqualified leads being processed.
This is a problem for the model lab/agent creator because it fails to consider unsuccessful data points and/or data edge cases, which creates a higher chance of creating incomplete workflows that need continuous debugging.
This is a problem for the sales lead because improperly categorised leads could result is missed deal opportunities which could directly impact company revenue.
```

#### Artifact 5: Comparative Response Evaluation (A vs B)
A good example of concise preference justification using instruction adherence, user utility, and friction reduction.

```text
Response A is much more favorable. It adheres to the user's main instruction to communicate the policy that the customer "doesn't need to return the damaged item" and the required employee sign off of "Kind regards, Morgan Ellis, Customer Support. Response B outputs an ambiguous "we can sort something out for you", as well as creating unnecessary customer friction by wrongly requesting more photos from the customer in order to process the issue. Response A follows the necessary formatting constraints that make it a significantly stronger output than Response B.
```

---

## Reference Screenshots

![[Screenshot_2026-04-13_at_6.52.23_pm.png]]
![[Screenshot_2026-04-10_at_10.28.58_am.png]]
![[Screenshot_2026-04-13_at_6.53.08_pm.png]]
![[Screenshot_2026-04-14_at_9.47.10_am.png]]
![[Screenshot_2026-04-14_at_9.49.49_am.png]]
![[Screenshot_2026-04-14_at_11.09.03_am.png]]
![[Screenshot_2026-04-14_at_12.48.21_pm.png]]
![[Screenshot_2026-04-14_at_12.49.54_pm.png]]


