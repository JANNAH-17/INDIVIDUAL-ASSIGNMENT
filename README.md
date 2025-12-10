# INDIVIDUAL-ASSIGNMENT
<div align="center">
<h1 style="font-size:40px; font-weight:bold;">🧬 WEB PERFORMANCE TESTING 🧬</h1>
</div>

**Name:** NURJANNAH NADHIRAH BINTI YAZIB  
**Student ID:** 2022209102  
**Group:** NBCS2555A
**Course Code:** ITT440 - Network Programming  
**Tool Used:** Apache JMeter  
**Testing Type:** SPIKE TEST , LOAD TEST, STRESS TEST 
**Target Website:** jmeter-plugins.org
 


## 😵‍💫 What is Spike Test?
A Spike Test is a type of performance test used to evaluate how a system behaves when it experiences a sudden, extreme increase in load within a very short period of time.
In JMeter, this involves generating a sharp and rapid rise in the number of virtual users (VUs) to observe the system’s stability, ability to recover, and overall performance under stress. 

## 🧰 Propose
The main purpose of a spike test is to understand how well the system responds to unexpected load surges. It helps to determine how quickly the system recovers after the load returns to normal


## ⚙️ Test Configuration And Methadology (SPIKE TEST)
<p align="center">
  <img src="./about.png" width="600">
</p>

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

(image spike test)
---

## ✍🏿 Sample Raw Data

(raw data)

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

---

## 👩‍💻 Demonstration Video
