<h1 align="center">Queues using Array</h1>

## Basic Idea

We are implementing a **Queue** using a **simple array** in Java.  
A Queue follows the **FIFO (First In, First Out)** principle — the first element inserted is the first one removed.

We will implement four basic queue operations:
1. **add()** → insert an element at the rear  
2. **remove()** → delete the front element  
3. **peek()** → check the front element without removing it  
4. **isempty()** → check if the queue is empty  

This is a basic queue implementation suitable for understanding how queues work internally.

---

## Step-by-Step Explanation

### 1️⃣ Creating the queue class  
Inside the main class, we create a static inner class named `queue`.  
This class contains:
- an array `arr[]` to store elements  
- `size` to store capacity  
- `rear` to track the last inserted element  

💡 **Remember:**  
`rear = -1` means the queue is empty.

---

### 2️⃣ Declaring variables

Inside the queue class:
- `static int arr[]` → the array holding queue values  
- `static int size` → max capacity  
- `static int rear = -1` → last element index  

As we add elements, `rear++` moves forward.

---

### 3️⃣ Constructor  
public queue(int n) {
this.size = n;
arr = new int[n];
}

- Initializes the queue with size `n`  
- Allocates memory for the array  

---

### 4️⃣ Checking if queue is empty (isempty())  


return rear == -1;

If rear is still at -1 → no elements have been added → queue is empty.

⚠️ **Common Mistake:**  
Don't confuse empty with full:
- Empty → `rear == -1`  
- Full → `rear == size - 1`  

---

### 5️⃣ Adding elements (add())  
Steps:
1. Check if queue is full → `rear == size - 1`  
   - If yes, print `"full"`  
2. Otherwise:
   - Increment `rear`  
   - Insert data at `arr[rear]`  

💡 **Remember:**  
- First element goes to index 0  
- Every new element goes at the end of the queue  

---

### 6️⃣ Removing elements (remove())  
Steps:
1. Check if queue is empty → return -1  
2. Store front element → `arr[0]`  
3. Shift all elements one step left  
4. Decrease `rear`  
5. Return the removed element  

Example of shifting:  
Before remove: `[10, 20, 30, 40]`  
After remove: `[20, 30, 40]`

⚠️ **Important:**  
Shifting makes remove() **O(n)**.

---

### 7️⃣ Peeking front element (peek())  
- If empty → return -1  
- Else return `arr[0]`  

This does not remove the element — just shows the front.

---

### 8️⃣ Testing in main()  
We create a queue object:


queue q = new queue(10);

We add:
- 10  
- 20  
- 30  
- 40  

Then print and remove elements one by one until queue becomes empty.

Output:


10
20
30
40


This confirms FIFO behavior.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| add() | O(1) | O(1) |
| remove() | O(n) | O(1) |
| peek() | O(1) | O(1) |
| isempty() | O(1) | O(1) |

---

## Code

```
public class queue_array {

public static class queue{
	static int arr[];
	static int size;
	static int rear=-1;

	public queue(int n) {
		this.size=n;
		arr=new int[n];
	}
	
	public static boolean isempty() {
		return rear==-1;
	}

	public static void add(int data) {
		if(rear==size-1) {
			System.out.print("full");
			return;
		}
		rear++;
		arr[rear]=data;
	}

	public static int remove() {
		if(isempty()) {
			System.out.print("empty");
			return -1;
		}
		int front=arr[0];
		for(int i=0;i<rear;i++) {
			arr[i]=arr[i+1];
		}
		rear--;
		return front;
	}

	public static int peek() {
		if(isempty()) {
			System.out.print("empty");
			return -1;
		}
		return arr[0];
	}
}

public static void main(String[] args) {
	queue q=new queue(10);
	q.add(10);
	q.add(20);
	q.add(30);
	q.add(40);

	while(!q.isempty()) {
		System.out.println(q.peek());
		q.remove();
	}
}
}
```