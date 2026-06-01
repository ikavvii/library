The design of a **Data Access Layer (DAL)** for a banking system—specifically one supporting a **CORE (Centralized Online Real-time Environment)**—is centered on providing a secure, reliable, and integrated interface between the business logic and the centralized datastore.

### **Data Access Layer Design for Banking**

The DAL is structured using the standard **JDBC application architecture**, which consists of the Java Application, the JDBC API, the Driver Manager, a specific JDBC Driver, and the Database. For a banking system handling account creation, deposits, and withdrawals, the layer follows a specific **flow of object creation**: `Connection` $\rightarrow$ `Statement` or `PreparedStatement` $\rightarrow$ `ResultSet`.

- **Centralized Datacenter:** To ensure that deposits are "reflected immediately" and accessible across all global branches, the DAL must connect to a centralized enterprise database.
- **Security Integration:** The design must utilize **`PreparedStatement`** objects rather than standard `Statement` objects to neutralize the risk of **SQL injection**, which is critical for protecting sensitive financial credentials.
- **Performance Optimization:** For high-traffic banking interactions (e.g., thousands of concurrent requests from ATMs and mobile apps), the DAL should implement **Connection Pooling** to manage database connections efficiently.

---

### **Implementation of CRUD Operations using JDBC**

In a banking context, CRUD (Create, Read, Update, Delete) operations translate directly to core financial services like account management and transaction processing.

1. **Create (Account Creation):**
    
    - **Implementation:** Uses the `executeUpdate()` method with an `INSERT` SQL statement to add new customer records to the database.
    - **Justification:** Using JDBC for this increases the **longevity of the code** compared to embedded forms like SQLJ, making the system easier to maintain as the bank's requirements evolve.
2. **Read (Real-time Balance Display):**
    
    - **Implementation:** Uses the **`executeQuery()`** method to retrieve data, which returns a **`ResultSet`** object containing the current balance.
    - **Justification:** This method is functionally designed for data retrieval and allows the application to present the most current data from the "centralized online real-time environment".
3. **Update (Deposits and Withdrawals):**
    
    - **Implementation:** Uses `executeUpdate()` to modify the balance column in the database.
    - **Justification:** For multi-step updates (e.g., transferring funds between accounts), the DAL must support **Distributed Transactions**. This ensures **atomicity**, meaning that if a withdrawal succeeds but the corresponding deposit fails, the entire transaction is rolled back to maintain data consistency.
4. **Delete (Account Closure):**
    
    - **Implementation:** Uses `executeUpdate()` with a `DELETE` or `UPDATE` (soft delete) statement to deactivate accounts.

---

### **Architectural Justifications**

- **Separation of Concerns (SoC):** By isolating database logic within the DAL, the bank maintains **departmental autonomy**. For example, the "Loans" department can update its internal data logic without disrupting the "Savings" or "ATM" modules.
- **Security and Integrity:** The use of **`PreparedStatement`** is a mandatory architectural choice to prevent SQL injection by treating user input strictly as data parameters rather than executable code.
- **Scalability:** In high-traffic e-commerce or banking platforms, the architecture uses **Connection Pooling** to handle thousands of concurrent customer requests, preventing the system from crashing during peak hours.
- **Reliability:** **Distributed Transactions** provide the necessary framework for multi-step orders or banking transfers, ensuring that the system functions as a "coherent whole" where no data is lost or fragmented during complex operations.