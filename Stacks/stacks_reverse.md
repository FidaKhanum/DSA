<h1 align="center">Reverse a Stack Using Recursion</h1>

## Basic Idea

We want to **reverse an entire stack** without using any extra data structure (like another stack or array).  
Since the Stack class allows insertion only at the **top**, we use **recursion** to reverse the order.

The reversal works in two main steps:
1. Recursively pop all elements until the stack becomes empty  
2. Insert each popped element at the **bottom** using the `pushbottom()` helper function  

This ensures the entire order of the stack is reversed.

Example:  
Original (top → bottom): `3, 2, 1`  
Reversed: `1, 2, 3`

---

## Step-by-Step Explanation

### 1️⃣ pushbottom() – Helper Function  
This method inserts an element at the **bottom of the stack** using recursion.

- If the stack is empty → push the element (base case)
- Otherwise:
  1. Pop the top
  2. Recursively call `pushbottom()`
  3. Push the popped value back

This ensures the new element goes to the bottom while the original order is restored on top.

---

### 2️⃣ reverse() – Main Function to Reverse the Stack  
public static void reverse(Stack<Integer> s)


This method reverses the entire stack using recursion.

Steps:
1. Base case → if stack is empty, return  
2. Pop the top element  
3. Recursively reverse the remaining stack  
4. Insert the popped element at the **bottom** using `pushbottom()`  

💡 **Why this works:**  
Recursion empties the stack completely.  
Then while unwinding, each element gets inserted at the bottom, reversing the order.

---

### 3️⃣ Using the reverse function in main()

In main():
- A new stack is created  
- Elements 1, 2, 3 are pushed  
- Calling `reverse(s)` reverses the stack  

We also use:
s.search(2)


to find the 1-based position of element `2` in the reversed stack.

Then we print all elements until the stack becomes empty.

This confirms that the stack was reversed successfully.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| reverse() | O(n²) (because each pushbottom() is O(n)) | O(n) recursion |
| pushbottom() | O(n) | O(n) recursion |
| normal push/pop | O(1) | O(1) |

---

## Code
```
import java.util.Stack;

public class stack_reverse {

public static void pushbottom(int data, Stack<Integer> s) {
	if(s.isEmpty()) {
		s.push(data);
		return;
	}
	int top=s.pop();
	pushbottom(data, s);
	s.push(top);
}

public static void reverse(Stack<Integer> s) {
	if(s.isEmpty()) {
		return;
	}
	int top=s.pop();
	reverse(s);
	pushbottom(top, s);
}

public static void main(String[] args) {

	Stack<Integer> s=new Stack<>();
	s.push(1);
	s.push(2);
	s.push(3);

	reverse(s);

	System.out.println("Position of 2: " + s.search(2));

	while(!s.isEmpty()) {
		System.out.println(s.peek());
		s.pop();
	}
}
}
```
