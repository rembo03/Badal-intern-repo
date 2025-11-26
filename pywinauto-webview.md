# Automating WebViews inside a Windows app (pywinauto + Selenium + WebView2)

This note explains how to detect WebView host components, attach Selenium to an embedded WebView2 via the DevTools endpoint, and keep pywinauto for native host automation. It includes practical tips and a short workflow you can adapt for Focus Bear.

## Quick contract
- Inputs: running Windows app with an embedded WebView2 (Focus Bear). Optional: ability to start the app with WebView2 remote debugging enabled.
- Outputs: pywinauto controls native host window; Selenium attached to WebView DOM via DevTools allows DOM interactions, clicks, and text extraction.
- Error modes: DevTools port not available, permission/access denied to user data folder, wrong driver version, timing/race conditions.

## 1) Detect WebView host components

- Use Microsoft Inspect (Inspect.exe, part of Windows SDK) to explore the UI Automation tree.
  - Look for panes or controls near the visible area that map to the embedded browser. Common clues:
    - Control type: Pane / Custom
    - Class names: `Chrome_WidgetWin_1`, `Windows.UI.Core.CoreWindow`, or vendor-specific host names
    - Automation properties: localized names or help text mentioning "WebView", "web", or "browser"
- In pywinauto, prefer the `uia` backend for modern apps: Desktop(backend='uia').window(title_re=...)
- Example (pywinauto interactive):

  - Open Inspect.exe, hover over the WebView content, and note the AutomationId, ClassName and ControlType.

## 2) Difference between native Windows UI testing and WebView testing

- Native UI (pywinauto / UIA): interacts with the host window, menus, controls exposed through UI Automation, and can perform OS-level input (click_input).
- WebView (Selenium + DevTools): interacts with the in-page DOM, JavaScript APIs, and browser features — useful when page logic and elements are not exposed to UIA.
- Together: pywinauto handles the host window (open windows, menu items, native dialogs). Selenium interacts with page content inside the WebView.

## 3) How to attach Selenium to WebView2 DevTools

Two common approaches:

- If the host app starts WebView2 with a remote debugging port (e.g. additional browser args `--remote-debugging-port=XXXX`), WebView2 will write a `DevToolsActivePort` file in the Edge/User Data profile folder. You can then read the port and attach ChromeDriver to `localhost:PORT`.
- If the host app does not expose remote debugging, you need to modify the host (developer change) to pass the extra argument when creating the WebView2 environment:

  - Example (C# snippet):

    ```csharp
    var options = new CoreWebView2EnvironmentOptions(additionalBrowserArguments: "--remote-debugging-port=9222");
    var env = await CoreWebView2Environment.CreateAsync(null, userDataFolder, options);
    await webView.EnsureCoreWebView2Async(env);
    ```

  - With this, WebView2 will listen for DevTools connections at the specified port and write `DevToolsActivePort` into the profile folder.

### How the repo helper works

- The helper in `utils/webview_port.py` searches common Edge/User Data locations for a `DevToolsActivePort` file and reads a port value. This is what `tests/test_webview.py` uses to attach.

## 4) Running Selenium attached to the port

- Create ChromeOptions and set the experimental option `debuggerAddress` to `localhost:PORT`. Then start ChromeDriver with those options — you don't start a fresh browser; ChromeDriver attaches to the existing debug-enabled browser instance.

Example (Python):

- In `tests/test_webview.py` we use:

```py
options = webdriver.ChromeOptions()
options.add_experimental_option("debuggerAddress", f"localhost:{port}")
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=options)
```

Then use normal Selenium calls to find and click DOM elements.

## 5) How Pywinauto and Selenium work together

- Use pywinauto to find and manipulate native elements (menus, window sizing, opening dialogs that are native to the host).
- Use Selenium to operate the web page inside the WebView (DOM queries, JS, network interception via DevTools, etc.).
- Typical test flow:
  1. Start/attach to the host process with pywinauto and make sure the WebView is visible and loaded.
  2. Use `utils/webview_port.get_webview_port()` to find the DevTools port.
  3. Attach Selenium to the DevTools endpoint and interact with the DOM.
  4. Optionally use pywinauto to interact with native UI after DOM actions (e.g., native dialogs triggered by the page).

## 6) Common challenges and mitigations

- DevToolsActivePort missing
  - Cause: WebView2 was not started with `--remote-debugging-port`.
  - Fix: Start the host with additional browser arguments (developer change) or instruct the app to enable remote debugging.

- Port discovery ambiguities
  - Multiple profiles or multiple WebView2 instances can create several `DevToolsActivePort` files. Read the content and verify which one maps to your target (process id, timestamp, etc.).

- Driver-binary mismatch
  - Ensure ChromeDriver version is compatible with the browser engine used by WebView2 (WebView2 uses Edge Chromium). Use webdriver-manager or pin an appropriate driver.

- Timing / race conditions
  - WebView may take time to create its browser process and write the port file. Use polling and reasonable timeouts before giving up.

- Input & focus issues
  - Synthetic clicks from Selenium are inside the browser; some native overlays or transparent windows may intercept input. Use `pywinauto`'s `click_input()` when native-level input is required, and ensure the WebView has focus.

- Security / permissions
  - Reading user data folders may require correct user context. Run tests under the same user account as the app.

## 7) Example test pattern

- The repository contains `tests/test_webview.py` with an example flow:
  - `attach_native_host()` — attach to the host via pywinauto (Windows only) and optionally click a native button
  - `connect_webview()` — locate `DevToolsActivePort` via `utils/webview_port.py` and attach Selenium
  - `example_end_to_end()` — click a button inside the WebView DOM and print sample text

## 8) Next steps / troubleshooting checklist

1. If you cannot find a `DevToolsActivePort` file: confirm the host is starting WebView2 with `--remote-debugging-port`.
2. Use Inspect.exe to confirm the control tree and collect a reliable selector/property that pywinauto can use.
3. Confirm that ChromeDriver matches the WebView engine version.
4. Use logging, and add sleeps/polls at host startup to handle timing.

---
If you want, I can:
- Add a small Windows-only helper that launches Focus Bear with a temporary user data dir and a known remote debugging port (useful for CI or local debugging).
- Add unit tests/more robust port discovery that matches process ids.

Happy to implement the next item you prefer.
