Here’s a glossary of common terms related to Artillery.io, the modern, powerful load testing toolkit. This glossary can help you understand the key concepts and terminology used in Artillery testing.

### Artillery.io Glossary

1. **Artillery**: An open-source load testing tool designed for testing and benchmarking web applications, APIs, and microservices.

2. **Load Testing**: The process of simulating multiple users or transactions to evaluate how an application behaves under expected load conditions.

3. **YAML**: A human-readable data serialization format used for configuration files in Artillery, allowing users to define scenarios, settings, and test parameters.

4. **Scenario**: A defined sequence of actions that simulate user behavior, including requests to an application, which can be configured in the Artillery YAML file.

5. **Vuser**: A virtual user simulated by Artillery, performing actions according to defined scenarios. The number of virtual users can be scaled up or down during tests.

6. **Throughput**: The number of requests processed by the application in a given time frame, typically measured in requests per second (RPS).

7. **Response Time**: The total time taken by the server to process a request and send back a response, an important metric for assessing performance.

8. **Error Rate**: The percentage of failed requests compared to total requests during a load test. A high error rate may indicate issues with the application.

9. **HTTP(s)**: Hypertext Transfer Protocol (Secure) used for transferring data on the web, commonly tested with Artillery.

10. **Hooks**: Functions that allow users to run custom logic before or after certain actions in the test, providing flexibility for scenarios and data manipulation.

11. **Statistics**: Metrics collected during a test run, such as response times, throughput, and error rates, which are reported at the end of the test.

12. **Ramp-Up**: The gradual increase in the number of virtual users over time during a test, allowing the application to adjust to growing load levels.

13. **Duration**: The total time for which a load test is run, defined in the Artillery configuration. 

14. **Targets**: The endpoints or URLs that the test will send requests to, specified in the scenario configuration.

15. **Phases**: Defined periods in a load test that specify different configurations, such as ramping up users or maintaining a constant load.

16. **Configuration File**: The YAML file that defines all aspects of the test, including scenarios, settings, and reporting options.

17. **Result Reporting**: The process of outputting collected metrics and statistics after a test run, which can be displayed in various formats (e.g., console, JSON, HTML).

18. **JSON Output**: A format for reporting test results that allows for easy integration with other tools and services for analysis.

19. **Custom Metrics**: User-defined metrics that can be captured and reported during a test, allowing for more granular performance analysis.

20. **Test Data**: Input data used during tests, which can be static or dynamic, often parameterized to simulate realistic user behavior.

21. **Stress Testing**: A type of testing focused on evaluating how an application behaves under extreme conditions, often beyond its specified limits.

22. **Distributed Testing**: Running Artillery tests across multiple machines to simulate a larger load and gather performance data from various sources.

23. **Latency**: The delay between sending a request and receiving a response, an important factor in assessing application performance.

24. **Timeout**: A defined period that specifies how long to wait for a response before considering a request as failed.

25. **WebSocket Testing**: The ability to test WebSocket connections in addition to standard HTTP requests, useful for real-time applications.

---
### [Back to README](./README.md)