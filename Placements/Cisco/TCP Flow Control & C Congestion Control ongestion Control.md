
Transmission Control Protocol (TCP) is a connection-oriented, reliable transport layer protocol that provides a byte-stream service. To act as a "safe" protocol, TCP uses strict mechanisms to ensure it does not overwhelm either the receiver or the underlying network.

## 1. Flow Control (Receiver-Driven)

**Goal:** Prevent a fast sender from overwhelming a slow receiver's buffer.

- **Mechanism (Sliding Window):** Flow control is managed via the **sliding window mechanism**. The receiver allocates a specific buffer size for incoming data and communicates the remaining unused space to the sender in every acknowledgment (ACK). 
- **Receive Window (`rwnd`):** This advertised value is known as the receive window, which tells the sender exactly how many unacknowledged bytes it is allowed to transmit.
- **Zero Window & Persist Timer:** If the receiver's application processes data too slowly, its buffer fills up, and it will advertise a window size of **zero**. The sender must then pause transmission and start a **persist timer**. The sender will periodically send 1-byte "probe" packets to check if the receiver's window has reopened, preventing a deadlock.

## 2. Congestion Control (Network-Driven)

**Goal:** Prevent a sender from injecting too much data into the network and causing router buffers to overflow, which leads to packet loss and delays.

- **Mechanism (Congestion Window):** TCP defines a sender-side variable called the **Congestion Window (`cwnd`)**.
- **The Golden Rule:** At any given time, the maximum amount of unacknowledged data the sender can transmit is determined by: `min(cwnd, rwnd)`.

TCP dynamically adapts the `cwnd` using an **AIMD (Additive Increase, Multiplicative Decrease)** approach to probe for available bandwidth. This process is divided into several distinct phases:

### Phase A: Slow Start

- When a connection begins (or restarts after a severe timeout), TCP doesn't know the network's capacity.
- It starts with a `cwnd` of 1 Maximum Segment Size (MSS).
- For every ACK received, `cwnd` doubles each Round Trip Time (RTT).
- Despite the name "slow start," the growth is **exponential** (e.g., 1 → 2 → 4 → 8).
- This exponential growth continues until `cwnd` reaches a predetermined threshold called the **slow start threshold (`ssthresh`)**.

### Phase B: Congestion Avoidance

- Once `cwnd` $\ge$ `ssthresh`, the algorithm switches to the Congestion Avoidance phase.
- To avoid suddenly flooding the network, `cwnd` grows **linearly** (Additive Increase), increasing by just 1 MSS per RTT.

### Phase C: Congestion Detection & Recovery

Network congestion is implicitly detected through packet loss. TCP reacts differently based on the severity of the loss:

1. **Mild Congestion (3 Duplicate ACKs):**
    - If a sender receives 3 duplicate ACKs, it implies a segment was lost, but subsequent segments are still getting through.
    - **Fast Retransmit:** TCP immediately retransmits the missing segment without waiting for the timeout.
    - **Fast Recovery:** TCP performs a _Multiplicative Decrease_. It cuts `ssthresh` to half of the current `cwnd`, sets the new `cwnd` to the new `ssthresh` value, and resumes in the **Congestion Avoidance** (linear) phase.
2. **Severe Congestion (Timeout / RTO):**
    - If a sender's Retransmission Timeout (RTO) expires without an ACK, it assumes severe network congestion (packets are being dropped heavily).
    - TCP reacts aggressively: It sets `ssthresh` to half of the current `cwnd`, drops `cwnd` all the way back to **1 MSS**, and completely restarts the **Slow Start** (exponential) phase.

## 3. Modern Congestion Control Variants (Interview Bonus)

Top companies often ask about modern TCP variants. Knowing these sets you apart as an advanced candidate:

- **TCP Reno:** The classic loss-based algorithm that uses standard AIMD.
- **TCP CUBIC:** The current default in Linux. It uses a cubic mathematical function instead of a linear one to quickly ramp up to the previous maximum window size. It is excellent for standard datacenters with low RTT.
- **TCP BBR (Bottleneck Bandwidth and RTT):** Developed by Google, BBR models the actual bandwidth and RTT rather than just reacting blindly to packet loss. It is highly recommended for high-latency, satellite, or lossy wireless networks.

## 4. Quick Comparison for Interviews

|Feature|Flow Control|Congestion Control|
|:--|:--|:--|
|**Protects**|The Receiver|The Network|
|**Controlled By**|Receiver (via `rwnd` field in TCP Header)|Sender (via internal `cwnd` variable)|
|**Trigger for Change**|Application buffer filling up/emptying|Packet loss (Timeouts or Duplicate ACKs)|
|**Mechanism**|Sliding Window Protocol|Slow Start, AIMD, Fast Retransmit/Recovery|

## 5. Typical Practice / Interview Problems

**Q: If the Slow Start Threshold (`ssthresh`) is 8 MSS and the initial `cwnd` is 2 MSS, what will be the window size at the start of the 4th transmission?**

- _Solution:_
    - 1st transmission: 2 MSS
    - 2nd transmission: 4 MSS (doubles)
    - 3rd transmission: 8 MSS (doubles, hits `ssthresh`)
    - 4th transmission: 9 MSS (Enters Congestion Avoidance, linear +1 increase).

**Q: A TCP sender has a Congestion Window of 4 KB and the Receiver advertises a Receive Window of 6 KB. The sender has 10,240 as the last byte sent and 8,192 as the last byte acknowledged. How much free space is currently in the sender's window?**

- _Solution:_
    - The effective window size is `min(cwnd, rwnd)` = `min(4 KB, 6 KB)` = 4 KB (4096 bytes).
    - Unacknowledged bytes in flight = Last byte sent - Last byte ACKed + 1 = 10,240 - 8,193 + 1 = 2048 bytes.
    - Free space = Effective Window (4096) - Bytes in flight (2048) = 2048 bytes (meaning half the window is empty).

**Q: What is the purpose of the "Fast Retransmit" algorithm?**

- _Solution:_ Normally, TCP waits for a Retransmission Timer to expire before re-sending a lost packet. Fast Retransmit speeds up this recovery by immediately retransmitting a segment as soon as **three duplicate ACKs** are received, bypassing the long timeout timer entirely.