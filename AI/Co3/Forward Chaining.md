Apply **forward chaining reasoning** to a simple weather forecast rule set (e.g., pressure, clouds, cyclones) to predict weather status.

Forward chaining is a **data-driven (bottom-up)** reasoning strategy that starts with a known fact and applies inference rules to derive new information until a goal is reached.

### **1. The Weather Forecast Rule Set**

- **Rule 1:** If anticyclone, then clear sky.
- **Rule 2:** If cyclone, then clouds.
- **Rule 3:** If pressure is low, then cyclone.
- **Rule 4:** If pressure is high, then anticyclone.
- **Rule 5:** If arrow is down, then pressure is low.
- **Rule 6:** If arrow is up, then pressure is high.

### **2. Forward Chaining Trace**

Given the initial fact that the **"arrow is down"**, the algorithm proceeds through the following logical steps to reach a conclusion:

1. **Start with the Fact:** The system identifies the initial fact: **"arrow is down"**.
2. **Apply Rule 5:** Since the arrow is down, Rule 5 triggers ("If arrow is down, then pressure is low").
    - _New Derived Fact:_ **Pressure is low**.
3. **Apply Rule 3:** The system now searches for rules where "pressure is low" is the condition. Rule 3 triggers ("If pressure is low, then cyclone").
    - _New Derived Fact:_ **Cyclone**.
4. **Apply Rule 2:** The system searches for rules where "cyclone" is the condition. Rule 2 triggers ("If cyclone, then clouds").
    - _New Derived Fact:_ **Clouds**.

### **3. Final Prediction**

Through the forward chaining process, the system concludes that the current weather status is **"clouds"**.