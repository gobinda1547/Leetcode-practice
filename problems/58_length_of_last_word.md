## Problem name
[58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)


## Solution 1
By using java split API, we can easily solve this problem. When we will split the input string by an empty string (" "), then all the words will be returned from that API, and by accessing the last string's size we can have our answer.


#### Code
```java
class Solution {
    public int lengthOfLastWord(String s) {
        String[] splitedValue = s.split(" ");
        if(splitedValue.length == 0) {
            return 0;
        }
        return splitedValue[splitedValue.length-1].length();
    }
}
```


#### Time complexity
The split() API will generate the result with complexity O(n) - where n is the length of the input string s. So O(n) is our entire complexity here.

#### Space complexity
Though we are using String[] but ultimately it's gonna take memory as the length of the input string s. 
So our space complexity is O(n) when n is the length of the input string s.




## Solution 2
In this approch we will start traversing from the right side of the input string. while traversing we could have 2 possible cases, either the current character will be a space or alphabet. When we will find the alphabet then we will just increase our wordCounter variable, on the other hand when we will find current character is space then we can have another 2 cases. Whether the counter is 0 or not. If the counter is not zero that means we already found a word - alphabet previously. So we will return the result. If the counter is zero - that means we didn't find any alphabet previous - so we will ignore the current character & start traversing again.


#### Code
```java
class Solution {
    public int lengthOfLastWord(String s) {
        int counter = 0;
        for (int i=s.length()-1; i>=0; i--) {
            if (s.charAt(i) == ' ') {
                if(counter != 0) {
                    return counter;
                }
            } else {
                counter++;
            }
        }
        return counter;
    }
}
```


#### Time complexity
In worst cases we may not find any match. In that case we will have a complexity of O(n) - where n is the length of the input string s.

#### Space complexity
We only used an integer variable extra. So the space complexity is constant and it's O(1).