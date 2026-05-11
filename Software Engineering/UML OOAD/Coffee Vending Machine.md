### **Question 1c: Full Text**

**Design a neat Sequence and Collaboration Diagram to depict the Coffee Vending Machine explained below.**

**Coffee machine interface** consists of a GUI, a coin slot for accepting change & returning change, a slot for delivering the cup of drink and selection buttons for coffee and tea.

The coffee machine can handle coins of the values 5 and 10, where 5 is the price for a cup of tea and 10 is the price for a cup of coffee. Internally, the coffee machine consists of a **change verification device** that counts money and makes change.

- If a coin with the value of 10 is inserted and the **Coffee** button is pressed - the customer receives a cup of coffee.
- If a coin with the value of 5 is inserted and the **Tea** button is pressed - the customer receives a cup of tea.
- If a coin with the value of 10 is inserted and the **Tea** button is pressed - the customer receives a cup of tea and the change.
- If a coin with the value of 5 is inserted and the **Coffee** button is pressed - the money is returned.

---

### **Answers**

#### **1. Sequence Diagram**

This diagram shows the time-ordered interaction between the Customer and the system components.

![](attachments/Pasted%20image%2020260511210655.png)

#### **2. Collaboration Diagram (Communication Diagram)**

This diagram focuses on the structural organization of the objects that send and receive messages. Messages are numbered to show the sequence of events.


![](attachments/Pasted%20image%2020260511210721.png)

```
@startuml
title Collaboration Diagram: Coffee Vending Machine flow

object ":Customer" as C
object ":Coin Slot" as CS
object ":Change Verification Device" as CVD
object ":GUI" as G
object ":Selection Buttons" as B
object ":Delivery Slot" as DS

' Relationships and numbered messages
C -right-> CS : 1: Insert Coin() / 8: Receive Change()
CS -right-> CVD : 2: ValidateValue() / 7: ReturnChange()
CVD -up-> G : 3: DisplayBalance()
C -down-> B : 4: PressSelection()
B -right-> CVD : 5: ProcessRequest()
CVD -down-> DS : 6: DispenseDrink()
DS -left-> C : 9: ReceiveDrink()

@enduml
```
### **Explanation of Logic**

- **Objects:** The system is decomposed into the **GUI** (for user feedback), **Coin Slot** (input/output of money), **Change Verification Device** (the "brain" that handles logic and GST/change), **Selection Buttons**, and the **Delivery Slot**.
- **Process Flow:** The process always begins with a coin insertion, followed by validation by the internal change device. The user then makes a selection.
- **Conditional Logic:**
    - **Direct Match:** If the coin matches the price (10 for Coffee or 5 for Tea), only the drink is dispensed.
    - **Change Case:** If 10 is inserted for a 5-unit Tea, the change device must trigger both the delivery slot and the coin slot (to return 5).
    - **Failure Case:** If 5 is inserted for a 10-unit Coffee, the logic dictates the money is simply returned through the coin slot.