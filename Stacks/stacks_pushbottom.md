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
