### **Question 2c) i): Full Text**

**A GOLD vending machine problem is explained as follows:** This machine is similar to ATM – it is a vending machine to buy gold coins; each coin weighs 1 gram.

- Customer apply for a GOLD card to access this machine. Gold card with sealed PIN is dispatched to the customer. Customer uses this card for purchasing GOLD coin from the machine.
- Customer scans the card in the machine; it validates the card and asks for the PIN.
- Customer enters the PIN.
- Machine displays the current rate of a coin.
- Customer enter the number of coins interested to buy.
- Machine calculates and displays the amount to be paid by the customer after adding **18% as GST**.
- If the customer is interested to buy, he/she presses the **“BUY”** button or **“CANCEL”** button to cancel the transaction.
- Machine asks for the mode of payment **[Cash/ Card]**.
- If the customer decided to pay **CASH**, machine accepts the same; checks the cash inserted in the machine; dispense the Gold coins along with the balance if any and a receipt.
- Otherwise, machine reads the Card inserted by the customer; debit the amount from the card and dispense the Gold coins and a receipt.
- Machine also handles any queries from the customer.

**Write sufficient number of test cases required to test this Gold Vending Machine problem using Black Box Testing approach. Assume the values required for the problem.**.

---

### **Answer: Black Box Test Cases**

To design these test cases, we assume a **Gold Rate of ₹7,000 per gram** and a **Daily Purchase Limit of 10 coins**.

|TC ID|Test Scenario|Input Data|Expected Output|
|:--|:--|:--|:--|
|**TC01**|**Invalid Card**|Insert expired or damaged card|Display "Invalid Card" and eject.|
|**TC02**|**Invalid PIN**|Correct Card + Wrong PIN|Display "Incorrect PIN. Please try again".|
|**TC03**|**Transaction Cancellation**|Valid Card/PIN + Press "CANCEL"|System terminates and returns to the home screen.|
|**TC04**|**GST Calculation**|Buy 2 coins (Rate: 7000)|Display total: ₹16,520 (Base: 14000 + 18% GST).|
|**TC05**|**Cash Payment (Exact)**|Total: ₹16,520; Insert: ₹16,520|Dispense 2 coins and a receipt.|
|**TC06**|**Cash Payment (Balance)**|Total: ₹16,520; Insert: ₹17,000|Dispense 2 coins, ₹480 change, and a receipt.|
|**TC07**|**Cash (Insufficient)**|Total: ₹16,520; Insert: ₹10,000|Display "Insufficient Cash" and return money.|
|**TC08**|**Card Payment (Success)**|Total: ₹16,520; Card Balance: ₹50,000|Debit ₹16,520; Dispense 2 coins and receipt.|
|**TC09**|**Card Payment (Fail)**|Total: ₹16,520; Card Balance: ₹5,000|Display "Transaction Declined: Low Balance".|
|**TC10**|**Boundary (Zero)**|Enter Quantity: 0|Display "Error: Please enter a valid quantity".|
|**TC11**|**Boundary (Limit)**|Enter Quantity: 11 (Limit: 10)|Display "Error: Exceeds daily purchase limit".|
|**TC12**|**Customer Query**|Select "Check Gold Rate"|Display current price per gram.|

#### **Testing Methodologies Used:**

1. **Equivalence Partitioning:** Dividing inputs into valid (1-10 coins) and invalid (0 or 11+ coins) groups.
2. **Boundary Value Analysis (BVA):** Testing the minimum (1 coin) and maximum (10 coins) limits.
3. **Error Guessing:** Testing scenarios like insufficient cash or low bank balance.