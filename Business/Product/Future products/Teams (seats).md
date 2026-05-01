---

---

### **1. Set Up Your Database**

You’ll need new data types and fields to support teams and seats.

### Data Types and Fields:

1. **Team**
    - `Name` (text): Name of the team.
    - `Owner` (User): The user who owns the team.
    - `Members` (List of Users): A list of users in the team.
    - `Seats` (number): The maximum number of users allowed in the team (optional).
2. **User**
    - Add a field: `Team` (Team): Links the user to their assigned team.
    - Add a field: `Role` (text): Define user roles like `Owner`, `Admin`, or `Member` within the team.
3. **Invitation (Optional for Team Invites)**
    - `Email` (text): Email of the person invited.
    - `Team` (Team): The team they’re invited to.
    - `Status` (text): Whether the invite is pending, accepted, or declined.

---

### **2. Create the UI for Teams**

### Pages/Components to Include:

4. **Team Management Page (Owner/Admin View)**
    - Display the team name and a list of current members.
    - Include an "Add Member" button to invite new members.
    - Show the number of seats used vs. available (if applicable).
5. **Join/Accept Invitation Page**
    - Allow users to accept team invites by linking their user account to the team.
    - Optionally show the team details before they join.
6. **Permissions Page (Optional)**
    - Allow admins to assign roles or permissions to team members (e.g., who can add/remove members, access specific features).

---

### **3. Workflows for Team Management**

### Create a Team:

7. Add a "Create Team" button.
8. Workflow:
    - **Action**: `Create a new Team`.
    - Fields:
        - `Name`: Set from an input field.
        - `Owner`: Set to the current user.
        - `Members`: Add the current user.
9. Update the User’s `Team` field to the newly created team.

---

### Add a Member (Invite via Email):

10. Add a "Send Invitation" button.
11. Workflow:
    - **Action**: `Create a new Invitation`.
    - Fields:
        - `Email`: Set from an input field.
        - `Team`: Set to the current user’s team.
        - `Status`: Set to `Pending`.
12. Send an email to the invited user with a link to accept the invite:
    - Use Bubble’s built-in email action to include the team invite link.

---

### Accept an Invitation:

13. Create a page where users can accept invitations.
14. Workflow when they accept:
    - **Search for Invitation**: Match the email and team from the URL parameters.
    - Add the user to the `Members` list in the `Team` data type.
    - Update the user’s `Team` field with the accepted team.
    - Optionally update the `Invitation` status to `Accepted`.

---

### Limit Seats (Optional):

15. When adding members:
    - Add a condition: `Team's Members:count < Team's Seats`.
    - If the count exceeds the seat limit, display an error message.

---

### **4. Manage Permissions**

Use conditional statements to ensure only authorized users can perform certain actions.

### Example Conditionals:

- To show "Add Member" button:
    - **Condition**: `Current User's Role is Owner or Admin`.
- To allow a user to remove members:
    - **Condition**: `Current User's Role is Owner`.

---

### **5. Optional Features**

### Allow Multiple Teams per User:

- Instead of linking `User` to a single `Team`, use a list:
    - Field: `Teams` (List of Teams) in the `User` data type.
    - Add functionality for users to switch between teams.

### Enable Billing for Seats:

- Add a `Billing` data type to track team subscription plans.
- Include workflows for upgrading seat limits and validating payment.

---

### Summary:

16. **Database**: Set up `Team`, `User`, and optional `Invitation` data types.
17. **UI**: Create pages for managing teams, sending invites, and accepting invites.
18. **Workflows**: Handle team creation, member management, and permissions.
19. **Optional Enhancements**: Add billing and multi-team support.

Let me know if you’d like help with specific workflows or setups!