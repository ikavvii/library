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