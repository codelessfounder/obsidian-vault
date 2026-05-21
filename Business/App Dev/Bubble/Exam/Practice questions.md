---

---

**Database Structure and Relationships**

**Question:**
You are building a marketplace app where users can post listings for products. Each listing has:

- A title (text)
- A price (number)
- A category (Category data type)
- A seller (linked to the User data type)
1. How would you set up the database to allow a product to belong to multiple categories (e.g., "Electronics" and "Gadgets")?
2. What type of field should the `Category` be, and why?

---

### **Workflows**

**Question:**
You are creating a form for users to submit feedback. When they click the "Submit" button:

- Their input should be saved in a "Feedback" database with fields: `Message`, `Rating` (number), and `Submitted By` (User).
- After submission, the user should see a confirmation message and be redirected to the "Thank You" page.
3. Describe the actions and conditions you would configure in the workflow to achieve this.

---

### **Responsive Design**

**Question:**
You are designing a user profile page. The page contains:

- A profile picture on the left.
- User details (name, bio) on the right.
- A full-width button at the bottom ("Edit Profile").
4. How would you set up the page to ensure it looks good on both desktop and mobile devices?
5. If the profile picture and user details need to stack vertically on smaller screens, how would you configure the layout?

---

### **Data Privacy and Security Rules**

**Question:**
You have a job application app where only:

- Applicants can view their own applications.
- Recruiters can view applications submitted to their company.
6. What privacy rules would you set up in the database to enforce these restrictions?

---

### **Dynamic Data and Repeating Groups**

**Question:**
You are building a to-do list app. Users should see their tasks displayed in a repeating group, filtered by:

- **Assigned User** (current user).
- **Status** (e.g., "Pending" or "Completed").
7. How would you configure the repeating group to filter the tasks dynamically when the user selects a status filter (e.g., "Pending")?

---

### **API Connections**

**Question:**
You want to integrate your Bubble app with a weather API to display the current weather based on a user’s location.

8. How would you configure the API Connector to call the weather API?
9. What steps would you take to display the weather dynamically on a page using the API response?

---

### **Conditionals**

**Question:**
You are building a shopping cart. On the checkout page:

- The "Place Order" button should only be clickable if the cart is not empty.
- If the cart is empty, the button should display a message: "Your cart is empty."
10. How would you configure the button's conditions to achieve this functionality?

---

### **Custom States**

**Question:**
You are building a quiz app. Each question has multiple-choice answers, and you want to:

- Temporarily store the user's selected answer for a question without saving it to the database until the quiz is submitted.
11. How would you use a custom state to store the selected answer temporarily?

---

### **Performance Optimization**

**Question:**
Your app has a list of 10,000 products. A repeating group displays these products, filtered by category and sorted by price.

12. What strategies would you implement to ensure the page loads quickly while maintaining a good user experience?

---

### **Version Control and Collaboration**

**Question:**
You’re working with a team on an app and are about to launch a major feature update. Before going live:

- The team needs to test the new feature without disrupting the live version.
13. How would you use Bubble's version control system to safely roll out this update?
14. What best practices would you follow to ensure collaboration is smooth during the update process?