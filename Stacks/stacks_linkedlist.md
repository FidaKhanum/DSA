<h1 align="center">Stacks using Linked List</h1>

## Basic Idea

We are implementing a **Stack** using a **Linked List** in Java.  
A Stack works on the **LIFO (Last In, First Out)** principle — the last inserted element is removed first.

In this implementation:
- Each element is stored inside a **Node**.
- We use the **head** of the linked list as the **top** of the stack.
- Stack operations become:
  1. **push()** → insert at the head  
  2. **pop()** → remove from the head  
  3. **peek()** → look at the head  
  4. **isEmpty()** → check if head is null  

This avoids resizing issues because linked lists grow dynamically.

---

## Step-by-Step Explanation

### 1️⃣ Creating the Node class  
We create a private static inner class `Node`:

- `int data` → stores the value  
- `Node next` → pointer to the next node  
- Constructor initializes the node with given data

Each Node represents one element of the stack.

---

### 2️⃣ Creating the Stacks class  
This class defines all stack operations and the stack structure.

It contains:
- `static Node head` → the top of the stack  
  - If head is null → stack is empty  
  - New elements are always added at the head

💡 **Remember:**  
Linked list head = top of the stack.

---

### 3️⃣ Pushing an element (push())  
To push:
1. Create a new node  
2. If the stack is empty (head is null) → new node becomes the head  
3. Otherwise:  
   - Point newnode.next to current head  
   - Move head to newnode  

This places the new element on the **top** of the stack.

Example after pushes:  
`push(0)` → 0  
`push(1)` → 1 → 0  
`push(2)` → 2 → 1 → 0 (top = 2)

---

### 4️⃣ Checking if the stack is empty (isEmpty())  
