---

---

| Design | Functionality  |
| --- | --- |
| Landing Page  | Repeating groups |
| Nav bar  | Element conditions |
| Footer  | Links  |
| Element style  | Search bar & Get page data from URL  |
| Dashboard  | Sign in/logout |
| Sign in page  | Option sets  |
| Log in page  | States |
| Reusable elements | State Lists |
| Pop Ups  | Custom events |
| Toggle button | Custom states  |
| logged-in user dropdown | User data privacy  |
| Admin account & user analytics | Workflow that deletes hosted file and uncompleted use file submissions  |
| Responsive design (desktop, mobile, tablet) | Toggle button functionality  |
| Mobile version | Dynamic table data  |
| Google inspect (Mobile responsiveness) | Search function (table data with filter fields) |
| Bubble GPT | Popup steps (states) |
|   | Creating a thing  |
|   | Making changes to a thing  |
|   | Charts  |
|   | Unit talleys sorted by creation date  |
|   | Page redirects (privacy) |
|   | Admin account & User Analytics 2 |
|   | Constraints/expression filters |
|   | Admin privacy settings  |
|   | Mobile version  |
|   | Race conditions (Custom event to stop bubble running workflow steps simultaneously)  |
|   | App optimisations  |
|   | App SEO - Alt tags, SVG & WebP, Lighthouse, HTML tags (most important text on page)  |
|   | Payments integration (Stripe, Lemonsqueezy) |
|   | Email integration (Sendgrid, Loops, mailerlite, mailersend) |
|   | DIY plugins (Javascript) |
|   | API connector |
|   | Deleting a thing  |
|   | Displaying data in an element of a thing  |
|   | Creating a random ID  |
|   | API workflows/backend API |
|   | Bubble GPT |

[https://bubble.io/plugin/animated-backgrounds-1653386346535x975715712343474200](https://bubble.io/plugin/animated-backgrounds-1653386346535x975715712343474200)

option sets: 

1. Create option set 
2. Create element you want the option set data to appear in 
3. Change “type of content” in *element appearance to *the name of the option set 
4. Change *data source * to “all (name of option set)” 
5. Logic should appear blue 

Note: Option sets are referenced/linked via the data type. For example, 

“*current row’s application’s status’s display”*

- *application *is the data type 
- *status *is the field within that data type 
- *option set *is the list of preferences that relate to “status”
    - this option set list would consist of different types of status’s (approved, pending, declined, etc)
    - Option sets are the data that we wish to show to the user. We create the option sets. 
    - Data fields is the data that the user wishes to see 
    - Data types are the broad groups of data fields that the user wishes to see



Sign in: 

6. Create sign in page design 
7. Set custom states based on different user types in Workflows 
- e.g. Company or Candidate, Patient or Plastic Surgeon
8. Create New User Type in Data Tab
9. Set up workflow for each button 
10. Set up conditional expressions for button design 
11. Make sure “*this input should not be empty” *is checked in the appearance tab
12. Add conditional expression to sign up button for when inputs have not been filled in (add in Primary button styling)
13. Add workflow “*sign user up” to *sign up submit primary button on sign up page 
    - E.g. “input type your email’s value” is the first condition in the workflow 
    - Remember to do *confirmation email*
14. Add conditional statement to *submit primary button:* “when checkbox i agree to terms of service…. element isnt clickable”
15. Reference custom state made earlier in the “checkbox conditional statement” 
16. Add confirmation email in workflow 
17. Responsive Design 



Custom states:

Log in:

18. Copy and paste Sign up page 
19. Make edits to text relevant to a log in page 
20. Change “sign up” to “log in”
21. Add “log the user in” workflow to log in button 
    - Stay logged in no 
    - Remember email yes 



4 main factors that affect SEO:

22. Performance 
23. Accessibility 
24. Best Practices 
25. SEO

- Use SVG images: Tiny in size and are preferred by search engines
- WebP: created by Google for better image compression and higher quality output 
    - For images that the app creator has control over, you want to be using WebP. This will greatly impact performance and how Google ranks your site.
- ALT tags: allows Google to know what company you have on your home page through the images you upload 
    - “*current cell’s company’s display *Logo”
- Colour contrast: Google ranks how legible your site is based on colours (see tool [Coolors.co](http://coolors.co/) contrast checker)
- Internal linking strategy: Link elements, NO buttons. Put links in footer and header. All pages should link to all pages. 
    - Use buttons only when you need to run a workflow. Links are faster. 


- SEO Title & Description conditional statement @ Page level 
- Fill out SEO settings and Metatags
- 301 redirections


Deployment checklist: 

26. Bubble app plan 
27. Domain settings 
28. SEO settings 
29. Privacy rules 
30. Test all user types and page redirects
31. Third part integration tests 
32. Responsive design 
33. Unfixed issues 





