<h1 align="center">Queue using Linked List</h1>

## Basic Idea

We are implementing a **Queue** using a **Linked List** in Java.  
A Queue works on the **FIFO (First In, First Out)** principle — the element inserted first is the first one removed.

In this implementation:
- Each element is represented by a **Node**
- We maintain **two pointers**:
  - **head** → points to the front  
  - **tail** → points to the rear  
- This allows efficient:
  1. **add()** → insert at tail  
  2. **remove()** → delete from head  
  3. **peek()** → return the front element  
  4. **isempty()** → check if queue is empty  

Using a linked list avoids resizing issues and provides **O(1)** insertion and deletion.

---

## Step-by-Step Explanation

### 1️⃣ Creating the Node class  
Each Node contains:
- `int data` → value of the element  
- `node next` → pointer to the next node  

`next = null` initially since new nodes don’t point anywhere yet.

---

### 2️⃣ Creating the queue class  
The queue class maintains:
- `static node head` → front of queue  
- `static node tail` → rear of queue  

💡 **Remember:**  
- If **head = null AND tail = null**, queue is empty  
- We add at tail, remove from head

---

### 3️⃣ Checking if queue is empty (isempty())  
return head == null & tail == null;

If both pointers are null → no elements are present.

⚠️ Note:  
`&` works here but `&&` is more common in conditions.

---

### 4️⃣ Adding an element (add())  
Steps:
1. Create a new node  
2. If queue is empty (tail == null):  
   - head = tail = newnode  
   - return  
3. Otherwise:  
   - Attach newnode after tail → `tail.next = newnode`  
   - Move tail forward → `tail = newnode`  

This inserts elements at the **rear**.

Example after adds:  
1 → 2 → 3

(head = 1, tail = 3)

---

### 5️⃣ Removing an element (remove())  
Steps:
1. If empty → return -1  
2. Store `head.data` → this is the front element  
3. If head == tail (only one element):  
   - Set tail = null  
4. Move head to next node → `head = head.next`  
5. Return the removed value  

This removes from the **front**, ensuring FIFO order.

---

### 6️⃣ Peeking at the front (peek())  
- If empty → return -1  
- Else return `head.data`  

This shows the front element without removing it.

---

### 7️⃣ Testing in main()  
We create a queue object and add:
- 1  
- 2  
- 3  

Then print and remove elements until queue becomes empty.

Output:


1
2
3

This confirms correct FIFO behavior.

---

## 🧮 Complexity Analysis

| Operation | Time | Space |
|------------|-------|-------|
| add() | O(1) | O(n) |
| remove() | O(1) | O(n) |
| peek() | O(1) | O(1) |
| isempty() | O(1) | O(1) |

---

## Code

```
public class queue_linkedlist {

static class node {
	int data;
	node next;
	node(int data){
		this.data=data;
		next=null;
	}
}

public static class queue{
	static node head=null;
	static node tail=null;
	
	public static boolean isempty() {
		return head==null & tail==null;
	}
	
	public static void add(int data) {
		node newnode=new node(data);
		if(tail==null) {
			tail=head=newnode;
			return ;
		}
		tail.next=newnode;
		tail=newnode;
	}
	
	public static int remove() {
		if(isempty()) {
			System.out.print("empty");
			return -1;
		}
		int front=head.data;
		if(head==tail) {
			tail=null;
		}
		head=head.next;
		return front;
	}

	public static int peek() {
		if(isempty()) {
			System.out.print("empty");
			return -1;
		}
		return head.data;
	}
}

public static void main(String[] args) {

	queue q=new queue();
	q.add(1);
	q.add(2);
	q.add(3);

	while(!q.isempty()) {
		System.out.println(q.peek());
		q.remove();
	}
}
}
```