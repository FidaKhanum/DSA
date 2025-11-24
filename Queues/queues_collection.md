<h1 align="center">Queue using Collection Framework</h1>

## Basic Idea

We are implementing a **Queue** using Java’s **Collection Framework**.  
Instead of building our own queue logic, we use:

- **Queue Interface** → provides queue operations  
- **LinkedList Class** → implements Queue efficiently  

This gives us a ready-made, optimized FIFO (First In, First Out) queue.

Operations used:
1. **add()** → insert at the rear  
2. **peek()** → view the front element  
3. **remove()** → delete the front element  
4. **isEmpty()** → check if queue is empty  

Java internally handles all pointer movement and resizing, so the implementation becomes very clean.

---

## Step-by-Step Explanation

### 1️⃣ Importing Queue and LinkedList  
import java.util.LinkedList;
import java.util.Queue;

- `Queue` is an interface — it defines queue behavior  
- `LinkedList` is a class — it implements the Queue interface  

We use `LinkedList` because it provides **O(1)** insertion and deletion at the ends.

---

### 2️⃣ Creating the main class  
`queue_collection` contains the `main()` method where we test built-in queue operations.

---

### 3️⃣ Creating a Queue Object  


Queue<Integer> q = new LinkedList<>();

- We create a queue that stores integers  
- Since LinkedList implements Queue, all queue operations are available  

💡 **Remember:**  
When using the Collection Framework:
- Left side → Interface (`Queue`)  
- Right side → Concrete class (`LinkedList`)

---

### 4️⃣ Adding Elements (add())  


q.add(1);
q.add(2);
q.add(3);

Elements are added in this order:
1 → 2 → 3  
Front → 1  
Rear → 3  

---

### 5️⃣ Checking if Queue is Empty  


while (!q.isEmpty())

This loop continues until all elements are removed.

---

### 6️⃣ Getting the Front Element (peek())  


q.peek();

- Returns the **front** element  
- Does *not* remove it  
- First time → returns 1  

---

### 7️⃣ Removing Elements (remove())  


q.remove();

- Removes the element at the front  
- After removing 1 → queue becomes [2, 3]  
- Then 2 → [3]  
- Finally 3 → []  

This ensures FIFO behavior.

---

## 🧾 Output Example


1
2
3


---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| add() | O(1) | O(n) |
| remove() | O(1) | O(n) |
| peek() | O(1) | O(1) |
| isEmpty() | O(1) | O(1) |

---

## Code

```
import java.util.LinkedList;
import java.util.Queue;

public class queue_collection {

public static void main(String[] args) {

	Queue<Integer> q = new LinkedList<>();

	q.add(1);
	q.add(2);
	q.add(3);

	while (!q.isEmpty()) {
		System.out.println(q.peek());
		q.remove();
	}
}
}
```