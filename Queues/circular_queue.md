<h1 align="center">Circular Queue using Array</h1>

## Basic Idea

We are implementing a **Circular Queue** using an array in Java.  
A circular queue also works on the **FIFO (First In, First Out)** principle, but it solves the biggest problem of a normal array-based queue:

❌ Normal queue wastes space after repeated insertions & removals.  
✅ Circular queue **reuses freed space** using modulo arithmetic.

We maintain:
- **front** → points to the first element  
- **rear** → points to the last element  
- Queue becomes circular using:  
(rear + 1) % size

markdown
Copy code

Operations performed:
1. **add()** → insert at rear  
2. **remove()** → remove from front  
3. **peek()** → check front element  
4. **isempty()**  
5. **isfull()**

---

## Step-by-Step Explanation

### 1️⃣ Creating the circular queue class  
The class `cqueue` contains:
- `arr[]` → array to store elements  
- `front` and `rear` pointers  
- `size` → capacity of the queue  

Initially:
front = -1
rear = -1

yaml
Copy code

This means the queue is empty.

---

### 2️⃣ Constructor  
public cqueue(int n) {
arr = new int[n];
this.size = n;
}

yaml
Copy code
- Allocates array of given size  
- Initializes queue capacity  

---

### 3️⃣ Checking if queue is empty (isempty())  
return rear == -1 && front == -1;

yaml
Copy code
If both are -1 → queue has no elements.

---

### 4️⃣ Checking if queue is full (isfull())  
(rear + 1) % size == front

yaml
Copy code
This means the next circular index of rear is occupied → queue is full.

💡 **Key Concept:**  
Modulo `%` makes the queue **wrap around**.

---

### 5️⃣ Adding elements (add())  
Steps:
1. If queue is full → print “full”  
2. If queue is empty (front = -1) → set front = 0  
3. Move rear forward using:  
rear = (rear + 1) % size;

markdown
Copy code
4. Store element at `arr[rear]`

Example insertions:
- add(1) → front = 0, rear = 0  
- add(2) → rear = 1  
- add(3) → rear = 2  

Now the queue looks like:
front → 1 2 3 ← rear

yaml
Copy code

---

### 6️⃣ Removing elements (remove())  
Steps:
1. If empty → return -1  
2. Store front element  
3. If this was the only element (`front == rear`):  
   - Reset both → `front = rear = -1`  
4. Else move front forward using:  
front = (front + 1) % size;

yaml
Copy code

This removes the **frontmost** element.

---

### 7️⃣ Peeking front element (peek())  
- If empty → return -1  
- Otherwise return `arr[front]`  

This shows the first element without removing it.

---

### 8️⃣ Testing in main()  
Steps:
- Create a circular queue of size 5  
- Add: 1, 2, 3  
- Remove elements while printing front  

Output:
1
2
3

yaml
Copy code

This confirms FIFO behavior.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| add() | O(1) | O(n) |
| remove() | O(1) | O(n) |
| peek() | O(1) | O(1) |
| isempty() | O(1) | O(1) |
| isfull() | O(1) | O(1) |

---

## Code

```
public class queue_circular_array {

csharp
Copy code
public static class cqueue {
	static int arr[];
	static int rear = -1;
	static int size;
	static int front = -1;

	public cqueue(int n) {
		arr = new int[n];
		this.size = n;
	}

	public static boolean isempty() {
		return rear == -1 && front == -1;
	}

	public static boolean isfull() {
		return (rear + 1) % size == front;
	}

	public static void add(int data) {
		if (isfull()) {
			System.out.print("full");
			return;
		}
		if (front == -1) {
			front = 0;
		}
		rear = (rear + 1) % size;
		arr[rear] = data;
	}

	public static int remove() {
		if (isempty()) {
			System.out.print("empty");
			return -1;
		}
		int temp = arr[front];
		if (rear == front) {
			rear = front = -1;
		} else {
			front = (front + 1) % size;
		}
		return temp;
	}

	public static int peek() {
		if (isempty()) {
			System.out.print("empty");
			return -1;
		}
		return arr[front];
	}
}

public static void main(String[] args) {
	cqueue q = new cqueue(5);
	q.add(1);
	q.add(2);
	q.add(3);

	while (!q.isempty()) {
		System.out.println(q.peek());
		q.remove();
	}
}
}
```