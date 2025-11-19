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
return head == null;

If no nodes exist, head is null, meaning the stack is empty.

---

### 5️⃣ Popping an element (pop())  
1. Check if empty → return -1  
2. Store the current head (top)  
3. Move head to the next node (`head = head.next`)  
4. Return the removed value  

This removes the top element.

---

### 6️⃣ Peeking at the top element (peek())  
1. Check if stack is empty → return -1  
2. Return `head.data`  

This gives the top element without removing it.

---

### 7️⃣ Testing the implementation  
In `main()`:
- Create a stack object  
- Push: 0, 1, 2  
- Print top element (peek)  
- Pop until the stack becomes empty  

Output will be:


2
1
0


This matches **LIFO behavior**.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| push() | O(1) | O(n) |
| pop() | O(1) | O(n) |
| peek() | O(1) | O(1) |
| isEmpty() | O(1) | O(1) |

---

## Code

```
public class stack_linkedlist {

private static class Node{
    int data;
    Node next;
    Node(int data){
        this.data=data;
        next=null;
    }
}

public static class Stacks{

    public static Node head=null;

    public static void push(int data) {
        Node newnode= new Node(data);
        if(head==null) {
            head=newnode;
            return;
        }
        newnode.next=head;
        head=newnode;
    }

    public static boolean isEmpty() {
        return head==null;
    }

    public static int pop() {
        if(isEmpty()) {
            return -1;
        }
        Node top=head;
        head=head.next;
        return top.data;
    }

    public static int peek() {
        if(isEmpty()) {
            return -1;
        }
        Node top=head;
        return top.data;
    }
}

public static void main(String[] args) {

    Stacks s=new Stacks();
    s.push(0);
    s.push(1);
    s.push(2);
    while(!s.isEmpty()) {
        System.out.println(s.peek());
        s.pop();
    }
}
}
```
