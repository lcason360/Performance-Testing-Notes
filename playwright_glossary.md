Here’s a glossary of common terms related to Playwright, the open-source automation library for testing web applications. This glossary can help you navigate Playwright's concepts and terminology more effectively.

### Playwright Glossary

1. **Playwright**: An open-source automation library for browser testing that allows developers to write tests for web applications across multiple browsers.

2. **Browser Context**: A new instance of a browser that allows tests to run in isolation, simulating different sessions, cookies, and storage for each context.

3. **Page**: Represents a single tab or page within a browser context, where you can interact with elements, navigate, and perform actions.

4. **Element Handle**: A reference to a DOM element that allows you to interact with it (e.g., click, type) in your tests.

5. **Locator**: An API that enables you to find elements in the page based on various selectors, such as CSS selectors or XPath.

6. **Test Runner**: The tool that executes your tests. Playwright comes with its own test runner, but it can also be integrated with other frameworks like Jest or Mocha.

7. **Action**: Any operation performed in the browser, such as clicking a button, filling a form, or navigating to a new page.

8. **Assertion**: A statement that checks whether a certain condition is true, commonly used in tests to validate expected outcomes.

9. **Selector**: A method to identify elements on a webpage. Playwright supports multiple selector strategies, including CSS selectors and text selectors.

10. **Network Interception**: The ability to capture and modify network requests and responses made by the application during tests, useful for simulating different scenarios.

11. **Screenshot**: A capture of the visual representation of a page or element, often used for visual regression testing or debugging.

12. **Video Recording**: The ability to record video of the test execution, providing a visual representation of what happened during the test.

13. **Headless Mode**: A way to run the browser without a graphical user interface, often used for faster execution in CI/CD environments.

14. **Test Fixtures**: Predefined setup and teardown logic for tests, allowing you to establish the context, such as opening a browser or navigating to a URL.

15. **API Testing**: Using Playwright to send HTTP requests directly to an application’s API, allowing you to test backend functionality alongside UI interactions.

16. **Waits**: Mechanisms to pause test execution until certain conditions are met, such as waiting for an element to be visible or for a network request to complete.

17. **Timeout**: A predefined period during which an operation is expected to complete before failing, helping to manage test execution duration.

18. **Debugging**: The process of identifying and fixing issues in your tests, which Playwright supports through interactive modes and debugging tools.

19. **Custom Locators**: User-defined methods for locating elements that allow for complex selection criteria beyond standard selectors.

20. **Cross-Browser Testing**: The practice of testing web applications in multiple browsers (Chrome, Firefox, Safari, etc.) to ensure compatibility and consistent behavior.

21. **Page Object Model (POM)**: A design pattern for organizing test code by encapsulating page-related interactions within classes, improving maintainability and readability.

22. **Trace**: A record of actions taken during a test run, including network requests, console logs, and screenshots, used for debugging and analysis.

23. **Concurrency**: The ability to run multiple tests in parallel, speeding up test execution and improving efficiency in large test suites.

24. **Assertions Library**: A collection of functions for verifying conditions in tests, often integrated with Playwright's test runner for ease of use.

25. **Headful Mode**: A way to run the browser with a graphical user interface, useful for manual debugging and visual confirmation of test actions.


---
### [Back to README](./README.md)