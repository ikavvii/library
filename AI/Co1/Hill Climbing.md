**Hill Climbing** is a heuristic search that follows a path of increasing value to find an optimum. However, this algorithm frequently encounters three major **pitfalls** that can prevent it from reaching the global maximum.

The following explanations and solutions are based on standard Artificial Intelligence academic principles, as the provided sources identify this as a required exam topic but do not contain the descriptive answers within their text:

### **1. Local Maxima**

- **Description:** A **Local Maximum** is a peak that is higher than all its immediate neighboring states but is **lower than the global maximum**. Since the algorithm only moves "upward," it gets stuck at this sub-optimal point because any move it takes will lead to a lower value.
- **Solution:** The most common solution is **Random Restart Hill Climbing**, where the algorithm is restarted from a completely different random initial state. This increases the probability of eventually starting in a region that leads to the global optimum.

### **2. Plateaus**

- **Description:** A **Plateau** (or "flat local maximum") is an area of the state space where the evaluation function is essentially **flat**. In this scenario, all neighboring states have the same value, providing the algorithm with no "uphill" direction to follow.
- **Solution:** This can be solved by allowing the agent to take a **Random Walk**. By moving to a neighbor that has the same value as the current state, the agent may eventually find a way out of the flat region toward a new incline.

### **3. Ridges**

- **Description:** A **Ridge** is a challenging area where the state space consists of a sequence of local maxima that are very close together. Because the ridge itself may be sloped, the algorithm may see every individual move (e.g., North, South, East, West) as a "downhill" move even though moving diagonally would be "uphill".
- **Solution:** To navigate a ridge, the algorithm can be modified to **move in multiple directions simultaneously** or use more complex search techniques that allow for a broader exploration of the neighborhood.

### **Exam Context**

- **Preparation Tip:** When answering this in the exam, **sketching a small graph** for each pitfall (a single peak for Local Maxima, a flat line for Plateaus, and a jagged line for Ridges) is highly recommended to secure full marks.