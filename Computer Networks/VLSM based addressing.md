![](attachments/Pasted%20image%2020260817032853.png)

The ISP has been allocated **24.16.16.0/12**.

### (a) Address-space sufficiency

A `/12` block contains:

[  
2^{32-12}=2^{20}=1,048,576\text{ addresses}  
]

Required:

- **Group 1:** 2 customers × 1024 = 2,048 addresses
    
- **Group 2:** 2 customers × 512 = 1,024 addresses
    
- **Group 3:** 8 customers × 4 = 32 addresses
    

Total required:

[  
2048+1024+32=\boxed{3104\text{ addresses}}  
]

Therefore, the block is **more than sufficient**.

Unallocated addresses:

[  
1,048,576-3,104=\boxed{1,045,472}  
]

---

### (b) VLSM allocation

Allocate the largest networks first.

|Group|Customer|Required addresses|CIDR|Allocated subnet|
|---|---|--:|---|---|
|Group 1|C1|1024|/22|24.16.16.0/22|
|Group 1|C2|1024|/22|24.16.20.0/22|
|Group 2|C3|512|/23|24.16.24.0/23|
|Group 2|C4|512|/23|24.16.26.0/23|
|Group 3|C5|4|/30|24.16.28.0/30|
|Group 3|C6|4|/30|24.16.28.4/30|
|Group 3|C7|4|/30|24.16.28.8/30|
|Group 3|C8|4|/30|24.16.28.12/30|
|Group 3|C9|4|/30|24.16.28.16/30|
|Group 3|C10|4|/30|24.16.28.20/30|
|Group 3|C11|4|/30|24.16.28.24/30|
|Group 3|C12|4|/30|24.16.28.28/30|

This uses addresses from **24.16.16.0 through 24.16.28.31**.

---

### (c) Details of every allocated subnet

|Customer|Subnet ID|CIDR|Subnet Mask|Valid Host Range|Broadcast|Usable Hosts|
|---|---|---|---|---|---|--:|
|C1|24.16.16.0|/22|255.255.252.0|24.16.16.1 – 24.16.19.254|24.16.19.255|1022|
|C2|24.16.20.0|/22|255.255.252.0|24.16.20.1 – 24.16.23.254|24.16.23.255|1022|
|C3|24.16.24.0|/23|255.255.254.0|24.16.24.1 – 24.16.25.254|24.16.25.255|510|
|C4|24.16.26.0|/23|255.255.254.0|24.16.26.1 – 24.16.27.254|24.16.27.255|510|
|C5|24.16.28.0|/30|255.255.255.252|24.16.28.1 – 24.16.28.2|24.16.28.3|2|
|C6|24.16.28.4|/30|255.255.255.252|24.16.28.5 – 24.16.28.6|24.16.28.7|2|
|C7|24.16.28.8|/30|255.255.255.252|24.16.28.9 – 24.16.28.10|24.16.28.11|2|
|C8|24.16.28.12|/30|255.255.255.252|24.16.28.13 – 24.16.28.14|24.16.28.15|2|
|C9|24.16.28.16|/30|255.255.255.252|24.16.28.17 – 24.16.28.18|24.16.28.19|2|
|C10|24.16.28.20|/30|255.255.255.252|24.16.28.21 – 24.16.28.22|24.16.28.23|2|
|C11|24.16.28.24|/30|255.255.255.252|24.16.28.25 – 24.16.28.26|24.16.28.27|2|
|C12|24.16.28.28|/30|255.255.255.252|24.16.28.29 – 24.16.28.30|24.16.28.31|2|

**Note:** `/30` is used for Group 3 because each customer requires **2 usable IP addresses**. A `/30` has 4 total addresses: network + 2 usable hosts + broadcast.

---

### (d) Address-utilization analysis

The allocated address blocks consume:

[  
2(1024)+2(512)+8(4)=3104  
]

So the overall utilization of the ISP's `/12` block is:

[  
\frac{3104}{1,048,576}\times100  
\approx\boxed{0.296%}  
]

Thus, about **99.704%** of the ISP's address space remains available for future allocation.

Within each subnet, the usable-host efficiency is:

- `/22`: (1022/1024 \approx 99.8%)
    
- `/23`: (510/512 \approx 99.6%)
    
- `/30`: (2/4 = 50%)
    

The VLSM design is efficient because each customer receives the **smallest subnet that satisfies its requirement**, minimizing address wastage.

---

### (e) Hierarchical network diagram

```text
                    AirVoice ISP
                 24.16.16.0/12
                        |
        +---------------+----------------+
        |               |                |
      Group 1         Group 2          Group 3
        |               |                |
    +---+---+       +---+---+       +----+----+----+----+
    |       |       |       |       |    |    |    |    |
  C1      C2       C3      C4      C5   C6   C7   C8   ...
 /22     /22      /23     /23     /30  /30  /30  /30
16.0    20.0     24.0    26.0    28.0 28.4 28.8 28.12

                         Group 3 continued:
                    C9 /30  → 24.16.28.16
                    C10 /30 → 24.16.28.20
                    C11 /30 → 24.16.28.24
                    C12 /30 → 24.16.28.28
```

### Final answer

The VLSM allocation is therefore:

[  
\boxed{  
\begin{aligned}  
&24.16.16.0/22\  
&24.16.20.0/22\  
&24.16.24.0/23\  
&24.16.26.0/23\  
&24.16.28.0/30,;24.16.28.4/30,\ldots,24.16.28.28/30  
\end{aligned}}  
]

It satisfies **all 12 customer requirements** while using only **3,104 of 1,048,576 addresses**.