## java.util.Comparator

Here we will learn about object sorting which is also called as structured sort. The main thing to remember while using Comparator is that the override method compare() should return #negative value when you want the #item1 to be #smaller, should return #positive value when you want the #item1 is #greater with compared to #item2.


Suppose we have below Student class. Firstly we will make a list of student as input - then we will sort them id-wise & age-wise both in Ascending and Descending order.

```java
class Student {
	String name;
	int id;
	int age;

	public Student(String name, int id, int age) {
		this.name = name;
		this.id = id;
		this.age = age;
	}

	@Override
	public String toString() {
		return String.format("[name = %s, id = %d, age = %d]", name, id, age);
	}
}
```

#### To sort student list in Ascending order based on ID value
```java
class AscendingSortById implements Comparator<Student> {
	public int compare(Student student1, Student student2) {
		return student1.id - student2.id;
	}
}
```

#### To sort student list in Descending order based on ID value
```java
class DescendingSortById implements Comparator<Student> {
	public int compare(Student student1, Student student2) {
		return student2.id - student1.id;
	}
}
```

#### To sort student list in Ascending order based on AGE value
```java
class AscendingSortByAge implements Comparator<Student> {
	public int compare(Student student1, Student student2) {
		return student1.age - student2.age;
	}
}
```

#### To sort student list in Descending order based on AGE value
```java
class DescendingSortByAge implements Comparator<Student> {
	public int compare(Student student1, Student student2) {
		return student2.age - student1.age;
	}
}

```


#### Full code
```java
public class Main {

	public static void main(String[] args) {
		ArrayList<Student> studentList = new ArrayList<>();

		studentList.add(new Student("bijoy", 3, 20));
		studentList.add(new Student("gobinda", 1, 30));
		studentList.add(new Student("nayon", 4, 22));
		studentList.add(new Student("joy", 2, 25));

		printList("raw input list", studentList);

		Collections.sort(studentList, new AscendingSortById());
		printList("after applying ascending sort by ID", studentList);

		Collections.sort(studentList, new DescendingSortById());
		printList("after applying descending sort by ID", studentList);

		Collections.sort(studentList, new AscendingSortByAge());
		printList("after applying ascending sort by age", studentList);

		Collections.sort(studentList, new DescendingSortByAge());
		printList("after applying descending sort by age", studentList);
	}

	static void printList(String message, ArrayList<Student> studentList) {
		System.out.println(message);
		for (Student student : studentList) {
			System.out.println(student);
		}
		System.out.println();
	}
}
```


#### Full output
```java
raw input list
[name = bijoy, id = 3, age = 20]
[name = gobinda, id = 1, age = 30]
[name = nayon, id = 4, age = 22]
[name = joy, id = 2, age = 25]

after applying ascending sort by ID
[name = gobinda, id = 1, age = 30]
[name = joy, id = 2, age = 25]
[name = bijoy, id = 3, age = 20]
[name = nayon, id = 4, age = 22]

after applying descending sort by ID
[name = nayon, id = 4, age = 22]
[name = bijoy, id = 3, age = 20]
[name = joy, id = 2, age = 25]
[name = gobinda, id = 1, age = 30]

after applying ascending sort by age
[name = bijoy, id = 3, age = 20]
[name = nayon, id = 4, age = 22]
[name = joy, id = 2, age = 25]
[name = gobinda, id = 1, age = 30]

after applying descending sort by age
[name = gobinda, id = 1, age = 30]
[name = joy, id = 2, age = 25]
[name = nayon, id = 4, age = 22]
[name = bijoy, id = 3, age = 20]
```
