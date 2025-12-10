# INDIVIDUAL-ASSIGNMENT
<div align="center">
<h1 style="font-size:40px; font-weight:bold;">🧬 WEB PERFORMANCE TESTING 🧬</h1>
</div>

**Name:** NURJANNAH NADHIRAH BINTI YAZIB  
**Student ID:** 2022209102  
**Group:** NBCS2555A
**Course Code:** ITT440 - Network Programming  
**Tool Used:** Apache JMeter  
**Testing Type:** Spike test, Load Test, Stress test
**Target Website:** jmeter-plugins.org
 
## 😵‍💫1.  What is Spike Test?
A Spike Test is a type of performance test used to evaluate how a system behaves when it experiences a sudden, extreme increase in load within a very short period of time.
In JMeter, this involves generating a sharp and rapid rise in the number of virtual users (VUs) to observe the system’s stability, ability to recover, and overall performance under stress. 

## 🧰 Propose
The main purpose of a spike test is to understand how well the system responds to unexpected load surges. It helps to determine how quickly the system recovers after the load returns to normal


## ⚙️ Test Configuration (SPIKE TEST)
<div align="center">

| **Starts Thread Count** | **Initial Delay (Sec)** | **Startup Time (Sec)** | **Hold Load For (Sec)** | **Shutdown Time (Sec)** |
|--------------------------|--------------------------|---------------------------|---------------------------|---------------------------|
| 150                      | 0                        | 1350                      | 2400                      | 600                       |
| 25                       | 1950                     | 225                       | 1575                      | 600                       |
| 25                       | 2775                     | 225                       | 750                       | 600                       |

</div>

---

## 🧩 Test Plan Setup

| Step | Description |
|------|-------------|
| 1    | Launch Apache JMeter and create a new test plan. |
| 2    | Add a **Thread Group** and configure based users based on the thread table above. |
| 3    | Add **HTTP Request Sampler** targeting `JMeter Plugins :: JMeter-Plugins.org`. |
| 4    | Add **Listeners** (Summary Report, View Result Tree). |
| 5    | Save and execute the test plan. |
| 6    | Observe response times, throughput, and error rates during the spike. |
| 7    | Export reports and analyze results. |

![Spike test setup](https://github.com/JANNAH-17/INDIVIDUAL-ASSIGNMENT/blob/main/Spike%20setup.png?raw=true)
---
## ✍🏿 Sample Raw Data

![Raw data](https://github.com/JANNAH-17/INDIVIDUAL-ASSIGNMENT/blob/main/Result%20Raw%20Data.png?raw=true)
## Explanation 
📈Row 1 – 150 Users
•	Initial delay: Starts immediately at 0 seconds.
•	Startup time: Ramps up gradually from 0 to 150 users over 1350 seconds (22 min 30 sec).
•	Hold time: Holds full 150 users for 2400 seconds (~40 minutes).
•	Shutdown: Ends after 600 seconds of graceful shutdown.
Purpose: This creates a large, stable baseline load to measure average system performance.

📈Row 2– 25 Users 
•	Initial delay: Begins at 1950 seconds (32 min 30 sec).
•	Startup time: Ramps up from 0 → 25 users in 225 seconds.
•	Hold time: Holds these 25 users until 3750 seconds, syncing with Row 1.
•	Shutdown: Ends together with Row 1 after 600 seconds.
Purpose: Simulates an increase of traffic mid-test, used to test server elasticity and scaling behavior.

📈Row 3 - 25 Users 
•	Initial delay: Begins at 2775 seconds (46 min 15 sec).
•	Startup time: Ramps up in 225 seconds (finishes at exactly 50 minutes).
•	Hold time: Lasts until 3750 seconds, matching previous rows.
•	Shutdown: Ends simultaneously with all other rows.
Purpose: Introduces a final peak load stage to push the system to its maximum capacity (200 users).

---

## 📝 Results Summary

| **Response Time Behavior** | Response times increased significantly during the first spike (up to 150 users) |
| **Throughput** | The highest throughput was observed during the 150 + 25 user spike layer|
| **Recovery Behavior** | After the spike load reduced to 0 users, the system recovered without manual restart, indicating good resilience|

---

##  🧠  Recommendations for improvement
1. Optimize server scalability for sudden load increases
  > Implement auto-scaling (horizontal scaling) if the application is cloud-hosted.
  > Review CPU and memory utilization during spikes to identify hardware bottlenecks

2. Reduce errors during peak loads
  > Increase server thread pools or connection pools.
  > Validate timeouts and retry logic in the backend to prevent cascading failures

---

## 🧠 **Conclusion**

The spike test demonstrated that the system is generally capable of handling sudden and extreme increases in user load. It confirms that the system can withstand unexpected traffic surges, but improvements in scalability, backend performance, and error handling would further enhance its stability and responsiveness during real-world peak events.
===================================================================================================================================================================================================================
## 😵‍💫 2. What is Load Test?
To determine an application behaviour when a large number of users access the application. Load testing is to check how much load a system can handle and helps to identify the maximum operation capacity of any application. 

## 🧩 Test Plan Setup
| Step | Description |
|------|-------------|
| 1    | Apache JMeter was opened and a new Test Plan was created and renamed to “LOAD  TEST.” This Test Plan acted as the main container for all testing components. |
| 2    | A Thread Group was added to simulate multiple users accessing the website.|
| 3    | Add HTTP Header Manager - This allowed the requests to appear as if they were coming from a real web browser.This setup directed JMeter to send GET requests to the Wikipedia homepage|
| 4    | Add **Listeners** (Summary Report, View Result Tree). |
| 5    | Add View Result Tree - It displayed detailed information such as response code, response time, and HTML data returned from the server.|
| 6    | Add Summary Report – to provide overall performance data including average, minimum, and maximum response time, throughput, and error percentage |
| 7    | Start Test - The test was executed by clicking the green “Start” button on the JMeter toolbar. The listeners were used to monitor real-time results and verify that all requests were completed successfully.|
|8     | Capture Result - After execution, data from the Summary Report was analyzed to evaluate website performance, response stability, and throughput under simulated load conditions. Example Configuration to execute data into excel file ![Configuration](https://github.com/JANNAH-17/INDIVIDUAL-ASSIGNMENT/blob/main/Configuration.jpg?raw=true) |
|9     | Result shows in Excel ‘Loading.Test.csv’                                                                                                                                                                           ![Result.csv](https://github.com/JANNAH-17/INDIVIDUAL-ASSIGNMENT/blob/main/Result.load.png?raw=true)|

## **Result Summary**
| **Label**           | **# Samples** | **Average (ms)** | **Min (ms)** | **Max (ms)** | **Std. Dev (ms)** | **Error %** | **Throughput** | **Received KB/sec** | **Sent KB/sec** | **Avg Bytes** |
|----------------------|---------------|------------------|--------------|--------------|--------------------|-------------|------------------|-----------------------|------------------|----------------|
| **jmeter-search**    | 100           | 361              | 255          | 1017         | 180.12             | 0.00%       | 8.4/sec          | 134.77               | 1.13             | 164538         |
| **jmeter-document**  | 100           | 335              | 271          | 597          | 65.13              | 0.00%       | 8.8/sec          | 155.53               | 1.13             | 180107         |
| **jmeter-start**     | 100           | 316              | 260          | 1448         | 129.30             | 0.00%       | 8.1/sec          | 192.77               | 1.07             | 228123         |
| **TOTAL**            | 300           | 337              | 255          | 1448         | 131.90             | 0.00%       | 23.4/sec         | 435.66               | 3.02             | 105057         |

## Overall Test Result 

1.	Performance was stable, with an overall average response time of 337 ms, which is considered fast and within acceptable performance thresholds for most web applications.
2.	Zero errors (0.00%) indicate that the system handled the entire load test without failing any requests.
3.	Throughput reached 23.4 requests/sec, demonstrating the system’s ability to handle moderate traffic loads effectively

## Recommendation 
| **Category**                | **Observed Issue**                                           | **Recommendation**                                              | **Expected Improvement**                         |
|-----------------------------|--------------------------------------------------------------|------------------------------------------------------------------|--------------------------------------------------|
| **Scalability / Load Handling** | Throughput low at 2.40 req/sec even with high user load      | Implement load balancing, horizontal scaling, use CDN           | Higher throughput and better handling of peak loads |
| **JMeter Test Plan**        | Sudden user spikes from Ultimate Thread Group                | Use smoother ramp-up, run test in non-GUI mode, disable heavy listeners | More accurate and stable load simulation |

## Conclusion
The test results demonstrate that the system performs reliably under the given load profile. All endpoints maintained response times under 1.5 seconds, with zero errors, and achieved a healthy aggregate throughput of 23.4 requests per second. Bandwidth usage remained within reasonable levels. These metrics indicate that the system can sustain peak operational conditions without degradation or instability.
===================================================================================================================================================================================================================
## 😵‍💫 3. What is Stress Test?
Stress test is the process of gradually increasing user load beyond expected limits to evaluate how a system performs under peak or excessive pressure. It helps identify the maximum capacity the application can handle before performance degrades or failures occur

## 🧰 Propose
Stress test is to test the system behaviour, to push the system beyond its normal operation and it is to determine the system stability.

## ⚙️ Stress Test Thread Group Setup
 ![stress test setup](https://github.com/JANNAH-17/INDIVIDUAL-ASSIGNMENT/blob/main/Setup%20stress%20test.png?raw=true)

 ## Result for Response time graph
 ![Result](https://github.com/JANNAH-17/INDIVIDUAL-ASSIGNMENT/blob/main/Result%20response%20time.png?raw=true)

 ## Result for View in table 
 ![Result](https://github.com/JANNAH-17/INDIVIDUAL-ASSIGNMENT/blob/main/Result%20in%20table(stress).png?raw=true)

 ## 🧠Recommendation – On Performance Improvement

 | **Category**          | **Identified Issue**                               | **Recommendation**                                              | **Expected Impact**                                      |
|------------------------|----------------------------------------------------|------------------------------------------------------------------|-----------------------------------------------------------|
| **JMeter Test Plan**   | GUI listeners slow down JMeter execution           | Disable heavy listeners (Results Tree/Table), use Non-GUI mode  | More accurate and higher-performance load testing         |
| **Sample Size**        | Only 100 samples (not enough for stable conclusion)| Increase to 500–2000 samples                                     | More reliable and statistically valid results             |
| **Network Configuration** | Potential network handshake overhead              | Enable HTTP Keep-Alive                                           | Reduces connection overhead and improves throughput       |

## Conclusion
The summary report shows that 100 HTTP requests were executed successfully with no errors (0%), indicating a stable server during the test run. The average response time was 984 ms, which is within acceptable limits for general web applications but shows room for improvement due to a high maximum response time of 3.49 seconds. The standard deviation of 398 ms indicates performance inconsistency, suggesting the server may have occasional processing delays or resource spikes.
The throughput of 2.49 requests per second reflects the test design and server response time. With each response averaging 117 KB, the network throughput of 286 KB/sec indicates a moderate data load handled efficiently by the server.
Overall, the system is functionally stable with no failures, but optimization may be needed to reduce high response-time variance and improve consistency under load.


## 👩‍💻 Demonstration Video

