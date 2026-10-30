Here is the exam-oriented **Question Bank for CO3 / UNIT 3 — Cloud Architecture, Platforms and Programming Models**, constructed from the official syllabus and the end-semester examination papers.

---

# **CO 3 UNIT 3 — Cloud Architecture, Platforms and Programming Models**

### **Course Outcome (CO3)**

_Analyse and implement the programming models of cloud computing and its applications._

---

## **Part A: Short Answer / Concept Questions (3 Marks Each)**

1. **Google BigTable Schema**: Sketch the schematic data model of Google BigTable and identify its core components.
    - _Key Answer Elements_: Show row key, column family, column qualifier, timestamp, and cell value.
2. **Google BigTable 'Anchor' Qualifier**: Recognize the role of the `anchor` column qualifier in BigTable web table implementations.
    - _Key Answer Elements_: Explain how referring site links are stored as column qualifiers (e.g., `anchor:cnnsi.com`) with cell text as the display anchor text.
3. **AWS Data Transfer**: Specify the primary mechanisms for transferring massive datasets into AWS.
    - _Key Answer Elements_: Highlight AWS Snowball/Snowmobile (physical device transfer) and AWS DataSync / Direct Connect (network transfer).
4. **HDFS NameNode Metadata Files**: State and define the two key metadata files managed by the HDFS NameNode.
    - _Key Answer Elements_: `FSImage` (point-in-time snapshot of file system metadata) and `EditLog` (transaction log recording every write/append operation).
5. **Eucalyptus Cluster Controller (CC)**: State the key functions of the Cluster Controller in Eucalyptus cloud architecture.
    - _Key Answer Elements_: Controls node controllers within a cluster, schedules VM execution, and manages virtual network routing.
6. **Aneka Container Services**: Outline the primary role of the Container component in the Aneka cloud platform framework.
    - _Key Answer Elements_: Serves as the execution engine for services, managing fabric, execution, and foundation services.

---

## **Part B: Analytical & Descriptive Questions (5 Marks Each)**

1. **Eucalyptus Architecture**: Diagrammatically represent the 5-layer architecture of Eucalyptus cloud and explain the functions of Cloud Controller (CLC), Cluster Controller (CC), Storage Controller (SC), Node Controller (NC), and Walrus.
    - _Key Answer Elements_:
        - **CLC**: Entry point and global resource manager.
        - **CC**: Manages VM state and cluster resources.
        - **SC**: Block-level storage interface (EBS equivalent).
        - **NC**: Hypervisor-level VM host executor.
        - **Walrus**: S3-compatible object storage.
2. **Map-Reduce Programming Phases**: Describe the fundamental execution phases involved in the Map-Reduce programming model.
    - _Key Answer Elements_: Input Splitting \(\rightarrow\) Map Phase \(\rightarrow\) Combine (optional) \(\rightarrow\) Shuffle & Sort \(\rightarrow\) Reduce Phase \(\rightarrow\) Final Output Writing.
3. **AWS EC2 Instance Categorization**: Describe the various purchasing/pricing instance types offered by AWS EC2 with practical use cases for each.
    - _Key Answer Elements_:
        - **On-Demand**: Short-term, unpredictable workloads without upfront commitment.
        - **Reserved**: Long-term baseline workloads (1–3 year commitment for cost discount).
        - **Spot**: Fault-tolerant, stateless batch jobs utilizing spare capacity at deep discounts.
        - **Dedicated**: Strict regulatory compliance requiring isolated physical hardware.
4. **Google BigTable Architecture**: Draw the Google BigTable data model and detail the concepts of **Tablets** and **Column Families**.
    - _Key Answer Elements_:
        - **Column Family**: Grouping of related columns stored together for locality.
        - **Tablet**: Contiguous range of rows partitioned dynamically for distributed balancing.
5. **Aneka Framework Services**: Sketch the Aneka platform architecture and classify the services offered by its Container framework.
    - _Key Answer Elements_:
        - **Fabric Services**: Hardware abstraction, node discovery, profiling.
        - **Execution Services**: Job scheduling, execution, and dispatching.
        - **Foundation Services**: Storage management, billing, accounting, security.

---

## **Part C: Comprehensive & Scenario-Based Questions (12 Marks Each)**

1. **HDFS Write Protocol & Data Copy Pipeline**:
    
    - **Question**: Describe the step-by-step procedure of the **HDFS Write Operation**. Demonstrate how a client writes a 500MB file (with a 128MB block size and a replication factor of 3) to DataNodes, detailing interactions with the NameNode and pipeline creation.
    - **Model Answer Structure**:
        - _Block Breakdown_: 500 MB \(\div\) 128 MB = 3 full blocks (128 MB) + 1 partial block (116 MB) = 4 blocks total.
        - _Step 1 (Client request)_: Client requests NameNode to create file entry.
        - _Step 2 (NameNode check & allocation)_: NameNode verifies permissions, checks FSImage/EditLog, and returns 3 target DataNode addresses per block.
        - _Step 3 (Pipeline Creation)_: Client connects to DataNode 1 \(\rightarrow\) DataNode 1 streams to DataNode 2 \(\rightarrow\) DataNode 2 streams to DataNode 3.
        - _Step 4 (Packet Streaming & ACKs)_: Data is written as 64KB packets; ACK packets traverse back through the pipeline.
        - _Step 5 (Close)_: Client notifies NameNode upon complete pipeline write.
2. **Map-Reduce Application Design & Case Study Logic**:
    
    - **Question**: Explain the Map-Reduce execution model. Construct a complete Map-Reduce application logic for an e-commerce platform that processes daily access logs to extract the **top 10 most frequently accessed URLs**.
    - **Model Answer Structure**:
        - _Input Schema_: Raw log line containing `[Timestamp, User_IP, Request_Type, URL_Accessed]`.
        - _Mapper Function_: Extracts `URL_Accessed` and emits `key-value` pair: `(URL, 1)`.
        - _Combiner / Local Reducer_: Aggregates counts per URL on local mapper node: `(URL, local_count)`.
        - _Shuffle & Sort_: Groups intermediate values by URL across the network.
        - _Reducer Function_: Sums all counts per URL: `(URL, total_count)`.
        - _Top-10 Sorting Pass_: Secondary Reducer or in-memory Min-Heap of size 10 to output the final top 10 URLs.
3. **AWS S3 Storage Optimization Scenario**:
    
    - **Question**: Compare the technical features, access latencies, and pricing structures of AWS S3 storage classes (**Standard**, **Intelligent-Tiering**, **Standard-IA**, **Glacier Instant Retrieval**, **Glacier Flexible Retrieval**, and **Glacier Deep Archive**).
    - **Scenario Application**: Recommend and justify the optimal storage class for a hospital system archiving patient discharge summaries that are rarely accessed but require immediate retrieval when a patient returns with complications.
    - **Model Answer Structure**:
        - _Comparison Table_: Compare classes across latency (ms vs. hours), retrieval cost, storage cost per GB, and minimum storage duration.
        - _Scenario Decision_: **S3 Glacier Instant Retrieval** or **S3 Standard-IA**.
        - _Justification_: Archives rarely accessed records (keeps monthly storage cost ultra-low) while ensuring millisecond retrieval speed when an urgent medical complication arises.
4. **Aneka Platform Framework Architecture**:
    
    - **Question**: Detail the Aneka Cloud Application Platform framework. Explain how Aneka supports hybrid cloud deployments and analyze how its Container framework manages thread, grid, and Map-Reduce execution models.

---

## **CO3 High-Yield Revision Summary**

| Topic                                             | Frequency in Past Papers | Target Marks  |   Priority Level    |
| :------------------------------------------------ | :----------------------: | :-----------: | :-----------------: |
| **HDFS Write Protocol Pipeline & NameNode Files** |    100% (4/4 papers)     |   12 Marks    |   **Must-Master**   |
| **Map-Reduce Execution Model & Log Case Study**   |    100% (4/4 papers)     | 5 or 12 Marks |   **Must-Master**   |
| **AWS S3 Storage Classes & Decision Scenarios**   |     75% (3/4 papers)     |   12 Marks    |  **High Priority**  |
| **Eucalyptus Architecture & Components**          |     75% (3/4 papers)     | 3 to 5 Marks  |  **High Priority**  |
| **Google BigTable Data Model Schema**             |     75% (3/4 papers)     | 3 to 5 Marks  |  **High Priority**  |
| **Aneka Container Services Framework**            |     50% (2/4 papers)     | 5 or 12 Marks | **Medium Priority** |

---

💡 _Would you like me to construct similar detailed question banks for CO1, CO2, or CO4, or provide step-by-step code/diagram solutions for any of these questions?_