<h1 align="center">Stacks using Java Collection Framework</h1>

## 📘 Basic Idea

Here, we are implementing a **Stack** using Java’s built-in **`Stack` class** from the Collection Framework.  
A Stack follows the **LIFO (Last In, First Out)** rule — the last element inserted is the first one removed.

The `Stack` class already provides all the main stack operations:
1. **push()** → insert an element at the top  
2. **pop()** → remove the top element  
3. **peek()** → check the top element without removing  
4. **isEmpty()** → check if the stack is empty  

Since this is a built-in implementation, we don’t manually manage pointers or arrays — Java handles everything internally.

---

## 🪜 Step-by-Step Explanation

### 1️⃣ Importing the Stack Class  
We write:

import java.util.Stack;
This gives access to Java’s built-in Stack class.

---

### 2️⃣ Creating the main class

We create a class (`stack_collection`) that contains the `main()` method.  
All stack operations are performed inside `main()` using the Stack object.

---

### 3️⃣ Creating a Stack Object

Inside `main()`:
Stack<Integer> s = new Stack<>();

- Creates an empty stack that stores **Integer** values.  
- Java internally handles resizing and memory.

💡 Remember This:  
- The **top** element of the stack is always the **last** pushed element.

---

### 4️⃣ Pushing Elements (push())

We push elements:
- `s.push(5);`  
- `s.push(10);`  
- `s.push(15);`  

After pushing → stack looks like:  
`[5, 10, 15]`  
(Top = 15)

---

### 5️⃣ Looping Until Stack is Empty

We use:
while (!s.isEmpty())


This ensures we keep processing elements until stack becomes empty.

---

### 6️⃣ Checking Top Element (peek())

Inside the loop:
s.peek();

- Returns the **topmost** element  
- Does NOT remove it  
- First time → prints **15**

💡 Remember This:  
peek() helps check the top element without modifying the stack.

---

### 7️⃣ Removing the Top Element (pop())

s.pop();

- Removes the top element  
- After popping 15 → new top becomes 10  
- Then 5  
- Eventually the stack becomes empty

---

## 🧾 Output Example

15
10
5


This confirms **LIFO behavior**.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| push() | O(1) | O(n) |
| pop() | O(1) | O(n) |
| peek() | O(1) | O(n) |
| isEmpty() | O(1) | O(1) |

---

## Code
```
import java.util.Stack;

public class stack_collection {
public static void main(String[] args) {

	 Stack<Integer> s=new Stack<>();
	 s.push(5);
	 s.push(10);
	 s.push(15);

	 while(!s.isEmpty()) {
		 System.out.println(s.peek());
		 s.pop();
	 }
}
}
```
