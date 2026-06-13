### **Question 2c) ii): Full Text**

**One of the common problem for Test Case Design is the Triangle Problem.**

**Triangle Problem** accepts three integers **a, b, c** as three sides of the triangle. It returns the type of triangle as **Scalene/ Isosceles/ Equilateral/ Not a Triangle** formed by a, b, c. Show the Test Case Design for the Triangle Problem using **BVA (Boundary Value Analysis)** and **Robust-based testing** methods.

Assume that the three sides of the triangle lie in the range ****. Select appropriate boundary conditions in such a way that it is covering all possible checking with respect to the Triangle problem.

**Notes:** For a, b, c to form a triangle, the following conditions should be satisfied:

- $a < b+c$
- $b < a+c$
- $c < a+b$

If any of these conditions is violated, the output is **Not a Triangle**.

- For **Equilateral Triangle**, all the sides are equal.
- For **Isosceles Triangle**, exactly one pair of sides is equal.
- For **Scalene Triangle**, all the sides are different.

---

### **Answer: Test Case Design**

To design these test cases, we identify the boundary values for the range ****:

- **Minimum (min):** 1
- **Just above min (min+):** 2
- **Nominal (nom):** 15
- **Just below max (max-):** 29
- **Maximum (max):** 30

For **Robustness Testing**, we add:

- **Below min (min-):** 0
- **Above max (max+):** 31

#### **1. Boundary Value Analysis (BVA) Test Cases**

Following the single-fault assumption ($4n+1$), we vary one side while keeping others at nominal (15).

| TC ID    | a      | b      | c      | Expected Output    | Logic                  |
| :------- | :----- | :----- | :----- | :----------------- | :--------------------- |
| **TC01** | 15     | 15     | **1**  | Isosceles          | $1 < 15+15$ (Valid)    |
| **TC02** | 15     | 15     | **2**  | Isosceles          | Valid triangle         |
| **TC03** | 15     | 15     | **15** | Equilateral        | All sides equal        |
| **TC04** | 15     | 15     | **29** | Isosceles          | $29 < 15+15$ (Valid)   |
| **TC05** | 15     | 15     | **30** | **Not a Triangle** | $30 < 15+15$ is False  |
| **TC06** | 15     | **1**  | 15     | Isosceles          | Boundary check for $b$ |
| **TC07** | 15     | **2**  | 15     | Isosceles          | Boundary check for $b$ |
| **TC08** | 15     | **29** | 15     | Isosceles          | Boundary check for $b$ |
| **TC09** | 15     | **30** | 15     | **Not a Triangle** | $30 < 15+15$ is False  |
| **TC10** | **1**  | 15     | 15     | Isosceles          | Boundary check for $a$ |
| **TC11** | **2**  | 15     | 15     | Isosceles          | Boundary check for $a$ |
| **TC12** | **29** | 15     | 15     | Isosceles          | Boundary check for $a$ |
| **TC13** | **30** | 15     | 15     | **Not a Triangle** | $30 < 15+15$ is False  |

#### **2. Robustness Test Cases**

These test values outside the valid range to ensure the system handles invalid data.

| TC ID    | a      | b      | c      | Expected Output | Logic     |
| :------- | :----- | :----- | :----- | :-------------- | :-------- |
| **TC14** | 15     | 15     | **0**  | Invalid Input   | Side < 1  |
| **TC15** | 15     | 15     | **31** | Invalid Input   | Side > 30 |
| **TC16** | 15     | **0**  | 15     | Invalid Input   | Side < 1  |
| **TC17** | 15     | **31** | 15     | Invalid Input   | Side > 30 |
| **TC18** | **0**  | 15     | 15     | Invalid Input   | Side < 1  |
| **TC19** | **31** | 15     | 15     | Invalid Input   | Side > 30 |

#### **3. Additional Logical Coverage (To satisfy "covering all possible checking")**

While BVA focuses on ranges, testing the triangle logic requires specific combinations.

| TC ID    | a   | b   | c   | Expected Output | Logic                        |
| :------- | :-- | :-- | :-- | :-------------- | :--------------------------- |
| **TC20** | 12  | 13  | 14  | Scalene         | All sides different          |
| **TC21** | 5   | 5   | 5   | Equilateral     | Min-range equilateral        |
| **TC22** | 2   | 2   | 5   | Not a Triangle  | Sum of two sides ($2+2$) < 5 |
