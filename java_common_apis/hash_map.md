## java.util.HashMap

## put() & size() & isEmpty()

All of these APIs have a time complexity of **O(1)**.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("gobinda", 20000);
	map.put("sourav", 25000);
	map.put("shamim", 30000);

	System.out.println("Map size : " + map.size());
	System.out.println("Is map empty : " + map.isEmpty());
}

**Output:**

Map size : 3
Is map empty : false
```

## containsKey() & containsValue()

**containsKey()** has a complexity of **O(1)** in average case but **O(n)** in worst case.
On the other hand **containsValue()** always have a time complexity of **O(n)**.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("gobinda", 20000);
	map.put("sourav", 25000);
	map.put("shamim", 30000);

	System.out.println("Is key(joy) exist -> " + map.containsKey("joy"));
	System.out.println("Is key(gobinda) exist -> " + map.containsKey("gobinda"));

	System.out.println("Is value(30000) exist -> " + map.containsValue(30000));
	System.out.println("Is value(10000) exist -> " + map.containsValue(10000));
}

**Output:**

Is key(joy) exist -> false
Is key(gobinda) exist -> true
Is value(30000) exist -> true
Is value(10000) exist -> false
```


## get()

**get()** has a complexity of **O(1)** in average case but **O(n)** in worst case. HashMap uses hashing to directly access key-value pairs. It calculates the hash value of the key, finds the corresponding bucket, and retrieves the value. This usually takes constant time, but collisions (multiple keys in a bucket) can lead to linear searches within a bucket, resulting in O(n) in the worst case.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("gobinda", 20000);
	map.put("sourav", 25000);
	map.put("shamim", 30000);

	System.out.println("Getting item -> " + map.get("gobinda"));
	System.out.println("Getting item -> " + map.get("joy"));
}

**Output:**

Getting item -> 20000
Getting item -> null
```


## putIfAbsent()

**putIfAbsent()** has a complexity of **O(1)** in average case but **O(n)** in worst case.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("gobinda", 20000);
	map.put("sourav", 25000);
	map.put("shamim", 30000);

	System.out.println("Initially = " + map);

	map.putIfAbsent("gobinda", 5000);
	System.out.println("putIfAbsent(gobinda) = " + map);

	map.putIfAbsent("joy", 5000);
	System.out.println("putIfAbsent(joy) = " + map);
}

**Output:**

Initially = {shamim=30000, gobinda=20000, sourav=25000}
putIfAbsent(gobinda) = {shamim=30000, gobinda=20000, sourav=25000}
putIfAbsent(joy) = {shamim=30000, joy=5000, gobinda=20000, sourav=25000}
```


## remove()

**remove()** has a complexity of **O(1)** in average case but **O(n)** in worst case.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("a", 1);
	map.put("b", 2);
	map.put("c", 3);

	System.out.println("Initially = " + map);

	map.remove("gobinda");
	System.out.println("remove(gobinda) = " + map);

	map.remove("a");
	System.out.println("remove(a) = " + map);
}

**Output:**

Initially = {a=1, b=2, c=3}
remove(gobinda) = {a=1, b=2, c=3}
remove(a) = {b=2, c=3}
```


## computeIfAbsent() & computeIfPresent()

Both function have a time complexity of **O(1)** in average case but **O(n)** in worst case.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("a", 1);
	map.put("b", 2);
	map.put("c", 3);

	System.out.println("Initially = " + map);

	map.computeIfAbsent("m", (k) -> 40);
	System.out.println("computeIfAbsent = " + map);

	map.computeIfPresent("b", (k, v) -> v + 10);
	System.out.println("computeIfPresent = " + map);
}

**Output:**

Initially = {a=1, b=2, c=3}
computeIfAbsent = {a=1, b=2, c=3, m=40}
computeIfPresent = {a=1, b=12, c=3, m=40}
```



## keySet() & values()

**keySet()** function has a time complexity of **O(1)**. All that it is doing is returning a wrapper object on the HashMap. But **values()** has a time complexity of **O(n)** since HashMap doesn't have a direct way to access all values efficiently based on their content.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("a", 1);
	map.put("b", 2);
	map.put("c", 3);

	System.out.println("Map = " + map);

	ArrayList<String> keyItems = new ArrayList<>(map.keySet());
	System.out.println("Key items : " + keyItems);

	ArrayList<Integer> valueItems = new ArrayList<>(map.values());
	System.out.println("Value items : " + valueItems);
}

**Output:**

Map = {a=1, b=2, c=3}
Key items : [a, b, c]
Value items : [1, 2, 3]
```


## entrySet()

**entrySet()** function has a time complexity of **O(1)**.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("a", 1);
	map.put("b", 2);
	map.put("c", 3);

	ArrayList<Map.Entry<String, Integer>> entries = new ArrayList<>(map.entrySet());
	System.out.println("Entries = " + entries);

	for (Map.Entry<String, Integer> entry : entries) {
		System.out.printf("Single [%s = %d]\n", entry.getKey(), entry.getValue());
	}
}

**Output:**

Entries = [a=1, b=2, c=3]
Single [a = 1]
Single [b = 2]
Single [c = 3]
```

## getOrDefault()

**getOrDefault()** function has a time complexity of **O(1)**.

```java
public static void main(String[] args) {
	HashMap<String, Integer> map = new HashMap<>();

	map.put("a", 1);
	map.put("b", 2);
	map.put("c", 3);

	System.out.println("map(a) = " + map.getOrDefault("a", -1));
	System.out.println("map(b) = " + map.getOrDefault("b", -1));
	System.out.println("map(m) = " + map.getOrDefault("m", -1));
}

**Output:**

map(a) = 1
map(b) = 2
map(m) = -1
```

