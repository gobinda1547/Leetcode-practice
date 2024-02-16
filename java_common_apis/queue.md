## java.util.Queue

## add() & poll() & peek()

All these APIS have **O(1)** time complexity.

```java
public static void main(String[] args) {
	Queue<Integer> queue = new LinkedList<>();
	
	queue.add(2);
	queue.add(7);
	queue.add(4);
	
	System.out.println("Queue at this point 1 : " + queue);
	
	int polledItem = queue.poll();
	System.out.println("Polled item : " + polledItem);
	System.out.println("Queue at this point 2 : " + queue);
	
	int peekedItem = queue.peek();
	System.out.println("Peeked item : " + peekedItem);
	System.out.println("Queue at this point 3 : " + queue);
}

**Output:**

Queue at this point 1 : [2, 7, 4]
Polled item : 2
Queue at this point 2 : [7, 4]
Peeked item : 7
Queue at this point 3 : [7, 4]
```


## size() & isEmpty() & clear()

**size()** & **isEmpty()** have a complexity of **O(1)** But **clear()** API has **O(n)** complexity.

```java
public static void main(String[] args) {
	Queue<Integer> queue = new LinkedList<>();
	
	queue.add(5);
	queue.add(3);
	queue.add(9);
	
	System.out.println("(1) Size of the queue : " + queue.size());
	System.out.println("(1) Is queue empty : " + queue.isEmpty());
	
	queue.clear();
	
	System.out.println("(2) Size of the queue : " + queue.size());
	System.out.println("(2) Is queue empty : " + queue.isEmpty());
}

**Output:**

(1) Size of the queue : 3
(1) Is queue empty : false
(2) Size of the queue : 0
(2) Is queue empty : true
```