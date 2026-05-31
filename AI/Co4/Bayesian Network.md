A **Bayesian Network** is a probabilistic graphical model used to tackle AI problems that deal with **uncertain knowledge** by representing dependencies between variables. It is composed of two primary components: the **Directed Acyclic Graph (DAG)** and the **Conditional Probability Table (CPT)**.
 
### **1. Directed Acyclic Graph (DAG)**

The DAG represents the **qualitative** structure of the Bayesian Network, providing a visual map of how different variables relate to one another.

- **Role:**
    - **Nodes:** Each node in the graph represents a random variable (e.g., "Cloudy", "Rains", or "Wet Grass").
    - **Directed Edges:** The arrows (edges) between nodes represent **probabilistic dependencies** or causal influences. For example, an arrow from "Cloudy" to "Rains" indicates that cloudy weather directly influences the probability of rain.
- **Importance:**
    - **Acyclic Nature:** The "Acyclic" requirement is critical because it ensures there are **no feedback loops**. This allows for a clear, one-way flow of influence, which is necessary for calculating joint probabilities without logical contradictions.
    - **Conditional Independence:** The DAG simplifies complex environments by identifying which variables are independent of others, significantly reducing the amount of data needed to model the system.

### **2. Conditional Probability Table (CPT)**

While the DAG provides the structure, the CPT provides the **quantitative** data necessary for reasoning and inference.

- **Role:**
    - Every node in the network has an associated CPT.
    - For **Root Nodes** (those without parents), the CPT contains **Prior Probabilities**, such as $P(C) = 0.002$ for "Cloudy" weather.
    - For **Child Nodes**, the CPT lists the probability of that variable occurring for **every possible combination** of its parents' states. For instance, the CPT for "Wet Grass" ($WG$) specifies probabilities based on whether "Rains" ($R$) is True or False.
- **Importance:**
    - **Quantifying Uncertainty:** The CPT allows the system to move beyond simple "Yes/No" logic to "How likely" logic. It captures the strength of the relationship between variables (e.g., there is a 0.95 probability of wet grass if it rains, but still a 0.05 probability even if it doesn't).
    - **Enabling Inference:** By combining the DAG structure with CPT values, AI agents can perform complex calculations to find the **posterior probability** of an event (like the probability of having wet grass given specific weather conditions).

### **Summary of Interaction**

The **DAG** defines the **architecture of influence**, while the **CPT** provides the **numerical weight** of that influence. Together, they allow an agent to reason about uncertain environments—such as predicting if someone will be late from work based on various atmospheric or industrial factors—by chaining probabilities through the network.


A **Bayesian Network** is a probabilistic graphical model used in Artificial Intelligence to represent and reason about uncertain knowledge by modeling the dependencies between random variables.

### **1. Structure of a Bayesian Network**

The structure is defined by two primary components that work together to simplify complex joint probability distributions:

- **Directed Acyclic Graph (DAG):**
    - **Nodes:** Each node represents a random variable in the domain (e.g., weather conditions or agent actions).
    - **Directed Edges:** Arrows between nodes represent **probabilistic dependencies** or causal influences. For example, an arrow from "Rains" to "Wet Grass" indicates that rain directly affects the state of the grass.
    - **Acyclic Requirement:** The graph must be "acyclic," meaning there are **no feedback loops** or cycles. This ensures a clear directional flow of influence necessary for consistent probabilistic inference.
- **Conditional Probability Tables (CPT):**
    - Each node has an associated CPT that quantifies the relationship between the node and its parents.
    - **Root Nodes:** Nodes without parents (like "Cloudy") contain **prior probabilities**—the likelihood of the variable occurring without any other information.
    - **Child Nodes:** Nodes with parents contain **conditional probabilities** for every possible combination of their parents' states.

---

### **2. Analysis of the Provided Network (Figure 6)**

Based on the network shown in the sources, the environment involves four interconnected variables:

- **The DAG Structure:**
    - **CLOUDY (C)** is the root node.
    - **RAINS (R)** is a child of CLOUDY ($C \rightarrow R$).
    - **WET GRASS (WG)** is a child of RAINS ($R \rightarrow WG$).
    - **TAKE OFF FROM WORK (W)** is a child of RAINS ($R \rightarrow W$).
- **The Parameters (CPTs):**
    - **Prior for Cloudy:** $P(C) = 0.002$.
    - **CPT for Rains:** The probability of rain given cloudy weather is provided as $P(R|C) = 0.95$ and $P(R|\neg C) = 0.001$ (based on the provided FF value in the associated table).
    - **CPT for Wet Grass:** $P(WG|R) = 0.95$ and $P(WG|\neg R) = 0.05$.
    - **CPT for Take Off From Work:** $P(W|R) = 0.99$ and $P(W|\neg R) = 0.01$.

---

### **3. Calculation: Probability of Having Wet Grass**

To find the marginal probability of **Wet Grass** ($P(WG)$), we must account for the uncertainty of its ancestor nodes (Rains and Cloudy) using the **Chain Rule of Probability**.

**Step 1: Calculate the probability of Rain ($P(R)$)** We use the prior for Cloudy and its influence on Rain: $$P(R) = [P(R|C) \cdot P(C)] + [P(R|\neg C) \cdot P(\neg C)]$$ $$P(R) = (0.95 \cdot 0.002) + (0.001 \cdot 0.998) = 0.0019 + 0.000998 = \mathbf{0.002898}$$

**Step 2: Calculate the probability of Wet Grass ($P(WG)$)** We use the newly calculated probability of Rain and its influence on the grass: $$P(WG) = [P(WG|R) \cdot P(R)] + [P(WG|\neg R) \cdot P(\neg R)]$$ $$P(WG) = (0.95 \cdot 0.002898) + (0.05 \cdot 0.997102)$$ $$P(WG) = 0.0027531 + 0.0498551 = \mathbf{0.0526082}$$

**Final Result:** Based on the Bayesian Network analysis, the overall probability of having **Wet Grass** in this environment is approximately **5.26%**. Even when it is not raining, the 5% baseline probability (perhaps from dew or other factors) contributes significantly to the final outcome given that the prior for cloudy weather is very low.