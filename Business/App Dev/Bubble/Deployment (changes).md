---

---

### **How Changes Work in a Live Bubble App:**

1. **Development vs. Live Versions**
    - **Development version:** This is where you make and test changes.
    - **Live version:** This is what your users see. You can push updates from the development version to the live version once you’re satisfied.
2. **Making Changes Without Disrupting Users:**
    - You can make changes in the **Development** version without affecting the **Live** version. This lets you test new workflows or features safely.
    - When you're ready to go live with changes, you **deploy** them to the live version.
3. **Deployment Process:**
    - Once changes are tested, click **"Deploy to Live"** in the Bubble editor. The app will update with the new features and data structure.
    - Deployment typically takes a few minutes, and users won’t experience downtime unless the change involves breaking core features (e.g., login issues or API dependencies).
4. **Database Impact:**
    - If you're modifying the **database structure** (like adding or deleting fields), these changes will need to be reflected in both versions. Bubble will handle most structural changes seamlessly, but:
        - Be careful if you are deleting or renaming fields that are being used in the live version.
        - You can copy live data to the development database for testing, ensuring nothing breaks during deployment.
5. **Limitations During Live Changes:**
    - If you have users actively using the app, deploying big changes could cause interruptions (e.g., if a new feature changes the way users interact with key elements).
    - Bubble does not offer version control in the same way as traditional software development platforms, meaning you can’t roll back specific changes easily. However, you can **revert the entire app** to a previous state (e.g., to how it was an hour ago).
6. **Feature Flags & Conditionals:**
If you want to release new features progressively or test them with a subset of users:
    - Use **custom states or conditionals** to only show new features to selected users.
    - Alternatively, you can create a **Beta version** of your app by using a separate deployment environment for specific user testing.

---

### **In Summary:**

Making changes to your Bubble app after it goes live is straightforward:

- Work in the **development version**, test thoroughly, and then **deploy to live**.
- Avoid deleting critical database fields or workflows without careful planning.
- For larger updates, consider using feature flags or staging releases to minimize disruption.

Let me know if you'd like help planning your update strategy or have specific concerns about your setup!



Deployment prep:

7. Fix issues 
8. Connect domain 
9. Change Stripe payments to live 
10. Check mobile responsiveness
