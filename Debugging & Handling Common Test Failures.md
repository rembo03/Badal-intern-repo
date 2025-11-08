# Debugging & Handling Common Test Failures

## 🎯 Goal
Learn how to debug failing E2E (End-to-End) tests, handle flaky tests, and improve overall test stability.

---

## ✅ Why is this Important?
E2E tests can fail for many unpredictable reasons such as slow loading screens, dynamic elements, or WebView delays.  
Learning how to debug these effectively helps make automated testing **more reliable, faster to fix, and easier to maintain**.

---

## ✅ Tasks & Answers

### 1. Research: Common Reasons for E2E Test Failures
**Common causes include:**
- **Timing issues:** Elements take longer to appear or load.
- **Dynamic UI changes:** Element IDs or positions change between runs.
- **Incorrect locators:** Outdated or non-unique element selectors.
- **Network instability:** Slow API or backend responses.
- **Pop-ups or overlays:** Unexpected modals blocking UI interaction.
- **Test data problems:** Missing or inconsistent test data between runs.

---

### 2. Debugging: How to Determine if a Test is Flaky
A test is **flaky** when:
- It **passes sometimes and fails other times** without any code change.
- The **failure reason changes** between runs (e.g., timeout once, missing element next time).
- It works locally but **fails in CI pipelines** due to environment differences.
- Logs show **inconsistent timing** or **random errors**.

🧠 **Example:**  
If a test that clicks a button sometimes fails with “element not interactable,” it’s likely flaky due to timing or state issues.

---

### 3. Fixing: Strategies to Improve Test Reliability
**To stabilize flaky tests:**
- ✅ Use **explicit waits** (`WebDriverWait`) instead of `time.sleep()`.
- ✅ Implement **retry logic** for actions that may fail due to slow UI.
- ✅ Ensure **clean test environments** — clear cache or reset state before tests.
- ✅ Make locators **unique and consistent**.
- ✅ Use **Page Object Model (POM)** to separate logic and UI elements.
- ✅ Add **assertions** only after confirming elements are visible.

🧩 **Example Python Snippet:**
```python
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Wait for element
element = WebDriverWait(driver, 10).until(
    EC.visibility_of_element_located((By.ID, "loginButton"))
)
element.click()
