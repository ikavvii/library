The question paper for **Continuous Assessment Test - 2 (CA 2)** for the course **23MX23 - Object Oriented Programming Using Java**, here are the extracted questions:

### **Question 1**

**a)** How does `DataInputStream` differ from `ObjectInputStream` in terms of functionality, purpose, serialization, and available methods for file management? **(3 Marks) [L3]**

**b) i)** What is the purpose of `BufferedInputStream` and `BufferedReader` in Java, and in which scenarios should each be used? **(3 Marks) [L2]**

**b) ii)** How does `FileReader` differ from `BufferedReader` in terms of functionality and performance? Create a Java code snippet that reads content from an input file named `inp.txt` using the `FileReader` class and writes the content into an output file named `out.txt` using the `FileWriter` class. **(7 Marks) [L5]**

**c) i)** Differentiate between **Process-Based Multitasking** and **Thread-Based Multitasking**, and between **Single-Threaded** and **Multi-Threaded Systems** with respect to key points like resource usage, communication, execution, and performance. Illustrate the **life cycle of a thread** in Java with a diagram, and provide a brief description of each thread state using an example code snippet. **(12 Marks) [L5]**

**OR**

**c) ii)** Design a Java code that demonstrates how to run **multiple tasks using multiple threads** (three different tasks using three different threads). Each thread will be responsible for its own task only. Among these three threads:

- One will find the **median** of the input numbers.
- One will find the **greatest number** from the input array of numbers.
- One will find the **smallest number** from the input array of numbers. **(12 Marks) [L5]**

---

### **Question 2**

**a)** Analyze the given code and alter the program by including the required line of code(s) appropriately to set the **frame surface colour to blue**.

```
import java.awt.*;
public class SetF extends Frame {
    public static void main(String argv[]) {
        SetF s = new SetF();
        s.setSize(300,200);
        s.setVisible(true);
    }
}
```

**(4 Marks) [L3]**

**b) i)** Describe the steps involved in establishing a **JDBC connection** and executing SQL queries. **(4 Marks) [L3]**

**b) ii)** Analyze the following Java Code for its functionality and answer the below questions: **(6 Marks) [L4]**

```
import java.util.*;
class Pair<T, U> {
    private T first;
    private U second;
    public Pair(T first, U second) {
        this.first = first;
        this.second = second;
    }
    public T getFirst() { return first; }
    public U getSecond() { return second; }
    public String toString() { return first + " and " + second; }
}
public class GenericTest {
    public static void main(String[] args) {
        Pair<String, Integer> pair1 = new Pair<>("Age", 25);
        Pair<String, Double> pair2 = new Pair<>("Height", 5.9);
        System.out.println(pair1);
        System.out.println(pair2);
        List<Pair<?, ?>> pairList = new ArrayList<>();
        pairList.add(pair1);
        pairList.add(pair2);
        for (Pair<?, ?> pair : pairList) {
            System.out.println(pair.getFirst() + " is " + pair.getSecond());
        }
    }
}
```

- **w)** What is the purpose of the `Pair<T, U>` class in this code?
- **x)** How are generics being used in the `Pair` class and its `getFirst()` and `getSecond()` methods?
- **y)** What is the significance of `Pair<?, ?>` in the `pairList` declaration?
- **z)** What will be the output of this program when executed? Explain the reason behind it.

**c)** With a diagram explain the **Event Delegation Model** in Java AWT. What are the roles of `EventListener`, `EventObject`, and `EventSource` in this model? Illustrate with an example of handling a **button click event** in AWT. **(12 Marks) [L5]**


The following are comprehensive solutions for the Continuous Assessment Test - 2 (CA 2) based on the provided source materials.

---

### **Question 1**

#### **a) How does DataInputStream differ from ObjectInputStream in terms of functionality, purpose, serialization, and available methods for file management?**

- **Purpose and Functionality:** `DataInputStream` is designed to read primitive Java data types (such as `int`, `double`, `boolean`) from an underlying input stream in a machine-independent way. `ObjectInputStream`, however, is used for **deserialization**, which is the process of reading entire objects and graphs of objects previously written using `ObjectOutputStream`.
- **Serialization:** `ObjectInputStream` requires the classes of the objects being read to implement the `Serializable` interface. `DataInputStream` does not deal with object serialization; it simply reads raw binary representations of primitives.
- **Available Methods:**
    - **DataInputStream:** Includes methods like `readInt()`, `readDouble()`, `readBoolean()`, and `readUTF()`.
    - **ObjectInputStream:** Its primary method is `readObject()`, which returns an `Object` that must be cast back to its original type.

#### **b) i) What is the purpose of BufferedInputStream and BufferedReader in Java, and in which scenarios should each be used?**

- **Purpose:** Both classes are used to improve I/O performance by wrapping other streams and providing an internal **buffer**. Instead of calling the operating system for every single byte or character, they read large chunks into memory at once.
- **Scenarios for Use:**
    - **BufferedInputStream:** This is a **byte stream**. It should be used when handling raw binary data, such as images, audio, video, or encrypted files.
    - **BufferedReader:** This is a **character stream**. It should be used when processing human-readable text files (like `.txt`, `.csv`, or `.java` files) because it handles 16-bit Unicode characters and provides the convenient `readLine()` method.

#### **b) ii) How does FileReader differ from BufferedReader in terms of functionality and performance? Create a Java code snippet that reads content from an input file named inp.txt using the FileReader class and writes the content into an output file named out.txt using the FileWriter class.**

- **Differences:** `FileReader` is a basic character stream that reads a file character by character without internal buffering. `BufferedReader` wraps a `Reader` (like `FileReader`) to provide a buffer, making it significantly faster (~100x) for large files because it minimizes expensive disk access.
- **Java Code Snippet:**

```
import java.io.*;

public class FileCopy {
    public static void main(String[] args) {
        // Character streams for reading/writing text
        try (FileReader fr = new FileReader("inp.txt");
             FileWriter fw = new FileWriter("out.txt")) {

            int ch;
            // Read until end of file (-1)
            while ((ch = fr.read()) != -1) {
                fw.write(ch);
            }
            System.out.println("File copy complete.");
        } catch (IOException e) {
            System.err.println("I/O Error: " + e.getMessage());
        }
    }
}
```

_(Based on character stream examples in)_

#### **c) i) Differentiate between Process-Based and Thread-Based Multitasking, and between Single-Threaded and Multi-Threaded Systems. Illustrate the life cycle of a thread in Java with a diagram, and provide a brief description of each thread state.**

- **Multitasking Comparison:** 
| Feature | Process-Based Multitasking | Thread-Based Multitasking | 
| :--- | :--- | :--- | | **Definition** | Running two or more programs concurrently. | A single program running multiple threads. | | **Address Space** | Each process has its own address space. | Threads share the process's address space. | | **Resource Usage** | Heavyweight; no resource sharing. | Lightweight; share memory and resources. | | **Communication** | Inter-process communication (complex). | Methods like `wait()`, `notify()`, `notifyAll()`. | | **Performance** | Slower context switching. | Faster context switching. |
    
- **Systems Comparison:**
    
    - **Single-Threaded:** Only one sequence of execution exists; a task must finish before the next begins.
    - **Multi-Threaded:** Multiple sequences of execution run concurrently within the same program, sharing memory but having separate stacks and registers.
- **Thread Life Cycle States:**
    
    1. **New (Born):** The thread is created (`new Thread()`) but `start()` has not been called.
    2. **Runnable (Ready):** `start()` is called. The thread is eligible to run and waiting for CPU time.
    3. **Running:** The CPU scheduler has picked the thread, and it is executing its `run()` method.
    4. **Blocked / Waiting (Non-Runnable):** The thread is temporarily inactive (e.g., due to `sleep()`, `wait()`, or waiting for I/O).
    5. **Terminated (Dead):** The `run()` method has finished or the thread was stopped.

---

### **Question 2**

#### **a) Analyze the given code and alter the program to set the frame surface color to blue.**

To set the background color of an AWT `Frame`, you must call the `setBackground()` method within the constructor or on the object reference.

```
import java.awt.*;
public class SetF extends Frame {
    public SetF() { // Added constructor to set properties
        setBackground(Color.BLUE);
    }
    public static void main(String argv[]) {
        SetF s = new SetF();
        s.setSize(300,200);
        s.setVisible(true);
    }
}
```

#### **b) i) Describe the steps involved in establishing a JDBC connection and executing SQL queries.**

1. **Load Driver:** Load the specific JDBC driver (e.g., `Class.forName("com.mysql.cj.jdbc.Driver")`).
2. **Establish Connection:** Use `DriverManager.getConnection(url, user, password)` to connect to the database.
3. **Create Statement:** Create a `Statement` or `PreparedStatement` object from the connection.
4. **Execute Query:** Run SQL commands using `executeQuery()` (for `SELECT`) or `executeUpdate()` (for `INSERT/UPDATE`).
5. **Process Results:** Use a `ResultSet` to iterate through query results.
6. **Close Resources:** Close the `ResultSet`, `Statement`, and `Connection`.

#### **b) ii) Analyze the following Java Code for its functionality and answer the questions:**

- **w) Purpose of `Pair<T, U>`:** It is a **generic class** designed to store a pair of two related objects of different or same types, providing a reusable container for any data types while ensuring type safety.
- **x) Generic usage in `Pair`:** The type parameters `T` and `U` act as placeholders. The methods `getFirst()` and `getSecond()` use these placeholders to return the exact type passed during instantiation, eliminating the need for explicit type casting.
- **y) Significance of `Pair<?, ?>` in `pairList`:** This is an **unbounded wildcard**. It allows the `ArrayList` to store `Pair` objects with _any_ type arguments (e.g., a pair of `String/Integer` and a pair of `String/Double` in the same list).
- **z) Output and Reason:**
    - **Output:**
        
        ```
        Age and 25
        Height and 5.9
        Age is 25
        Height is 5.9
        ```
        
    - **Reason:** `System.out.println(pair1)` invokes the overridden `toString()` method, which returns `first + " and " + second`. The `for` loop iterates through the list, calling `getFirst()` and `getSecond()` to print the values with " is ".

#### **c) With a diagram explain the Event Delegation Model in Java AWT. What are the roles of EventListener, EventObject, and EventSource?**

- **Event Delegation Model:** This model defines a standard mechanism to generate and process events. Instead of a source handling its own events, it **delegates** that responsibility to a registered listener object.
- **Roles:**
    - **EventSource:** The GUI component (e.g., a `Button`) where the action occurs. It generates an `EventObject` when its state changes.
    - **EventObject:** An object that encapsulates the state change, containing details like the source of the event and the time it occurred.
    - **EventListener:** An object that waits for events. It must implement a specific listener interface (e.g., `ActionListener`) and register with the source using methods like `addActionListener()`.
- **Button Click Example:**
    1. Create a `Button` (Source).
    2. Implement the `ActionListener` interface with the `actionPerformed()` method.
    3. Register the listener: `btn.addActionListener(this);`.
    4. When clicked, the button creates an `ActionEvent` and calls the listener's `actionPerformed()` method.

_(See for diagram references)_