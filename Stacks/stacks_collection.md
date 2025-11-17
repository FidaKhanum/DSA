<h1 align="center">Stacks using Java Collection Framework (Stack Class)</h1>

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
```java
import java.util.Stack;
