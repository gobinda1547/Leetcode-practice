## java.lang.String


#### length()

String class have the method **length()** to share it's size. It is important to remember that the complexity of the length() is **O(1)** - since String is immutable.

```java
public static void main(String[] args) {
	String name = "gobinda";
	int nameLength = name.length();
	System.out.println("Size of name : " + nameLength);
}

**Output:**

Size of name : 7
```

#### substring()

The are 2 substring APIs. All of them are zero base indexed. Both have a time complexity of **O(n)** - where n is the length of the String. The first substring API takes only one integer as input (startIndex) and returns a new String containing all the characters started from the startIndex (**inclusive**). The second substring API takes 2 integer param as input (startIndex and endIndex) and returns a new String containing all the characters started from the startIndex (**inclusive**) and ended at endIndex (**exclusive**).

```java
public static void main(String[] args) {
	String input = "abcdefghij";

	String subString1 = input.substring(3);
	System.out.println("First subString : " + subString1);

	String subString2 = input.substring(3, 5);
	System.out.println("Second subString : " + subString2);
}

**Output:**

First subString : defghij
Second subString : de
```

#### indexOf()

This API can be used to find out the position of a specific character or even a String. This API is also zero indexed base. This API will return -1 incase the searching text or character not found in the input String. It could also take a integer param (fromPosition) as input. In that case - it will start searching the text from that position. This API has a time complexity of **O(nm)** where n is the length of the input String and m is the length of the searching text. 


```java
public static void main(String[] args) {
	String input = "gobinda1547@gmail.com";

	int position1 = input.indexOf('a');
	System.out.println("Value of position1 : " + position1);

	int position2 = input.indexOf('a', 7);
	System.out.println("Value of position2 : " + position2);

	int position3 = input.indexOf("1547");
	System.out.println("Value of position3 : " + position3);

	int position4 = input.indexOf("joy");
	System.out.println("Value of position4 : " + position4);
}

**Output:**

Value of position1 : 6
Value of position2 : 14
Value of position3 : 7
Value of position4 : -1
```


#### A simple usecase of indexOf()

We will split an email address into 2 parts (user part + domain name part).

```java
public static void main(String[] args) {
	String input = "gobinda1547@gmail.com";

	int breakPoint = input.indexOf("@");
	System.out.println("Break point at : " + breakPoint);

	String firstPart = input.substring(0, breakPoint);
	System.out.println("First part = " + firstPart);

	String secondPart = input.substring(breakPoint + 1);
	System.out.println("Second part = " + secondPart);
}

**Output:**

Break point at : 11
First part = gobinda1547
Second part = gmail.com
```

#### replace()

This function replace all the occurance at once. It has a complexity of **O(nm)**. It can replace by **char** or even **String**.

```java
public static void main(String[] args) {
	String input1 = "123412341234";
	String output1 = input1.replace('1', '0');
	System.out.println("First output : " + output1);
	
	String input2 = "abcdabcdabcd";
	String output2 = input2.replace("bcd", "xyz");
	System.out.println("Second output : " + output2);
}

**Output:**

First output : 023402340234
Second output : axyzaxyzaxyz
```

#### toLowerCase() & toUpperCase()

Use these APIs to convert the input string to upper case or lower case. Both of the APIs have **O(n)** complexity.

```java
public static void main(String[] args) {
	String input = "MyNameIsGobinda";

	String lowerCaseOutput = input.toLowerCase();
	System.out.println("Lower case : " + lowerCaseOutput);

	String upperCaseOutput = input.toUpperCase();
	System.out.println("Upper case : " + upperCaseOutput);
}

**Output:**

Lower case : mynameisgobinda
Upper case : MYNAMEISGOBINDA
```