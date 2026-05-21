---

---

To test the speed of your Bubble.io app, there are several ways to approach it, both manually and with plugins/tools. While Bubble doesn’t have native speed-testing tools, you can measure performance through external services and performance-enhancing plugins.

### **Quick Solution**:

- **Use Google Lighthouse**: Audit your app's speed directly from Chrome DevTools.
- **Plugins for Monitoring**:
    - **Page Speed Insights Plugin** – Displays Google Lighthouse scores directly in your app.
    - **FameMon (Page Analytics)** – Tracks page load times and other analytics in real-time.

If you’re debugging speed issues within Bubble itself, also consider using:

- **Bubble’s Server Logs**: Identify slow workflows.
- **Chrome DevTools**: Measure network performance and resource bottlenecks.

---

### **Step-by-Step: How to Test App Speed and Optimize**

### **Option 1: Using Google Lighthouse (Recommended)**

1. **Open your app** in a Chrome browser.
2. Right-click on the page and select **"Inspect"** to open Chrome DevTools.
3. Navigate to the **"Lighthouse" tab** (or install the Lighthouse extension).
4. Choose to generate a **performance report** for mobile or desktop.
5. Review the metrics, particularly:
    - **First Contentful Paint (FCP)**: How long the first visual elements take to load.
    - **Time to Interactive (TTI)**: When the page is fully interactive.

**Pro Tip**: Run multiple tests to account for variability in performance.

---

### **Option 2: Using Plugins within Bubble**

6. **Page Speed Insights Plugin**:
    - Install from the Bubble Plugin Marketplace.
    - This plugin pulls real-time Google PageSpeed metrics into your Bubble app's dashboard.
7. **FameMon - Page Analytics**:
    - Tracks performance data (page load times, device types, etc.) from within your app.
    - Ideal if you want **continuous monitoring** for end-users.

---

### **Option 3: Analyzing with Bubble Server Logs**

8. Go to **Bubble Editor** → **Logs**.
9. Review server logs for workflows and processes taking **more than a few seconds**.
10. Use this to spot inefficiencies in backend workflows.

---

### **Additional Tips for Speed Optimization**

- **Minimize Workflows on Page Load**: Reduce initial workflows and conditionally load elements.
- **Optimize Repeating Groups**: Use pagination instead of loading large datasets at once.
- **Lazy Load Images**: Utilize plugins to load images only when needed.
- **Check for Large Fonts and Files**: Use Chrome’s "Network" tab to spot unnecessary asset downloads.

These tools and strategies will help you systematically monitor and improve your Bubble app’s speed. If needed, I can guide you further based on a specific issue you encounter—feel free to share screenshots of your setup!