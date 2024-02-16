## java.util.Stack

#### push() & pop() & peek()

All these APIS have **O(1)** time complexity.

```java
public static void main(String[] args) {
	Stack<Integer> stack = new Stack<>();
	
	stack.push(5);
	stack.push(3);
	stack.push(9);
	
	System.out.println("Stack at this point 1 : " + stack);
	
	int popedItem = stack.pop();
	System.out.println("Poped item : " + popedItem);
	System.out.println("Stack at this point 2 : " + stack);
	
	int peekedItem = stack.peek();
	System.out.println("Peeked item : " + peekedItem);
	System.out.println("Stack at this point 3 : " + stack);
}

**Output:**

Stack at this point 1 : [5, 3, 9]
Poped item : 9
Stack at this point 2 : [5, 3]
Peeked item : 3
Stack at this point 3 : [5, 3]
```


#### size() & isEmpty() & clear()

**size()** & **isEmpty()** have a complexity of **O(1)** But **clear()** API has **O(n)** complexity.

```java
public static void main(String[] args) {
	Stack<Integer> stack = new Stack<>();
	
	stack.push(5);
	stack.push(3);
	stack.push(9);
	
	System.out.println("(1) Size of the stack : " + stack.size());
	System.out.println("(1) Is stack empty : " + stack.isEmpty());
	
	stack.clear();
	
	System.out.println("(2) Size of the stack : " + stack.size());
	System.out.println("(2) Is stack empty : " + stack.isEmpty());
}

**Output:**

(1) Size of the stack : 3
(1) Is stack empty : false
(2) Size of the stack : 0
(2) Is stack empty : true
```