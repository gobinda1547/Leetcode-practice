## java.util.Arrays

#### As the name suggested, Arrays class works with Array of any type. It doesn't work with List. To work with List you should use Collections API. Like to sort a list of items you have to use Collections.sort() API. On the other hand, to sort an array of any type you can use Arrays.sort() API.

## Arrays.sort(T[] t)

Have a complexity of **O(n log n)**. By using **Arrays.sort()** you can sort **int[]**, **double[]**, **float[]**. To sort a custom defined class type you must have to use **Arrays.sort(T[] t, Comparator<T> comparator)** function. The only thing to remember is that if you declare the data type as primitive type like (int, dobule, float) data then you can't use **Arrays.asList()** function. In the below code, we have used the data type as **Integer[]** instead of **int[]** since we have to print the content and we are doing it by using **Arrays.asList()** function.


```java
public static void main(String[] args) {
	Integer[] myList = new Integer[5];

	myList[0] = 4;
	myList[1] = 2;
	myList[2] = 7;
	myList[3] = 1;
	myList[4] = 9;
	
	System.out.println("Before sorting = " + Arrays.asList(myList));
	Arrays.sort(myList);
	System.out.println("After sorting = " + Arrays.asList(myList));
}

**Output:**

Before sorting = [4, 2, 7, 1, 9]
After sorting = [1, 2, 4, 7, 9]
```


## Arrays.sort(T[] t, Comparator comparator)

Have a complexity of **O(n log n)**. This function should be used to sort **custom defined class**.

```java
static class Student {
	int roll, age;

	Student(int roll, int age) {
		this.roll = roll;
		this.age = age;
	}
	
	@Override
	public String toString() {
		return String.format("Age:%d(%d)", age, roll);
	}
}

static class StudentSortener implements Comparator<Student> {
	public int compare(Student s1, Student s2) {
		if (s1.age == s2.age) {
			return s1.roll - s2.roll;
		}
		return s2.age - s1.age;
	}
}

public static void main(String[] args) {
	Student[] studentList = new Student[5];

	studentList[0] = new Student(1, 10);
	studentList[1] = new Student(2, 8);
	studentList[2] = new Student(3, 10);
	studentList[3] = new Student(4, 6);
	studentList[4] = new Student(5, 10);

	System.out.println("Before sorting = " + Arrays.asList(studentList));
	Arrays.sort(studentList, new StudentSortener());
	System.out.println("After sorting = " + Arrays.asList(studentList));
}

**Output:**

Before sorting = [4, 2, 7, 1, 9]
After sorting = [1, 2, 4, 7, 9]
```


## Arrays.fill(T[] t, T initialValue)

**fill()** API has a complexity of **O(n)**

```java
public static void main(String[] args) {
	Integer[] myList = new Integer[10];
	Arrays.fill(myList, 5);
	System.out.println("Array = " + Arrays.asList(myList));
}

**Output:**

Array = [5, 5, 5, 5, 5, 5, 5, 5, 5, 5]
```


## Arrays.asList(T[] t)

This function will return a new **List<T>** But remember that if **T** is a primitive type then this will not work, **T** must have to be Class type like **Integer**, **String**, or **any user defined class type**. Also the returned value can't be directly set to a ArrayList or HashSet type variable, but there is a workaround - check the sample code.

#### Arrays.asList() has a complexity of O(1) since it returns an immutable List

```java
public static void main(String[] args) {
	Integer[] myArray = new Integer[10];
	Arrays.fill(myArray, 3);

	// Arrays.asList() function returns List type
	List<Integer> myList = Arrays.asList(myArray);
	System.out.println("MyList = " + myList);

	// Converting returned value to ArrayList
	ArrayList<Integer> myArrayList = new ArrayList<>(myList);
	System.out.println("MyArrayList = " + myArrayList);

	// Converting returned value to HashSet
	HashSet<Integer> mySet = new HashSet<Integer>(myList);
	System.out.println("MySet = " + mySet);
}

**Output:**

MyList = [3, 3, 3, 3, 3, 3, 3, 3, 3, 3]
MyArrayList = [3, 3, 3, 3, 3, 3, 3, 3, 3, 3]
MySet = [3]
```
