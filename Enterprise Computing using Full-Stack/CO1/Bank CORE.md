To sketch a **Bank CORE (Centralized Online Real-time Environment)** architecture effectively for an enterprise computing exam, you should focus on creating a **multi-tier, centralized model** that integrates fragmented systems into a coherent whole.

Based on the sources, the best approach is to structure your sketch around the following layers and components:

### 1. Presentation Layer (Access Channels)

This is the top tier of your diagram, representing how customers and staff interact with the bank. You should include:

- **Multiple Service Channels:** Explicitly draw and label channels such as **ATMs, Internet Banking, and physical regional branches**.
- **Client Programs:** Note that these channels handle the interaction with users and should be flexible to support various client programs.

### 2. Business Logic Layer (Centralized Service Modules)

The core of the architecture should be a **centralized datacenter** that houses the business logic. Your sketch should show distinct modules for different banking functions to demonstrate **Separation of Concerns** and **departmental autonomy**. Key modules to include are:

- **Deposit/Savings Accounts**.
- **Loan and Mortgage Management**.
- **Credit Card Transactions**.
- **ATM Services and Payment Processing**.

### 3. Data Layer (Centralized Datastore)

At the bottom tier, indicate a **centralized database or datacenter**.

- **Real-time Processing:** The sketch should imply a "Real-time" flow where actions (like a deposit) are reflected immediately on the bank's servers, allowing for instant updates across all global branches.
- **Integration:** This layer must show how disparate, previously fragmented applications (like separate loan and savings databases) are now integrated into a **coherent whole**.

### 4. Architectural Principles to Highlight

To ensure your sketch meets exam requirements for a "Full Stack" or "Enterprise" architecture, you should incorporate:

- **Separation of Concerns (SoC):** Clearly define the boundaries between the UI (Presentation), the processing logic, and the database to simplify development and maintenance.
- **Modularity:** Ensure the design allows for autonomous departmental updates without disrupting the entire system.
- **Security and Interoperability:** Mention or illustrate the use of **middleware** and **frameworks** (like Spring Boot or MERN/MEAN stacks) to ensure secure and efficient service delivery.

### Recommended Visual Flow

1. **Top:** Users/Customers $\rightarrow$ Channels (ATM, Web, Branch Terminals).
2. **Middle:** API Gateway/Middleware $\rightarrow$ Centralized Business Logic Modules (Loans, Savings, etc.).
3. **Bottom:** Centralized Enterprise Database (Real-time synchronization).

By following this multi-tier structure, you demonstrate a clear understanding of the **CORE banking definition**: a centralized environment where branches access applications from a single datacenter to provide a comprehensive banking solution.