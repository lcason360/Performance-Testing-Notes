# Combining Artillery and Playwright for a UI Load Test
## **Source of Info: ChatGPT**

Combining Artillery.io and Playwright can provide a powerful solution for performing load tests on the UI of your web application. Artillery can handle load generation and simulate multiple users, while Playwright can simulate real user interactions in the browser.

Here’s a step-by-step guide on how to set this up:

### Step 1: Set Up Your Environment

1. **Install Artillery and Playwright**:

   ```bash
   npm install -g artillery
   npm install playwright
   ```

2. **Create a New Project Directory** and navigate to it:

   ```bash
   mkdir artillery-playwright-load-test
   cd artillery-playwright-load-test
   ```

3. **Initialize a New Node.js Project**:

   ```bash
   npm init -y
   ```

4. **Install Playwright Locally**:

   ```bash
   npm install playwright
   ```

### Step 2: Create Your Playwright Script

Create a Playwright script that simulates user interactions with your application. Save this as `playwright-test.js`:

```javascript
const { chromium } = require('playwright');

async function runUserFlow(url) {
    const browser = await chromium.launch({ headless: true });
    const context = await browser.newContext();
    const page = await context.newPage();

    // Navigate to your URL
    await page.goto(url);

    // Simulate user interactions
    await page.click('selector-for-some-button'); // Adjust selector
    await page.fill('selector-for-input', 'test input'); // Adjust selector
    await page.click('selector-for-submit'); // Adjust selector

    // Optionally wait for some response or element to ensure interaction is complete
    await page.waitForTimeout(1000); // Adjust as necessary

    await browser.close();
}

module.exports = runUserFlow;
```

### Step 3: Create Your Artillery Configuration

Create an Artillery configuration file, `load-test.yml`, to define how to generate load:

```yaml
config:
  target: 'http://localhost:3000' # Change to your app's URL
  phases:
    - duration: 60
      arrivalRate: 5
scenarios:
  - flow:
      - function: 'runUserFlow'  # This will call the Playwright function
```

### Step 4: Create a Wrapper Script to Run Artillery with Playwright

Create a wrapper script, `run-test.js`, to run Artillery and invoke the Playwright script:

```javascript
const artillery = require('artillery');
const runUserFlow = require('./playwright-test');

async function loadTest() {
    const artilleryConfig = {
        config: {
            target: 'http://localhost:3000', // Your target URL
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
                            await runUserFlow('http://localhost:3000'); // Your app's URL
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

### Step 5: Run Your Test

1. **Start Your Application**: Make sure your web application is running.
2. **Run the Load Test**:

   ```bash
   node run-test.js
   ```

### Considerations

- **Browser Resource Usage**: Running multiple Playwright instances can be resource-intensive. Monitor the machine where you're running the tests.
- **Adjust Load Parameters**: Modify the `duration` and `arrivalRate` in the Artillery config to simulate different load scenarios.
- **Error Handling**: Implement error handling in your Playwright script to manage any unexpected issues during testing.
- **Headless Mode**: The Playwright script is set to run in headless mode. You can change it to `false` for debugging purposes.

---
### [Back to README](./README.md)