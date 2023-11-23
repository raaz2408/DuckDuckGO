**Assessment**

*  Using Apache JMeter with your choice of language and framework, write a performance test script to Complete the following 3 transactions:

1.  Load DuckDuckGo Homepage (https://duckduckgo.com/)
2.  Type Suggested Search Term
3.  Select Search Term from the suggested Search Box.

**Transactions have been enclosed in the script.**

*  The script should iterate all three transactions and cycle through the following search teams picking a different one on each iteration.

**This capability has been activated through the utilization of the CSV Data Set Config element, which retrieves P_SearchTermParameter values from a file (SearchParameterFile.csv) located in the bin folder OR**
**Also, this has been enabled by using user parameters**

*  The test needs run for 5 minutes and should achieve 30 iterations per minute

**The configuration details are as follows:**

**1. First Method:**
Implemented a Constant Throughput Controller to specify the target throughput. Given the presence of 3 transactions, a throughput of 10 per minute has been assigned to each transaction, aligning with the 10 virtual users.

**2.  Second Method:**
Incorporated a Constant Throughput Controller into a Concurrency Thread Group consisting of 10 virtual users, a ramp-up period of 10, and a target rate duration of 5 minutes. This allows us to set and maintain the desired target throughput. Considering the presence of 3 transactions, I have set the throughput to 10 per minute.

**3.  Third Method:**
Number of Vusers: 10
Ramp up period : 30s ( 1 user ramps up every 3s)
Pacing time : 20s (using Flow Control Action Sampler)
Duration: 5 minutes + 30s (ramp up) => 330 seconds

*  Each user should be treated as a new user and caching should be handled appropriately

**1.Same user on each iteration has been disabled. 
  2.To handle Cache, HTTP Cache Manager has been added**

*  Please be aware that your script should report times for the different elements of the search process (homepage, suggested search, search)
**Transaction controllers have been incorporated to individually capture the response times of each mentioned transaction.**


**Additional Questions:**

**Question:**

**You are given a requirement which states “The system should scale to 2000 users”. What other questions would you need to ask to get enough information to create a workload model**

**Answer:**

**1. Concurrency Profile:**
What is the expected distribution of users over time? Are they expected to ramp up gradually or hit the system simultaneously?

**2.  User Scenarios:**
Can you provide specific user scenarios or use cases that are representative of typical user behavior?

**3.  User Types:**
Are there different types of users (e.g., anonymous users, registered users, administrators), and how should their behavior differ?

**4.  Data Volume and Complexity:**
What is the expected volume and complexity of data interactions during user sessions?

**5.  Geographical Considerations:**
Should the workload model account for users from different geographical locations?

**6.  Think Times and Pacing:**
Can you provide information on typical think times between user actions and the desired pacing?

**7.  Peak Load Scenarios:**
Are there specific events or scenarios that could cause a sudden spike in user activity?

**8.  Scalability Goals:**
Are there specific performance goals for key scalability metrics (e.g., response time, throughput) under various load levels?

**Question:**

**Please rewrite the requirement above so that it testable and more descriptive**

**Answer:**

The system should gracefully handle a scalable load of 2000 concurrent users within a specified response time threshold, while maintaining acceptable system performance metrics such as throughput and resource utilization.

**Question:**

**As well as creating a script in a tool to do the performance testing, what other factors would need to be considered for a performance testing engagement?**

**Answer:**

**Test Environment Stability:**
Ensure that the test environment is stable and representative of the production environment.

**Test Data Management:**
Consider the strategy for managing test data, ensuring data consistency and relevance throughout the test.

**Monitoring and Metrics:**
Establish a robust monitoring strategy to capture key performance metrics and diagnose issues during testing.

**Infrastructure Capacity:**
Validate that the testing infrastructure (servers, networks, databases) can handle the expected load without bottlenecks.

**Test Iterations and Analysis:**
Plan for multiple test iterations to refine the test scenarios based on initial results and analysis.

**Scalability Testing:**
Conduct scalability testing beyond the specified user count to identify system limits and performance degradation patterns.

**Failure and Recovery Scenarios:**
Test how the system handles failure scenarios and recovers under stress, ensuring robustness and resilience.

**Client-Side Considerations:**
Consider the impact of different client devices, browsers, and network conditions on performance.

**Security Testing Integration:**
Integrate security testing into performance testing to identify potential vulnerabilities under load.

**User Experience Validation:**
Validate not just technical performance metrics but also the end-user experience under realistic conditions.

**Reporting and Communication:**
Establish clear reporting mechanisms and communication channels to convey test results, identify bottlenecks, and propose improvements.
