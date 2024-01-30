## Problem name
[150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/description/?envType=daily-question&envId=2024-01-30)


## Solution 1
The given input represents an expression in 'Reverse polish notation'. That means we will first receive the 2 number and then we will get the operation we have to perform, then the result will represent a number. so on. So we can solve this problem by using a stack. When we will receive a number then we will add it to the stack, when we will receive any operator then we will pop 2 items from the stack and perform the operation between them - And we will push the result into the stack. Since the result is always valid - so at last we will have the answer in the stack.


#### Code
```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack();
        for (int i=0,first,second; i<tokens.length; i++) {
            String t = tokens[i];

            if (t.equals("+")) {
                second = stack.pop();
                first = stack.pop();
                stack.add (first + second);
            } else if (t.equals("-")) {
                second = stack.pop();
                first = stack.pop();
                stack.add (first - second);
            } else if (t.equals("*")) {
                second = stack.pop();
                first = stack.pop();
                stack.add (first * second);
            }  else if (t.equals("/")) {
                second = stack.pop();
                first = stack.pop();
                stack.add (first / second);
            } else {
                stack.add(Integer.parseInt(t));
            }
        }
        return stack.pop();
    }
}
```


#### Time complexity
O(n) cause we have traversed our input array once & all the stack push-pop operations are of O(1).


#### Space complexity
To calculate 6 number, we must need 5 operator, so the input length is 11 where 6 are numbers.
To calculate 7 number, we must need 6 operator, so the input length is 13 where 7 are numbers.
So we can say that approximately there will be (n/2) numbers, that means In worst case our stack can have (n/2) numbers.
Which is ultimately O(n) space complexity.


## Solution 2
Is similar to solution 1 - but note that we can solve the problem without using 2 extra variable (first & second). Below is the code.



#### Code
```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack();
        for (int i=0; i<tokens.length; i++) {
            String t = tokens[i];

            if (t.equals("+")) {
                stack.add (stack.pop() + stack.pop());
            } else if (t.equals("-")) {
                stack.add (-stack.pop() + stack.pop());
            } else if (t.equals("*")) {
                stack.add (stack.pop() * stack.pop());
            }  else if (t.equals("/")) {
                stack.add ((int)((1.0/stack.pop()) * stack.pop()));
            } else {
                stack.add(Integer.parseInt(t));
            }
        }
        return stack.pop();
    }
}
```