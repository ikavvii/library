**14 types of UML diagrams**, which are broadly categorized into two main groups: **Structural Diagrams** and **Behavioral Diagrams**.

### **1. Structural Diagrams (7 Types)**

These diagrams represent the **static architecture** of a system. They focus on the things/**objects** that make up the system and how they are connected.

- **Class Diagram:** The main building block showing classes, attributes, operations, and their relationships.
- **Component Diagram:** Displays the structural relationships between physical software components and their interfaces.
- **Deployment Diagram:** Visualizes the hardware nodes and the software components (executables, databases) deployed on them.
- **Object Diagram:** Also known as an Instance diagram, it shows a "snapshot" of the system at a specific moment in time using real-world examples.
- **Package Diagram:** Illustrates how different packages (logical groupings of code) depend on one another.
- **Profile Diagram:** A newer diagram type used to extend or customize existing UML metamodels for specific domains.
- **Composite Structure Diagram:** Shows the internal structure of a class and how different parts collaborate through ports and connectors.

### **2. Behavioral Diagrams (7 Types)**

These diagrams illustrate the **dynamic aspects** of a system, describing what should happen and how objects collaborate and change state over time.

- **Use Case Diagram:** Provides a high-level overview of actors, the functions (use cases) they need, and their interactions.
- **Activity Diagram:** Illustrates the flow of control, sequential activities, and concurrent workflows in a process.
- **State Machine Diagram:** (Or State chart) Describes the discrete behavior of an object as it transitions through finite states based on events.

#### **Interaction Diagrams (Sub-category of Behavioral)**

>Focus on the flow of messages between objects.

- **Sequence Diagram:** Depicts object interactions in a time-ordered sequence, showing when messages are sent.
- **Communication Diagram:** (Called a **Collaboration Diagram** in UML 1.x) Focuses on which objects participate in an interaction and the organization of the messages passed between them.
- **Interaction Overview Diagram:** A combination of an activity diagram and sequence diagrams, showing a sequence of interaction-based processes.
- **Timing Diagram:** Describes the behavior of objects within a specific timeframe, emphasizing how state changes relative to time.