This template for a **Student Registration System** combines AWT for the user interface and JDBC for database connectivity, following the specific requirements outlined in the sources, such as using the **Event Delegation Model**, **`PreparedStatement`** to prevent SQL injection, and ensuring resources are closed properly.

### **AWT + JDBC Registration Template**

```Java
import java.awt.*;
import java.awt.event.*;
import java.sql.*;

public class StudentRegistration extends Frame implements ActionListener {
    // AWT Components
    Label lblId, lblName, lblGrade;
    TextField txtId, txtName, txtGrade;
    Button btnRegister;

    public StudentRegistration() {
        // Setup Layout
        setLayout(new GridLayout(4, 2, 10, 10));
        setTitle("Student Registration System");

        lblId = new Label("Student ID:");
        txtId = new TextField();
        lblName = new Label("Name:");
        txtName = new TextField();
        lblGrade = new Label("Grade:");
        txtGrade = new TextField();
        btnRegister = new Button("Register");

        // Event Delegation Model: Registering the listener
        btnRegister.addActionListener(this);

        add(lblId); add(txtId);
        add(lblName); add(txtName);
        add(lblGrade); add(txtGrade);
        add(new Label("")); add(btnRegister);

        setSize(400, 300);
        setVisible(true);

        // Window closing logic
        addWindowListener(new WindowAdapter() {
            public void windowClosing(WindowEvent e) { dispose(); }
        });
    }

    // Event Handling
    public void actionPerformed(ActionEvent e) {
        String id = txtId.getText();
        String name = txtName.getText();
        String grade = txtGrade.getText();

        // JDBC Connectivity
        insertStudentRecord(id, name, grade);
    }

    private void insertStudentRecord(String id, String name, String grade) {
        // Use PreparedStatement to avoid SQL Injection
        String url = "jdbc:mysql://localhost:3306/studentdb"; // Database name
        String sql = "INSERT INTO students (id, name, grade) VALUES (?, ?, ?)"; // Table structure

        // Try-with-resources ensures resources are closed properly
        try (Connection conn = DriverManager.getConnection(url, "root", "password");
             PreparedStatement pstmt = conn.prepareStatement(sql)) {

            pstmt.setInt(1, Integer.parseInt(id));
            pstmt.setString(2, name);
            pstmt.setFloat(3, Float.parseFloat(grade));

            int rows = pstmt.executeUpdate();
            if (rows > 0) {
                System.out.println("Registration Successful!");
            }
        } catch (SQLException | NumberFormatException ex) {
            ex.printStackTrace(); // Handle exceptions appropriately
        }
    }

    public static void main(String[] args) {
        new StudentRegistration();
    }
}
```

### **Key Components Explained**

1. **AWT User Interface:** The code uses components like `Label`, `TextField`, and `Button` to collect student details (ID, name, and grade) as specified for a registration application.
2. **Event Delegation Model:** The button click is handled by implementing the `ActionListener` interface and registering the button with `addActionListener(this)`. This model involves an **event source** (the button), an **event object** (the click), and an **event listener** ( the class itself).
3. **Database Integration (JDBC):**
    - **Target Database:** The program connects to a MySQL database named `studentdb` and targets a table named `students`.
    - **Security:** It utilizes `PreparedStatement` to insert records, which is specifically required by examiners to avoid **SQL injection**.
    - **Resource Management:** By using a **try-with-resources** block, the `Connection` and `PreparedStatement` are automatically closed after execution, meeting the exam requirement to ensure resources are closed properly.
4. **Exception Handling:** The code includes a `try-catch` block to manage `SQLException` (database issues) and `NumberFormatException` (invalid user input), which is essential for a robust application.