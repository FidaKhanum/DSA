<h1 align="center">Push an Element at the Bottom of a Stack (Using Recursion)</h1>

## Basic Idea

We want to **insert an element at the bottom of a stack**, not at the top.  
Normally, `push()` always inserts at the **top**, so to place an element at the bottom, we need a different approach.

Since Java’s `Stack` doesn't allow direct bottom insertion, we use **recursion**:
1. Pop all elements until the stack becomes empty  
2. Insert the new element  
3. Push back all previously removed elements  

This ensures the new element ends up at the **bottom**, while the original order of elements above it is preserved.

Example:  
Original stack (top → bottom): `3, 2, 1`  
Insert `4` at bottom → New stack: `3, 2, 1, 4`

---

## Step-by-Step Explanation

### 1️⃣ Creating the main class  
The class `stack_pushbottom` contains both:
- the recursive function  
- the `main()` method to test it  

---

### 2️⃣ Using Java’s Stack class  
We import:
import java.util.Stack;

This gives access to the built-in stack.

---

### 3️⃣ Understanding the `pushbottom()` method  
This method inserts `data` at the **bottom** of the stack using recursion.

Signature:


pushbottom(int data, Stack<Integer> s)


---

### 4️⃣ Base Case (when stack is empty)  


if (s.isEmpty()) {
s.push(data);
return;
}


- If the stack becomes empty, that means we’ve popped all elements.  
- This is the correct moment to insert the element at the bottom.  
- We push the data and return.

---

### 5️⃣ Recursive Case  
If stack is not empty:
1. Pop the top element → store it  


int top = s.pop();

2. Recursively call `pushbottom()`  
- This keeps popping until we reach the base case  
3. After recursion, push the stored element back  


s.push(top);


This re-creates the original stack order above the newly inserted bottom element.

💡 **Remember This:**  
Recursion unwinds in reverse order, helping place all popped elements back in their original sequence.

---

### 6️⃣ Testing in `main()`  
In `main()`:
- Create a new stack  
- Push elements: 1, 2, 3  
- Call `pushbottom(4, s)` → insert 4 at the bottom  
- Print elements while popping to observe stack order  

Output:


3
2
1
4


This confirms the element `4` was inserted at the **bottom**.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| pushbottom() | O(n) | O(n) recursion stack |
| normal push/pop/peek | O(1) | O(1) |

---

## Code

```
import java.util.Stack;

public class stack_pushbottom {

public static void pushbottom(int data, Stack<Integer> s) {
	if(s.isEmpty()) {
		s.push(data);
		return;
	}
	int top=s.pop();
	pushbottom(data, s);
	s.push(top);
}

public static void main(String[] args) {

	Stack<Integer> s=new Stack<>();
	s.push(1);
	s.push(2);
	s.push(3);

	pushbottom(4, s);

	while(!s.isEmpty()) {
		System.out.println(s.peek());
		s.pop();
	}
}
}
```
