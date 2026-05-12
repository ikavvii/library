![](attachments/Pasted%20image%2020260511065311.png)

A **Sequence Diagram** is a type of behavioral UML diagram that depicts interactions between objects in the specific order in which they take place. Also known as **event diagrams** or **event scenarios**, they describe how and in what order various objects in a system function to complete a task.

### 1. Key Features and Purpose

- **Sequential Order:** The primary focus is the chronological order of interactions.
- **Time Representation:** Time is represented **vertically**, progressing from top to bottom.
- **Usage:** These diagrams are widely used by both business stakeholders and software developers to document and understand requirements for new or existing systems.
- **Focus:** They emphasize the **order and timing** of messages between objects rather than the physical relationships between them.

### 2. Core Components and Notations

- **Objects and Lifelines:** Objects are represented at the top of the diagram, each with a **vertical lifeline** extending downwards.
- **Messages:** Horizontal arrows between lifelines represent the communication or "messages" sent between objects.
- **Activation Time:** A thin rectangle on the lifeline indicates the period during which an object is performing an action.
- **Fragments:** Sequence diagrams can include logic such as **loops** (e.g., "for each item") or **alternative paths** (e.g., a path for successful login vs. a path for failed login).

### 3. Comparisons with Other Diagrams

- **Collaboration (Communication) Diagram:** These are "isomorphic" to sequence diagrams, meaning they contain the same information but organized differently. While sequence diagrams focus on **time-driven order**, collaboration diagrams emphasize the **organization and structure** of object relationships.
- **Activity Diagram:** An activity diagram shows the flow of control and steps in a process (similar to a flowchart), whereas a sequence diagram focuses specifically on **object-to-object interaction** over time.
- **Interaction Overview Diagram:** This is a higher-level diagram that uses frames to group different interaction diagrams (like sequence diagrams) together to simplify complex scenarios.

### 4. Examples

The sources highlight several scenarios where sequence diagrams are applied:

- **User Login:** Depicting the user entering credentials, the login page sending data to a database, and the database returning an "accepted" or "incorrect" message.
- **Vending Machines:** Modeling interactions for a **Gold Vending Machine** (scanning cards, PIN entry, payment) and an **Automated Coffee Vending System** involving a Customer, Vending Machine, Payment Processor, and Inventory System.
- **Restaurant Service:** A simple flow where a **Customer** orders from a **Waiter**, who communicates with the **Kitchen**, followed by food service and payment.
- **Shipment Processing:** Showing a loop that checks the status of multiple items before shipping goods and sending an invoice.
