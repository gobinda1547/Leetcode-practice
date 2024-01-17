### Problem name
[58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)


### Solution approch
By using java split API, we can easily solve this problem. When we will split the input string by an empty string (" "), then all the words will be returned from that API, and by accessing the last string's size we can have our answer.


### Code
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


### Time complexity
The split() API will generate the result with complexity O(n) - where n is the length of the input string s. So O(n) is our entire complexity here.

### Space complexity
Though we are using String[] but ultimately it's gonna take memory as the length of the input string s. 
So our space complexity is O(n) when n is the length of the input string s.