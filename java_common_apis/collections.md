## java.util.Collections


## Collections.sort(List list)

**sort(List list)**: Sorts the specified list using the natural ordering of its elements, offering **O(n log n)** complexity with various sorting algorithms depending on the data type. Useful for general-purpose sorting of list contents.

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

**sort(List list, Comparator comparator)**: Sorts the specified list using the provided comparator for defining custom sorting criteria, this function also uses **O(n log n)** complexity. Versatile for sorting based on specific logic.

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

**reverse(List list)**: Reverses the order of elements in the specified list, providing **O(n)** time complexity. Simple and efficient for changing the order of list elements.

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
