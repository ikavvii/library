### **Demonstration of Vulnerability: Standard `Statement` Object**

A standard `Statement` object is vulnerable to **SQL injection** because it typically uses string concatenation to build dynamic SQL queries with user-supplied input. In a university student portal login scenario, a developer might write code like this:

```
// Vulnerable Code Example
String query = "SELECT * FROM users WHERE username = '" + userProvidedName + "' AND password = '" + userProvidedPassword + "'";
Statement stmt = connection.createStatement();
ResultSet rs = stmt.executeQuery(query);
```

**How the Vulnerability is Exploited:** An attacker can input malicious SQL fragments into the login fields. For instance, if the attacker enters `' OR '1'='1` in the username field, the resulting query executed by the database becomes: `SELECT * FROM users WHERE username = '' OR '1'='1' AND password = '...'`

Because the condition `'1'='1'` is always true, the database will return a valid record regardless of the actual username or password, granting the attacker **unauthorized access**. This demonstrates how user input can manipulate the original intent of the SQL command, leading to severe security breaches.

---

### **Security Redesign: Using `PreparedStatement`**

To ensure security, the login process must be redesigned using a **`PreparedStatement`**. This object allows for the execution of **parameterized queries**, which effectively mitigates SQL injection risks.

**The Redesigned Login Logic:** Instead of concatenating strings, the SQL query is defined with **placeholders (`?`)**. The structure of the query is sent to the database and **pre-compiled** before any user data is added.

```
// Secure Redesigned Code
String sql = "SELECT * FROM students WHERE username = ? AND password = ?";
PreparedStatement pstmt = connection.prepareStatement(sql);

// Set values safely as parameters
pstmt.setString(1, userProvidedName);
pstmt.setString(2, userProvidedPassword);

ResultSet rs = pstmt.executeQuery();
```

**Why this Redesign is Secure:**

1. **Separation of Code and Data:** The database treats the values passed via `setString()` strictly as **literals (data)** rather than executable SQL code.
2. **Input Neutralization:** If an attacker attempts to input `' OR '1'='1`, the `PreparedStatement` will look for a username that literally matches the string `' OR '1'='1`, rather than executing it as a logical command.
3. **Prevention Solution:** This is the primary solution provided by the JDBC API to prevent injection attacks and ensure the integrity of enterprise data enabling.