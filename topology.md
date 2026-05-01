# 🗺️ Topology Analysis & Control Plane Verification

This document provides a detailed breakdown of the enterprise topology, the protocol interaction logic, and the evidence used to verify the "RIB Judge" theory.

## 📍 Network Domains
The lab is divided into several specialized routing domains to simulate a diverse enterprise environment:

### **1. OSPF Backbone (Blue Zone)**
![OSPF topology](./Topology-Snapshots/OSPF/topology.png)
* **Role:** Acts as the primary transit backbone for the core.
* **Area Design:** Features Area 0.
* **Key Routers:** **[R1](./Configurations/OSPF/R1.txt)** , **[R2](./Configurations/OSPF/R2.txt)** ,  **[R8](./Configurations/OSPF/R8.txt)**
* **Configuration**
* **Router 1**
* ![Router 1](./Topology-Snapshots/OSPF/R1.png)
* **Router 2**
* ![Router 2](./Topology-Snapshots/OSPF/R2.png)
* **Router 8**
* ![Router 8](./Topology-Snapshots/OSPF/R8.png)
* **Routers Configurations**

 
### **2. EIGRP 96 (Orange Zone)**
![EIGRP-96 topology](./Topology-Snapshots/EIGRP-96/topology.png)
* **Role:** Highly controlled stub/specialized site.
* **Features:** Utilizes **Static Neighborships** to eliminate multicast overhead and **VLSM Summarization** to keep the routing table lean.
* **Key Routers:** **[R5](./Configurations/EIGRP-96/R5.txt)** , **[R12](./Configurations/EIGRP-96/R12.txt)** , **[R13](./Configurations/EIGRP-96/R13.txt)** , **[R14](./Configurations/EIGRP-96/R14.txt)** , **[R15](./Configurations/EIGRP-96/R15.txt)** , **[R16](./Configurations/EIGRP-96/R16.txt)** , **[HQ-Hub](./Configurations/EIGRP-96/HQ-HUB.txt)** , **[R10](./Configurations/EIGRP-96/R10.txt)** , **[R21](./Configurations/EIGRP-96/R21.txt)**.
* **Router 5**
  * ![Router 5](./Topology-Snapshots/EIGRP-96/R5.png)
  * **Router 5 EIGRP NEIGHBORS**
  * ![Router 5 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R5-EIGRP-neighbors.png)

* **Router 16**
  * ![Router 16](./Topology-Snapshots/EIGRP-96/R16.png)
  * **Router 16 EIGRP NEIGHBORS**
   * ![Router 15 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R16-EIGRP-neighbors.png)
  
* **Router 21**
  * ![Router 21](./Topology-Snapshots/EIGRP-96/R21.png)
  * **Router 21 EIGRP NEIGHBORS**
  * ![Router 21 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R21-EIGRP-neighbors.png)

* **Router 15**
  * ![Router 15](./Topology-Snapshots/EIGRP-96/R15.png)
  * **Router 15 Key Chain**
  * ![Router 15 Key Chain](./Topology-Snapshots/EIGRP-96/R15-key-chain.png)
  * **Router 15 Leak Map Result**
  * ![Router 15 Leak Map Result](./Topology-Snapshots/EIGRP-96/R15-leak-map-result.png)
  * **Router 15 EIGRP NEIGHBORS**
  * ![Router 15 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R15-EIGRP-neighbors.png)
 
* **Router 14**
  * ![Router 14](./Topology-Snapshots/EIGRP-96/R14.png)
  * **Router 14 EIGRP NEIGHBORS**
  * ![Router 14 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R14-EIGRP-neighbors.png)

* **Router 13**
  * ![Router 13](./Topology-Snapshots/EIGRP-96/R13.png)
  * **Router 13 EIGRP NEIGHBORS**
  * ![Router 13 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R13-EIGRP-neighbors.png)

* **Router 12**
  * ![Router 12](./Topology-Snapshots/EIGRP-96/R12.png)
  * **Router 12 EIGRP NEIGHBORS**
  * ![Router 12 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R12-EIGRP-neighbors.png)

* **Router 10**
  * ![Router 10](./Topology-Snapshots/EIGRP-96/R10.png)
  * **Router 10 EIGRP NEIGHBORS**
  * ![Router 10 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-96/R10-EIGRP-neighbors.png)

* **HQ-HUB**
  * ![HQ-HUB](./Topology-Snapshots/EIGRP-96/HQ-HUB.png)

### **3. EIGRP 1 (Pink Zones)**
![EIGRP-96 topology](./Topology-Snapshots/EIGRP-1/topology.png)
* **Role:** The primary redistribution domain and the site of the RIB conflict.
* **Features:** Implemented EIGRP Route filtering
* **Key Routers:**  **[R10](./Configurations/EIGRP-1/R10.txt)** , **[R11](./Configurations/EIGRP-1/R11.txt)**, **[R7,](./Configurations/EIGRP-1/R7.txt)** , **[R8](./Configurations/OSPF/R8.txt)** ,  **[R9](./Configurations/EIGRP-1/R9.txt)**.
* **NOTE:** IP route snapshots for all EIGRP 1 routers are available in the **[Config folder](./Configurations/EIGRP-1/)** to review aside from R8.
* 
* **Router 10**
  * ![Router 10](./Topology-Snapshots/EIGRP-1/R10.png)
  * **Router 10 Metric Range**
  * ![Router 10 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-1/R10-metric-metric-range.png)

* **Router 11**
  * ![Router 11](./Topology-Snapshots/EIGRP-1/R11.png)
  * **Router 11 Traceroute To OSPF Domain**
  * ![Router 11 Traceroute To OSPF Domain](./Topology-Snapshots/EIGRP-1/R11-traceroute-to-ospf-domain.png)

* **Router 7**
  * ![Router 7](./Topology-Snapshots/EIGRP-1/R7.png)

* **Router 8**
  * ![Router 8](./Topology-Snapshots/EIGRP-1/R8.png)

* **Router 9**
  * ![Router 9](./Topology-Snapshots/EIGRP-1/R9.png)
  * **Router 9 Loopback Internal Block**
  * ![Router 9 Loopback Internal Block](./Topology-Snapshots/EIGRP-1/R9-loopback-internal-block.png)
  * **Router 9 Access List Block Route from e0/1 port**
  * ![Router 9 Loopback Internal Block](./Topology-Snapshots/EIGRP-1/R9-access-list-block-route-from-e01.png)

### **4. EIGRP 101(Green Zone)**
![EIGRP-101 topology](./Topology-Snapshots/EIGRP-101/topology.png)
* **Features:**  EIGRP Load balancing implementation using Offset as well as Variance.
* **Key Routers:** **[R2](./Configurations/EIGRP-101/R2.txt)** , **[R3](./Configurations/EIGRP-101/R3.txt)**, **[R4](./Configurations/EIGRP-101/R4.txt)** , **[R5](./Configurations/EIGRP-101/R5.txt)** , **[R6](./Configurations/EIGRP-101/R6.txt)**.

* **Router 2**
  * ![Router 2](./Topology-Snapshots/EIGRP-101/R2.png)

* **Router 3**
  * ![Router 3](./Topology-Snapshots/EIGRP-101/R3.png)

* **Router 4**
  * ![Router 4](./Topology-Snapshots/EIGRP-101/R4.png)

* **Router 5**
  * ![Router 5](./Topology-Snapshots/EIGRP-101/R5.png)

* **Router 6**
  * ![Router 6](./Topology-Snapshots/EIGRP-101/R6.png)

### **4. EIGRP Hub & Spoke topology (RED Zone)**
![EIGRP-HUB&SPOKE topology](./Topology-Snapshots/Hub%20%26%20Spoke%20topology/topology.png)
* **Features:**  EIGRP Hub and Spoke Topology implementated for monitioring of the data using a central device.
* **Key Routers:** **[Hub](./Configurations/Hub%20%26%20Spoke%20topology/hub-config.txt)** , **[Br-Spoke-1](./Configurations/Hub%20%26%20Spoke%20topology/Br-spoke-1.txt)** , **[Br-Spoke-2](./Configurations/Hub%20%26%20Spoke%20topology/Br-spoke-2.txt)**.  

* **HUB **
  * ![Hub](./Topology-Snapshots/Hub%20%26%20Spoke%20topology/hub.png)

* **Br-spoke-1 **
  * ![Br-spoke-1](./Topology-Snapshots/Hub%20%26%20Spoke%20topology/Br-spoke-1.png)

* **Br-spoke-2 **
  * ![Br-spoke-2](./Topology-Snapshots/Hub%20%26%20Spoke%20topology/Br-spoke-2.png)


### **3. EIGRP Named Mode (Purple/Yellow Zones)**
* **Role:** Modernized EIGRP implementation using Address Families.
* **Instances:** `e4033` and `e3340`.
* **Features:** Demonstrates the scalability of Named Mode configuration over Classic EIGRP.
* ### ***EIGRP E3340**
![EIGRP-E3340 topology](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/topology.png)
* **Key Routers:** **[R21](./Configurations/EIGRP-NAMED-mode-e3340/R21.txt)** , **[R22](./Configurations/EIGRP-NAMED-mode-e3340/R22.txt)** , **[R23](./Configurations/EIGRP-NAMED-mode-e3340/R23.txt)** , **[R24](./Configurations/EIGRP-NAMED-mode-e3340/R24.txt)**.
* * **Router 21**
  * ![Router 21](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R21.png)
  * **Router 21 EIGRP NEIGHBORS**
  * ![Router 21 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R21-eigrp-neighbors.png)
* * **Router 22**
  * ![Router 22](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R22.png)
  * **Router 22 EIGRP NEIGHBORS**
  * ![Router 22 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R22-eigrp-neighbors.png)
* * **Router 23**
  * ![Router 23](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R23.png)
  * **Router 23 EIGRP NEIGHBORS**
  * ![Router 23 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R23-eigrp-neighbors.png)
* * **Router 24**
  * ![Router 24](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R24.png)
  * **Router 24 EIGRP NEIGHBORS**
  * ![Router 24 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e3340/R24-eigrp-neighbors.png)
    
* ### ***EIGRP E4033**
![EIGRP-E3340 topology](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/topology.png)
* **Key Routers:** **[R25](./Configurations/EIGRP-NAMED-mode-e4033/R25.txt)** , **[R26](./Configurations/EIGRP-NAMED-mode-e4033/R26.txt)** , **[R27](./Configurations/EIGRP-NAMED-mode-e4033/R27.txt)** , **[R28](./Configurations/EIGRP-NAMED-mode-e4033/R28.txt)**.

* * **Router 25**
  * ![Router 25](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R25.png)
  * **Router 25 EIGRP NEIGHBORS**
  * ![Router 25 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R25-eigrp-neighbors.png)

* * **Router 26**
  * ![Router 26](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R26.png)
  * **Router 26 EIGRP NEIGHBORS**
  * ![Router 26 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R26-eigrp-neighbors.png)
  
* * **Router 27**
  * ![Router 27](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R27.png)
  * **Router 27 EIGRP NEIGHBORS**
  * ![Router 27 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R27-eigrp-neighbors.png)
  
* * **Router 28**
  * ![Router 28](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R28.png)
  * **Router 28 EIGRP NEIGHBORS**
  * ![Router 28 EIGRP NEIGHBORS](./Topology-Snapshots/EIGRP-NAMED-mode-e4033/R28-eigrp-neighbors.png)
  
    
