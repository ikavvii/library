The **Huffman Coding** system—a **greedy method** of algorithm design—can be used to generate an optimal prefix-free code for data compression.

### **1. Building the Huffman Tree**

To find the codes, we repeatedly combine the two nodes with the lowest frequencies until a single root is formed.

- **Initial Frequencies:** Q: 2, P: 9, L: 10, S: 13, E: 16, A: 40.
- **Step 1:** Combine **Q (2)** and **P (9)** to create a new internal node **(11)**.
- **Step 2:** Combine **L (10)** and the new node **(11)** to create internal node **(21)**.
- **Step 3:** Combine **S (13)** and **E (16)** to create internal node **(29)**.
- **Step 4:** Combine internal nodes **(21)** and **(29)** to create internal node **(50)**.
- **Step 5:** Finally, combine **A (40)** and node **(50)** to form the **Root (90)**.

### **2. Generated Huffman Codes**

By assigning '0' to the left branch and '1' to the right branch of each node in the resulting tree, we derive the following codes:

|Character|Frequency|Huffman Code|
|:--|:--|:--|
|**A**|40|**0**|
|**P**|9|**1011**|
|**Q**|2|**1010**|
|**L**|10|**100**|
|**E**|16|**111**|
|**S**|13|**110**|

---

### **3. Encoding the Message "APPLE"**

To encode the message, we replace each character with its corresponding Huffman code:

- **A** $\rightarrow$ 0
- **P** $\rightarrow$ 1011
- **P** $\rightarrow$ 1011
- **L** $\rightarrow$ 100
- **E** $\rightarrow$ 111

**Encoded Binary String:** `010111011100111`

---

### **4. Decoding the Message**

To decode, the receiver traverses the Huffman tree starting from the root for each bit until a leaf node (character) is reached:

1. **"0"**: Immediate leaf reached $\rightarrow$ **A**
2. **"1011"**: Traverse Right(1) $\rightarrow$ Left(0) $\rightarrow$ Right(1) $\rightarrow$ Right(1) $\rightarrow$ **P**
3. **"1011"**: Traverse Right(1) $\rightarrow$ Left(0) $\rightarrow$ Right(1) $\rightarrow$ Right(1) $\rightarrow$ **P**
4. **"100"**: Traverse Right(1) $\rightarrow$ Left(0) $\rightarrow$ Left(0) $\rightarrow$ **L**
5. **"111"**: Traverse Right(1) $\rightarrow$ Right(1) $\rightarrow$ Right(1) $\rightarrow$ **E**

**Decoded Message:** `APPLE`

This greedy approach ensures that the most frequent character ('A') uses the shortest code (1 bit), while less frequent characters use longer codes, thereby minimizing the total bits required for transmission.