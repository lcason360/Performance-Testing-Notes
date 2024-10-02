# Single Login for Multiple Tests via capturing cookies
## **Source of Info: ChatGPT**

To perform a single login and run multiple tests using Artillery and Playwright while maintaining the session, you can modify your setup to store the session cookies after logging in. This way, you won’t have to log in repeatedly during the load test.

### Step-by-Step Guide

1. **Log In Once and Capture Cookies**: Modify your Playwright script to log in once, capture the session cookies, and store them.

2. **Use the Captured Cookies for Subsequent Requests**: When running your load tests, use the stored cookies to authenticate without logging in again.

### Example Implementation

#### Step 1: Modify the Playwright Script

Update your Playwright script (`playwright-test.js`) to log in once and store the session cookies:

```javascript
const { chromium } = require('playwright');

let sessionCookies = null;

async function loginAndGetCookies(url) {
    const browser = await chromium.launch({ headless: true });
    const context = await browser.newContext();
    const page = await context.newPage();

    // Navigate to your login page
    await page.goto(url);

    // Perform login
    await page.fill('selector-for-username', 'your-username'); // Adjust selector
    await page.fill('selector-for-password', 'your-password'); // Adjust selector
    await page.click('selector-for-login'); // Adjust selector

    // Wait for navigation or element to ensure login is complete
    await page.waitForNavigation();

    // Capture cookies after logging in
    sessionCookies = await context.cookies();

    // Close the browser
    await browser.close();
}

async function runUserFlow(url) {
    const browser = await chromium.launch({ headless: true });
    const context = await browser.newContext();

    // Set cookies to the new context
    await context.addCookies(sessionCookies);
    const page = await context.newPage();

    // Simulate user interactions
    await page.goto(url); // Your target URL
    await page.click('selector-for-some-button'); // Adjust selector
    await page.fill('selector-for-input', 'test input'); // Adjust selector
    await page.click('selector-for-submit'); // Adjust selector

    await page.waitForTimeout(1000); // Adjust wait time if needed

    await browser.close();
}

// Expose functions
module.exports = { loginAndGetCookies, runUserFlow };
```

#### Step 2: Update the Load Test Script

Update your load test script (`run-test.js`) to perform the login once and reuse the session cookies:

```javascript
const artillery = require('artillery');
const { loginAndGetCookies, runUserFlow } = require('./playwright-test');

async function loadTest() {
    const url = 'http://localhost:3000'; // Your app's URL

    // Log in once and capture cookies
    await loginAndGetCookies(url);

    const artilleryConfig = {
        config: {
            target: url,
            phases: [
                {
                    duration: 60,
                    arrivalRate: 5,
                },
            ],
        },
        scenarios: [
            {
                flow: [
                    {
                        function: async () => {
                            await runUserFlow(url); // Reuse the same URL
                        },
                    },
                ],
            },
        ],
    };

    await artillery.run(artilleryConfig);
}

loadTest()
    .then(() => console.log('Load test completed.'))
    .catch(err => console.error(err));
```

### Step 3: Run Your Test

1. **Start Your Application**: Make sure your web application is running.
2. **Run the Load Test**:

   ```bash
   node run-test.js
   ```

### Explanation

- **Login Once**: The `loginAndGetCookies` function logs in to your application once and captures the session cookies.
- **Reuse Cookies**: The `runUserFlow` function uses the captured cookies to authenticate subsequent requests without needing to log in again.
- **Load Testing**: The Artillery configuration runs the user flow multiple times, simulating load while maintaining the session.

### Considerations

- **Session Expiry**: Ensure that your session does not expire during the load test. You may need to adjust the duration of the test or session management in your application.
- **Error Handling**: Consider adding error handling in your Playwright functions for robustness.
- **Monitoring**: Monitor the performance of your application during the load test to analyze results effectively.

This setup allows you to efficiently perform load testing while maintaining a single authenticated session, simulating a more realistic user experience.