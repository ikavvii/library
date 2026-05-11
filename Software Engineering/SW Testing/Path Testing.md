### **Question 2b: Full Text**

**Write a minimum level Pseudo code to handle withdraw money from a customer account by assuming the following:**

1. The customer is already authenticated.
2. Current balance in his/her account is Rs. 73,500.
3. Withdraw limit per day is Rs. 15,000.

**Apply Path testing to test the code.** (7 Marks)

---

### **Answer**

#### **1. Pseudo Code for Withdrawal Logic**

```
1.  START
2.  INITIALIZE balance = 73500
3.  INITIALIZE dailyLimit = 15000
4.  INPUT withdrawAmount
5.  IF (withdrawAmount > dailyLimit) THEN
6.      DISPLAY "Error: Daily withdrawal limit exceeded."
7.  ELSE
8.      IF (withdrawAmount > balance) THEN
9.          DISPLAY "Error: Insufficient funds in account."
10.     ELSE
11.         balance = balance - withdrawAmount
12.         DISPLAY "Cash dispensed successfully. Current Balance: ", balance
13.     ENDIF
14. ENDIF
15. STOP
```

#### **2. Path Testing Analysis**

**Control Flow Graph (Nodes):**

- **Node A (Lines 1-4):** Start and Input amount.
- **Node B (Line 5):** Decision: Is amount > dailyLimit?
- **Node C (Line 6):** Action: Display limit error.
- **Node D (Line 8):** Decision: Is amount > balance?
- **Node E (Line 9):** Action: Display insufficient funds error.
- **Node F (Lines 11-12):** Action: Dispense cash and update balance.
- **Node G (Line 15):** Stop.

**Cyclomatic Complexity ($V(G)$):**

- Formula: $V(G) = P + 1$ (where $P$ is the number of predicate/decision nodes).
- Decision Nodes: Line 5 and Line 8.
- **$V(G) = 2 + 1 = 3$.**
- This indicates there are **3 independent paths** to test.

**Independent Paths:**

- **Path 1 (Limit Exceeded):** A $\rightarrow$ B $\rightarrow$ C $\rightarrow$ G
- **Path 2 (Insufficient Funds):** A $\rightarrow$ B $\rightarrow$ D $\rightarrow$ E $\rightarrow$ G
- **Path 3 (Successful Transaction):** A $\rightarrow$ B $\rightarrow$ D $\rightarrow$ F $\rightarrow$ G

#### **3. Test Case Report**

|Test Case ID|Path|Input (`withdrawAmount`)|Expected Output|Status|
|:--|:--|:--|:--|:--|
|**TC01**|Path 1|20,000|"Error: Daily withdrawal limit exceeded."|Pass|
|**TC02**|Path 2|80,000|"Error: Daily withdrawal limit exceeded." (Note: Hits limit first)|Pass|
|**TC03**|Path 3|5,000|"Cash dispensed successfully. Current Balance: 68,500"|Pass|

**Note on Logic:** In this specific scenario where the daily limit (15,000) is much lower than the balance (73,500), the "Insufficient Funds" path is logically unreachable if the limit is checked first (as any amount exceeding the balance would have already exceeded the daily limit). However, the pseudo code includes the check to maintain a standard banking logic structure.