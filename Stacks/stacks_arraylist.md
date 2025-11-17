<h1 align="center">Stacks using ArrayList </h1>

## Basic Idea

We are implementing a Queue using a simple array in Java.
A Queue follows the FIFO (First In, First Out) rule — the first element inserted is the first one removed.
We’ll perform four basic queue operations:
1. add() → insert an element at the end
2. remove() → delete the front element
3. peek() → check the front element without deleting
4. isempty() → check if the queue is empty

---

## Step-by-Step Explanation

1️⃣ Creating the main class

We start with a main class (queue_array) which contains both our queue definition and a main() method to test it.

2️⃣ Creating a static inner class queue

We define a static inner class queue inside our main class.
This class will represent the queue itself — all data and functions related to it.

Why static?
Because it allows us to call its members directly without needing an object of the outer class.
It keeps things simpler for practice.

3️⃣ Declaring variables

Inside the queue class we have:

arr[] → The actual array where we’ll store our queue elements.

size → To store the maximum capacity of the queue.

rear → Points to the last inserted element.

Starts at -1 → means queue is empty.

Each time we add something, rear increases by 1.

💡 Remember This:

When rear == -1 → empty queue

When rear == size - 1 → full queue

4️⃣ Constructor

When we create a queue object, we give it a size (like 10).
The constructor initializes the array with that size and sets size = n.

This step “allocates memory” for our queue.

5️⃣ Checking if queue is empty (isempty())

This function just checks whether rear == -1.
If yes → queue is empty.
Otherwise → not empty.

⚠️ Common Mistake:
Don’t confuse “empty” with “full”. Always remember:

Empty → rear == -1

Full → rear == size - 1

6️⃣ Adding an element (add(data))

When we call add(data):

We first check if the queue is already full → rear == size - 1.
If full, we can’t add any more.

If not full:

Increase rear by 1.

Store the new element at arr[rear].

💡 Remember This:

The very first element goes to index 0 (since rear starts from -1).

Always check for “full” before inserting — otherwise, you’ll get ArrayIndexOutOfBoundsException.

7️⃣ Removing an element (remove())

When we call remove():

Check if the queue is empty. If it is, print "empty" and return -1.

Store the first element (arr[0]) — this is the front element to remove.

Shift all elements one step to the left so that the new front becomes index 0.
Example: [10, 20, 30, 40] → [20, 30, 40]

Decrease rear by 1 since one element was removed.

Return the removed element.

⚠️ Common Mistake:
Forgetting to shift elements → will cause wrong results when you peek or remove again.

💡 Remember This:
In this version, remove() is O(n) because we shift elements.
That’s okay for learning, but not ideal for performance.

8️⃣ Peeking at the front element (peek())

This function lets us see which element is at the front of the queue — the one that will be removed next.
It does not remove it.
Just returns arr[0].

💡 Remember This:
Peek doesn’t change the queue — it’s just for checking the front element.

9️⃣ Testing in the main() method

We create a queue object (like queue q = new queue(10)),
add a few elements (10, 20, 30, 40),
and use a loop to print each element (using peek()) and remove it (using remove()) until the queue is empty.

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
		stack s= new stack();
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

