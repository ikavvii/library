## **Queue Implementation using Singly Linked List**

### **Structure Definition:**

Code

```
Structure Node:
    data: integer
    next: pointer to Node
End Structure

Structure Queue:
    front: pointer to Node
    rear:  pointer to Node
End Structure
```

---

### **Queue Operations:**

#### **1. Initialize Queue**

Code

```
Algorithm: initQueue()
Output: Empty queue

1. Create new Queue Q
2. Q.front = NULL
3. Q.rear = NULL
4. Return Q
```

---

#### **2. Enqueue (Insert at rear)**

Code

```
Algorithm: enqueue(Q, value)
Input: Queue Q, value to insert
Output: Updated queue

1. Create new Node N
2. N.data = value
3. N.next = NULL
4. If Q.rear == NULL then  // Queue is empty
      Q.front = N
      Q.rear = N
   Else
      Q.rear. next = N
      Q.rear = N
   End If
5. Print "Enqueued:  " + value
```

---

#### **3. Dequeue (Delete from front)**

Code

```
Algorithm: dequeue(Q)
Input: Queue Q
Output:  Removed value

1. If Q.front == NULL then
      Print "Queue Underflow"
      Return -1
   End If
2. temp = Q.front
3. value = temp.data
4. Q.front = Q.front.next
5. If Q.front == NULL then  // Queue becomes empty
      Q.rear = NULL
   End If
6. Free(temp)
7. Return value
```

---

#### **4. Display Queue**

Code

```
Algorithm: display(Q)
Input: Queue Q
Output: Queue elements

1. If Q.front == NULL then
      Print "Queue is empty"
      Return
   End If
2. temp = Q.front
3. Print "Queue: "
4. While temp != NULL do
      Print temp.data + " "
      temp = temp. next
   End While
```

---

#### **5. Check if Empty**

Code

```
Algorithm: isEmpty(Q)
Input: Queue Q
Output: True if empty, False otherwise

1. If Q.front == NULL then
      Return True
   Else
      Return False
   End If
```

---

### **Example Execution:**

Code

```
Operation       Queue State (front → rear)    Output
-----------------------------------------------------------
initQueue()     []                            Queue created
enqueue(10)     [10]                          Enqueued: 10
enqueue(20)     [10, 20]                      Enqueued: 20
enqueue(30)     [10, 20, 30]                  Enqueued: 30
dequeue()       [20, 30]                      Dequeued: 10
enqueue(40)     [20, 30, 40]                  Enqueued: 40
dequeue()       [30, 40]                      Dequeued: 20
```