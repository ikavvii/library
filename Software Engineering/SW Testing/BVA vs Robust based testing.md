The primary difference between **Boundary Value Analysis (BVA)** and **Robust-based testing** lies in the range of input values they cover and their testing objectives.

### **1. Boundary Value Analysis (BVA)**

- **Focus:** BVA is a black-box testing technique that focuses on the **boundaries of the input domain**. It is based on the principle that errors are more likely to occur at the extreme ends of a range rather than in the middle.
- **Input Values:** For a given range $[min, max]$, BVA typically uses five specific values for each variable:
    - **Minimum (min)**.
    - **Just above minimum (min+)**.
    - **Nominal (nom)** (a value in the middle of the range).
    - **Just below maximum (max-)**.
    - **Maximum (max)**.
- **Goal:** To verify that the system correctly handles **valid boundary conditions**.

### **2. Robust-based Testing**

- **Focus:** Robustness testing is an **extension of BVA**. While BVA only looks at valid values, Robust-based testing checks how the system reacts to **invalid or out-of-range inputs**.
- **Input Values:** It includes the five values used in BVA plus two additional **invalid** values:
    - **Below the minimum (min-)**.
    - **Above the maximum (max+)**.
- **Goal:** To ensure the system is "robust," meaning it can gracefully handle and reject **illegal inputs** without crashing.

---

### **Comparison Example: The Triangle Problem**

If you are testing the "Triangle Problem" where the sides $a, b, c$ must be in the range ****:

|Feature|BVA Approach|Robust Approach|
|:--|:--|:--|
|**Valid Values Tested**|1, 2, 15 (nominal), 29, 30.|1, 2, 15, 29, 30.|
|**Invalid Values Tested**|None.|**0** (min-) and **31** (max+).|
|**Primary Check**|Does the code distinguish between Scalene, Isosceles, and Equilateral at the edges?.|Does the code trigger an **error message** or "Invalid Input" for 0 or 31?.|

In summary, while BVA ensures the software works correctly within its defined limits, **Robust-based testing** verifies that the software does not fail when those limits are exceeded.