## java.util.Collections

#### Collections class works with List of any type. It doesn't work with Array. To work with Array you should use Arrays API. Like to sort a list of items you have to use Collections.sort() API. On the other hand, to sort an array of any type you can use Arrays.sort() API.

## Collections.sort(List list)

This API Sorts the specified list with **O(n log n)** complexity. If list item type is a **custom user defined class** - then you must have to use **Collections.sort(List list, Comparator comparator)** API. For normal wrapper classes like **Integer**, **Double**, **Float** classes - you can use this API.

```java
public static void main(String[] args) {
	ArrayList<Integer> myList = new ArrayList<>();

	myList.add(5);
	myList.add(4);
	myList.add(9);

	System.out.println("(1) Before sorting : " + myList);
	Collections.sort(myList);
	System.out.println("(1) After sorting : " + myList);

	ArrayList<String> stringList = new ArrayList<>();

	stringList.add("gobinda");
	stringList.add("joya");
	stringList.add("joy");
	stringList.add("bijoy");

	System.out.println("(2) Before sorting : " + stringList);
	Collections.sort(stringList);
	System.out.println("(2) After sorting : " + stringList);
}

**Output:**

(1) Before sorting : [5, 4, 9]
(1) After sorting : [4, 5, 9]
(2) Before sorting : [gobinda, joya, joy, bijoy]
(2) After sorting : [bijoy, gobinda, joy, joya]
```



## Collections.sort(List list, Comparator comparator)

This API Sorts the specified list with **O(n log n)** complexity.

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

// sorting age wise then roll wise
static class StudentSortener implements Comparator<Student> {
	public int compare(Student s1, Student s2) {
		if (s1.age == s2.age) {
			return s1.roll - s2.roll;
		}
		return s2.age - s1.age;
	}
}

public static void main(String[] args) {
	ArrayList<Student> studentList = new ArrayList<>();

	studentList.add(new Student(1, 10));
	studentList.add(new Student(4, 6));
	studentList.add(new Student(3, 10));
	studentList.add(new Student(5, 10));
	studentList.add(new Student(2, 8));

	System.out.println("Before sorting : " + studentList);
	Collections.sort(studentList, new StudentSortener());
	System.out.println("After sorting : " + studentList);
}

**Output:**

Before sorting : [Age:10(1), Age:6(4), Age:10(3), Age:10(5), Age:8(2)]
After sorting : [Age:10(1), Age:10(3), Age:10(5), Age:8(2), Age:6(4)]
```


## Collections.reverse(List list)

This API reverses the order of elements in the list by **O(n)** time complexity. It has nothing to worry about the **Comparator**. You can use this method for any data type (**Integer**, **Double**, **Float**, **Custom defined class**, etc).

```java
public static void main(String[] args) {
	ArrayList<Integer> myList = new ArrayList<>();

	myList.add(5);
	myList.add(4);
	myList.add(9);

	System.out.println("(1) Before reversing : " + myList);
	Collections.reverse(myList);
	System.out.println("(1) After reversing : " + myList);
}

**Output:**

(1) Before reversing : [5, 4, 9]
(1) After reversing : [9, 4, 5]
```
