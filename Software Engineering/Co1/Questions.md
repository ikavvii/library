This question bank for **CO1 (Software Development Methodologies & Project Estimation)** is curated based on the patterns observed across the four provided previous year papers. Following the exam structure, CO1 always constitutes **Question 1 (25 Marks)**, divided into 3-mark, 7-mark, and 15-mark subdivisions.

### **Part A: Analytical & Conceptual (3 Marks)**

_These questions typically ask for justifications, comments on software engineering principles, or the impact of management decisions._

1. **Systematic Approach Impact:** How does a systematic approach contribute to high-quality and low-cost software?
2. **Brooks' Law Commentary:** "With the addition of more people and resources, software development can help meet project deadlines if lagging behind." Justify or comment on this statement.
3. **Documentation vs. Speed:** "Practicing software engineering while developing software will tend to create voluminous documentation and this will eventually slow down the process." Provide your comments.
4. **Discipline in Engineering:** Comment on the statement: "Software engineering is the disciplined approach to designing, developing, testing, and maintaining software systems."

### **Part B: Methodologies & Life Cycle Models (7 Marks)**

_These questions focus on comparing models (especially for risk management) and the relationship between Agile and DevOps._

1. **Risk-Based Model Selection:** For a project beset with many risks, would you recommend the **Prototyping model** or the **Spiral model**? Justify your choice with specific reasons.
2. **Agile & DevOps Integration:**
    - "When you are going **Agile without DevOps**, it is like racing with a tractor instead of a car. You will waste a lot of fuel and ultimately you can do loops, but you will not move faster." Comment on the significance of DevOps in Agile environments.
    - Provide brief notes on **DevOps** and its role towards the success of large projects.
3. **Agile Fundamentals:** List the four key characteristics of **Agile Software Development**.
4. **Methodology Comparison:** Differentiate between **Agile and Waterfall** models in the context of modern software development.
5. **Lack of Process:** What specific problems might a software development team face if they do not follow any life cycle models during development?

### **Part C: Project Estimation - COCOMO & Decomposition (15 Marks)**

_This is the most critical section. It is consistently a numerical problem involving the COCOMO method or decomposition techniques._

1. **Comprehensive COCOMO Estimation (AI/Financial Focus):**
    
    - **Scenario:** An AI-powered financial analytics system with three modules: Data Processing Engine (30 KLOC), Machine Learning (50 KLOC), and Visualization Dashboard (43 KLOC).
    - **Task:** Generate estimates for total effort, duration, number of people, and total cost using specific cost drivers (e.g., High database size, Very High complexity, Very High storage constraints).
    - **Costing:** Estimate total manpower cost given a salary distribution: ₹120,000/Programmer, ₹55,000/Tester, ₹60,000/Analyst, ₹85,000/Designer, and ₹350,000 for the Project Manager.
2. **COCOMO for Inexperienced Teams (CAD Focus):**
    
    - **Scenario:** A new company developing a CAD system for the automobile industry (noted as "overall, a bit inexperienced"). Modules: Screen drawing (20 KLOC), Object-base management (3.5 KLOC), Algebra/numerical methods (1750 KLOC).
    - **Task:** Use COCOMO constants ($a=3.2, b=1.05, c=2.5, d=0.38$) and drivers (Very Low language experience, Very High complexity) to calculate effort, duration, and staff.
3. **Decomposition & Estimation:**
    
    - **Scenario:** An Organic project decomposed into 7 distinct functions.
    - **Task:** Apply decomposition techniques using an empirical equation ($C1 + C2F$) to compute total LOC.
    - **Follow-up:** Apply the COCOMO method to the derived LOC values assuming specific cost drivers (Very High skilled programmer, Low product complexity).

### **Strategic Preparation Tips for CO1**

- **Safe Scorer:** Mastering the **COCOMO formula** ($\text{Effort} = a \cdot (\text{KLOC})^b \cdot \text{EAF}$) is mandatory, as it has appeared in every paper reviewed.
- **Hardest Logic:** Be prepared to calculate **manpower cost** based on a specific team composition (analysts, designers, programmers, etc.) rather than just a flat rate.
- **Fastest Study:** Memorize the justification for using the **Spiral model for high-risk projects**, as this specific comparison is a recurring examiner favorite.