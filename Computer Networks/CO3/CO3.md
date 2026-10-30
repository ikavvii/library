Here is the official **CO 3 Question Bank** for **Transport Layer Services, TCP Protocols, and Congestion Control**, curated directly from previous semester examination papers (`23MXAE`) and the syllabus requirements.

---

# 📚 CO 3 QUESTION BANK — Transport Layer Services, TCP Protocols & Congestion Control

- **Course Outcome 3 (CO3):** _"Paraphrase and analyze technology to ensure providing error-free and no data loss communications."_
- **Exam Weightage:** 25 Marks (Part A: 3–5 Marks | Part B: 7–10 Marks | Part C: 12 Marks)

---

## 📌 SECTION 1: PART A QUESTIONS (3 to 5 Marks) — Short Answer & Scenario Analysis

### **Q1.1 [Scenario-Based]**

A banking application requires **high reliability** for financial transactions, while its customer support module requires **low latency** for real-time messaging. Determine which TCP/IP transport protocol should be chosen for each case and justify your answer.

- **Core Answer Outline:**
    - **Financial Transactions:** Choose **TCP (Transmission Control Protocol)**. It provides connection-oriented, reliable byte-stream delivery with error checking, sequence numbers, ACKs, and retransmissions to prevent data loss or corruption.
    - **Customer Support Chat / Real-Time Media:** Choose **UDP (User Datagram Protocol)** or TCP with low overhead. For voice/chat streaming where minimal delay is critical and minor packet loss is acceptable, UDP avoids the head-of-line blocking and multi-roundtrip connection overhead of TCP.

### **Q1.2 [Formula / Problem-Solving]**

In a TCP connection, the current congestion window is \(\text{cwnd} = 4,000\text{ bytes}\) and the receiver's advertised window is \(\text{rwnd} = 7,000\text{ bytes}\). The sender has already transmitted \(3,000\text{ bytes}\) which remain unacknowledged.

1. Calculate how many additional bytes the sender can transmit immediately.
2. State the formula used.

- **Core Answer Outline:**
    - **Formula:** \(\text{Usable Window} = \min(\text{cwnd}, \text{rwnd}) - \text{Unacknowledged Bytes}\).
    - **Calculation:** \(\min(4000, 7000) - 3000 = 4000 - 3000 = 1,000\text{ bytes}\).
    - The sender can transmit **1,000 additional bytes** immediately.

### **Q1.3 [Conceptual]**

"Data loss due to congestion is controlled at the transport layer as well." Justify this statement and explain briefly how the transport layer achieves it.

- **Core Answer Outline:**
    - Transport layer protocols (specifically TCP) detect implicit network congestion via packet loss signals (RTO timeouts or 3 duplicate ACKs).
    - Upon detection, TCP dynamically throttles its transmission rate by adjusting the congestion window (\(\text{cwnd}\)) using **Slow Start**, **Congestion Avoidance (AIMD)**, and **Fast Recovery** algorithms.

### **Q1.4 [Protocol Comparison]**

Although UDP is considered an unreliable transport protocol, it is widely used for real-time applications such as video streaming. Justify this statement by analyzing the characteristics of UDP versus TCP.

- **Core Answer Outline:**
    - UDP has no connection setup delay (0-RTT), minimal header overhead (8 bytes vs 20–60 bytes for TCP), and no retransmission delays or congestion window throttling.
    - In real-time video/audio, timely arrival is critical; late retransmitted packets are useless to the playout buffer.

---

## 📌 SECTION 2: PART B QUESTIONS (7 to 10 Marks) — Numericals & Algorithmic Tracing

### **Q2.1 [UDP Checksum Calculation Numerical]**

**(a)** Determine the 8-bit checksum added by the sender to the UDP segment represented in hex `0xDE291F79E4`.  
**(b)** Show step-by-step receiver-side calculation proving that the segment is received error-free.

#### **Step-by-Step Solution Template:**

1. **Sender Side Calculation:**
    - Split the hex string into 8-bit (1-byte) blocks: `DE`, `29`, `1F`, `79`, `E4`.
    - Add the bytes using **1's Complement Arithmetic** (wrap around carry bits): \[\text{Sum} = \text{DE}_{16} + 29_{16} + 1\text{F}_{16} + 79_{16} + \text{E4}_{16}\]
        - \(\text{DE}_{16} + 29_{16} = 107_{16}\)
        - \(107_{16} + 1\text{F}_{16} = 126_{16}\)
        - \(126_{16} + 79_{16} = 19F_{16}\)
        - \(19F_{16} + \text{E4}_{16} = 283_{16}\)
    - Wrap around carry (\(2_{16}\)): \(83_{16} + 2_{16} = 85_{16} = 10000101_2\).
    - Take 1's complement of \(85_{16}\) to find Checksum: \[\text{Checksum} = \sim(10000101_2) = 01111010_2 = 7\text{A}_{16}\]
2. **Receiver Side Verification:**
    - Add all received data bytes plus the checksum: \[\text{Receiver Sum} = 85_{16} + 7\text{A}_{16} = \text{FF}_{16} = 11111111_2\]
    - Since the 1's complement of \(\text{FF}_{16}\) is `0x00`, the segment is verified as **error-free**.

---

### **Q2.2 [TCP Deadlock & Flow Control]**

**(a)** Explain the deadlock situation in TCP caused by a zero-window advertisement with a suitable example.  
**(b)** Explain how TCP persist timers and window probe segments resolve this deadlock.

#### **Solution Outline:**

- **Deadlock Trigger:** Receiver sends ACK with \(\text{rwnd} = 0\) when its buffer is full. Sender stops transmitting. Later, the receiver buffer frees up and sends a window update ACK (\(\text{rwnd} = 600\)), but this ACK gets **lost in transit**.
- **Deadlock State:** Sender is waiting for a non-zero window ACK; Receiver is waiting for sender to transmit data. Both sides freeze indefinitely.
- **Resolution:** When sender receives \(\text{rwnd} = 0\), it starts a **Persist Timer**. Upon expiration, sender transmits a **1-byte Window Probe Segment**. Receiver responds with an ACK stating its current \(\text{rwnd}\). If still 0, the persist timer doubles (exponential backoff) and probes again until the connection opens.

---

### **Q2.3 [TCP Sliding Window & Loss Recovery Tracing]**

A TCP connection uses 4 bits for sequence numbers. Host A sends packets with sequence numbers `0` through `8`. The ACK for packet `5` is received successfully, but packet `6` is lost. Packets `7` and `8` arrive at the receiver. Subsequently, the retransmission timer for segment `6` expires.

1. Illustrate the timeline of transmissions and acknowledgments.
2. Explain how the TCP sliding window protocol detects and recovers from the loss of packet `6`.
3. Show how the sliding window changes when packet `6` is retransmitted and acknowledged. Does the sender perform a cumulative ACK upon receiving segment `6`?

#### **Solution Outline:**

- **Sequence Numbers:** \(2^4 = 16\) space (\(0\) to \(15\)).
- **Event Sequence:**
    - Host A sends \(0, 1, 2, 3, 4, 5, 6, 7, 8\).
    - Receiver receives \(0..5\), sends \(\text{ACK}=6\).
    - Packet `6` drops. Receiver receives `7` and `8` (out of order), buffers them, and sends **Duplicate ACKs** (\(\text{ACK}=6\)).
    - When packet `6` timer expires (or 3 dup ACKs arrive), Host A retransmits segment `6`.
    - Upon receiving segment `6`, the receiver fills the gap (\(6, 7, 8\)) and issues a **Cumulative ACK = 9**.
    - The sender's sliding window slides forward past byte `8`.

---

## 📌 SECTION 3: PART C QUESTIONS (12 Marks) — Comprehensive Analysis & Design Problems

### **Q3.1 [TCP Congestion Control Tracing Numerical]**

A TCP connection is established with:

- Maximum Segment Size (\(\text{MSS}\)) = \(2,000\text{ bytes}\)
- Slow Start Threshold (\(\text{ssthresh}\)) = \(24,000\text{ bytes}\)
- Initial Congestion Window (\(\text{cwnd}\)) = \(4,000\text{ bytes}\)

Assume every acknowledgment is received successfully, each ACK corresponds to one segment, and no packet loss occurs initially. Analyze this scenario and answer the following:

1. Calculate the congestion window size (\(\text{cwnd}\)) after receiving **5 consecutive ACKs**.
2. Determine after how many total ACKs the connection will **exit the Slow Start phase** and enter the Congestion Avoidance phase.
3. If a packet loss occurs via timeout when \(\text{cwnd}\) reaches \(24,000\text{ bytes}\), calculate the new values of \(\text{ssthresh}\) and \(\text{cwnd}\) immediately after the loss.

#### **Full Step-by-Step Solution:**

1. **Initial State:**
    
    - \(\text{cwnd}_0 = 4,000\text{ bytes} = 2\text{ MSS}\).
    - \(\text{ssthresh} = 24,000\text{ bytes} = 12\text{ MSS}\).
    - State = **Slow Start** (\(\text{cwnd} < \text{ssthresh}\)).
2. **Part 1: \(\text{cwnd}\) after 5 consecutive ACKs:**
    
    - In Slow Start, for **each ACK received**, \(\text{cwnd}\) increases by \(1\text{ MSS}\) (\(2,000\text{ bytes}\)): \[\text{cwnd}_{\text{new}} = \text{cwnd}_{\text{old}} + \text{MSS}\]
    - After 1st ACK: \(\text{cwnd} = 4,000 + 2,000 = 6,000\text{ bytes}\) (\(3\text{ MSS}\))
    - After 2nd ACK: \(\text{cwnd} = 6,000 + 2,000 = 8,000\text{ bytes}\) (\(4\text{ MSS}\))
    - After 3rd ACK: \(\text{cwnd} = 8,000 + 2,000 = 10,000\text{ bytes}\) (\(5\text{ MSS}\))
    - After 4th ACK: \(\text{cwnd} = 10,000 + 2,000 = 12,000\text{ bytes}\) (\(6\text{ MSS}\))
    - After 5th ACK: \(\text{cwnd} = 12,000 + 2,000 = \mathbf{14,000\text{ bytes}}\) (\(\mathbf{7\text{ MSS}}\)).
3. **Part 2: Total ACKs to exit Slow Start:**
    
    - Slow start continues until \(\text{cwnd} \ge \text{ssthresh} = 24,000\text{ bytes}\) (\(12\text{ MSS}\)).
    - Starting \(\text{cwnd} = 4,000\text{ bytes}\) (\(2\text{ MSS}\)).
    - Required increase = \(24,000 - 4,000 = 20,000\text{ bytes} = 10\text{ MSS}\).
    - Since each ACK increases \(\text{cwnd}\) by \(1\text{ MSS}\) (\(2,000\text{ bytes}\)), total ACKs needed = **10 ACKs**.
4. **Part 3: Values after Packet Loss at \(\text{cwnd} = 24,000\text{ bytes}\):**
    
    - **If Loss is detected by Timeout:** \[\text{ssthresh}_{\text{new}} = \max\left(\frac{\text{cwnd}}{2}, 2 \times \text{MSS}\right) = \frac{24,000}{2} = \mathbf{12,000\text{ bytes}}\ (\mathbf{6\text{ MSS}})\] \[\text{cwnd}_{\text{new}} = 1\text{ MSS} = \mathbf{2,000\text{ bytes}}\] _(Connection re-enters Slow Start phase)._
    - **If Loss is detected by 3 Duplicate ACKs (Fast Recovery / Reno):** \[\text{ssthresh}_{\text{new}} = \frac{24,000}{2} = \mathbf{12,000\text{ bytes}}\ (\mathbf{6\text{ MSS}})\] \[\text{cwnd}_{\text{new}} = \text{ssthresh} + 3\text{ MSS} = 12,000 + 6,000 = \mathbf{18,000\text{ bytes}}\] _(Connection enters Fast Recovery / Congestion Avoidance phase)._

---

### **Q3.2 [TCP 3-Way Handshake Control Segment Tracing]**

A client (Host A) opens a TCP connection with an Initial Sequence Number \(\text{ISN}_A = 20,000\). The server (Host B) accepts with an Initial Sequence Number \(\text{ISN}_B = 1,000\). Client window size is set for 16 segments (each segment \(= 1,000\text{ bytes}\)).

Draw a timeline diagram illustrating all sequence numbers, acknowledgment numbers, and flag bits for:

1. Connection establishment via 3-way handshake.
2. Transmission of the first data segment from Host A.
3. Transmission of the next 3 segments from Host A.
4. Host B sending an ACK with ACK number set to `24001`.
5. Connection termination using 3-way/4-way handshake.

#### **Sequence Tracing Diagram:**

```
     Host A (Client)                                      Host B (Server)
  ISN_A = 20,000                                       ISN_B = 1,000
        |                                                     |
        | ------------- [SYN, Seq=20000, ACK=0] ------------> | (1. SYN)
        | <------- [SYN+ACK, Seq=10000, ACK=20001] ---------- | (2. SYN+ACK)
        | ------------- [ACK, Seq=20001, ACK=10001] --------> | (3. Handshake Complete)
        |                                                     |
        | --- [Data Seg 1: Seq=20001..21000 (1000B)] -------> | (4. First Segment)
        | --- [Data Seg 2: Seq=21001..22000 (1000B)] -------> |
        | --- [Data Seg 3: Seq=22001..23000 (1000B)] -------> |
        | --- [Data Seg 4: Seq=23001..24000 (1000B)] -------> | (5. Next 3 Segments)
        |                                                     |
        | <------------------ [ACK=24001] ------------------- | (6. Cumulative ACK)
        |                                                     |
        | ----------------- [FIN+ACK, Seq=24001] ------------> | (7. Active Close)
        | <----------------- [ACK, ACK=24002] --------------- |
        | <----------------- [FIN+ACK, Seq=10001] ----------- | (8. Passive Close)
        | ----------------- [ACK, ACK=10002] ---------------> | (9. Connection Closed)
```

---

## 💡 EXAM CHEAT-SHEET: Quick Reference Formulas for CO 3

1. **TCP Effective / Usable Window:** \[\text{Usable Window} = \min(\text{cwnd}, \text{rwnd}) - \text{Unacknowledged Bytes}\]
2. **Slow Start Growth Rate:** \[\text{cwnd}_{\text{new}} = \text{cwnd}_{\text{old}} + \text{MSS} \quad (\text{per ACK received})\] _(Effectively doubles \(\text{cwnd}\) every RTT)_
3. **Congestion Avoidance Growth Rate:** \[\text{cwnd}_{\text{new}} = \text{cwnd}_{\text{old}} + \frac{\text{MSS} \times \text{MSS}}{\text{cwnd}} \quad (\text{per ACK received})\] _(Increases \(\text{cwnd}\) by \(1\text{ MSS}\) per RTT)_
4. **Multiplicative Decrease (Loss Event):** \[\text{ssthresh}_{\text{new}} = \max\left(\frac{\text{cwnd}}{2}, 2 \times \text{MSS}\right)\]
    - **RTO Timeout:** Set \(\text{cwnd} = 1\text{ MSS}\) (Enter Slow Start).
    - **3 Duplicate ACKs:** Set \(\text{cwnd} = \text{ssthresh} + 3\text{ MSS}\) (Fast Recovery).
5. **1's Complement Arithmetic Checksum:** \[\text{Checksum} = \sim \left( \sum \text{Data Words} \text{ with wrapped carry} \right)\]

---

Would you like me to generate a similar **Question Bank for CO 2 (IP Addressing, VLSM Subnetting & Routing Protocols)** or **CO 4 (Application Protocols & DNS/SMTP)** next? 🚀