<h1 align="center">Stacks using ArrayList</h1>

## Basic Idea

We are implementing a **Stack** using Java’s **ArrayList**.  
A Stack follows the **LIFO (Last In, First Out)** rule — the element inserted last is removed first.

ArrayList makes this implementation simple because:
- It automatically grows in size  
- Accessing and removing the last element is **O(1)**  
- We don’t need to manage array indexes manually  

Stack operations implemented:
1. **push()** → insert at the top  
2. **pop()** → remove the top element  
3. **peek()** → view the top element  
4. **isempty()** → check if stack is empty  

---

## Step-by-Step Explanation

### 1️⃣ Creating the stack class  
We create a static inner class `stack` which contains the actual logic of the stack.  
Inside it, we use:

- `ArrayList<Integer> l` → stores all elements of the stack  

This ArrayList behaves as our dynamic stack.

---

### 2️⃣ Checking if the stack is empty (isempty())  
return l.size() == 0;

If the ArrayList has no elements, the stack is empty.

💡 **Remember:**  
ArrayList size changes automatically — you don’t manage it manually.

---

### 3️⃣ Pushing an element (push())  


l.add(data);

This inserts an element at the **end** of the ArrayList, which is considered the **top** of the stack.

Example after pushes:
- push(5) → `[5]`
- push(10) → `[5, 10]`
- push(15) → `[5, 10, 15]` (top = 15)

---

### 4️⃣ Popping the top element (pop())  
Steps:
1. If empty → return -1  
2. Store the top element:  


l.get(l.size() - 1)

3. Remove it:  


l.remove(l.size() - 1)

4. Return the removed value  

This removes the last element, which is the top of the stack.

---

### 5️⃣ Peeking at the top element (peek())  
If not empty, return:


l.get(l.size() - 1)

This gives the topmost value without removing it.

---

### 6️⃣ Testing in main()  
In `main()`:
- Create a stack object  
- Push: 5, 10, 15  
- Keep printing and popping until the stack becomes empty  

Output:


15
10
5


This confirms **LIFO** behavior.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| push() | O(1) | O(n) |
| pop() | O(1) | O(n) |
| peek() | O(1) | O(n) |
| isempty() | O(1) | O(1) |

---

## Code

```
import java.util.ArrayList;

public class stack_arraylist {

static class stack{
	ArrayList<Integer> l=new ArrayList<>();

	public boolean isempty() {			
		return l.size()==0;
	}
	
	public void push(int data) {
		l.add(data);
	}
	
	public int pop() {
		if (isempty()) {
			return -1;
		}
		int top=l.get(l.size()-1);
		l.remove(l.size()-1);
		return top;	
	}
	
	public int peek() {
		if (isempty()) {
			return -1;
		}
		return l.get(l.size()-1);
	}
}

public static void main(String[] args) {
	stack s = new stack();
	s.push(5);
	s.push(10);
	s.push(15);
	
	while(!s.isempty()) {
		System.out.println(s.peek());
		s.pop();
	}
}
}
```
