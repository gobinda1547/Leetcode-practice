### Problem name
[58. Length of Last Word](https://leetcode.com/problems/length-of-last-word/description/)


### Solution approch
In this approch we will start traversing from the right side of the input string. while traversing we could have 2 possible cases, either the current character will be a space or alphabet. When we will find the alphabet then we will just increase our wordCounter variable, on the other hand when we will find current character is space then we can have another 2 cases. Whether the counter is 0 or not. If the counter is not zero that means we already found a word - alphabet previously. So we will return the result. If the counter is zero - that means we didn't find any alphabet previous - so we will ignore the current character & start traversing again.


### Code
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


### Time complexity
In worst cases we may not find any match. In that case we will have a complexity of O(n) - where n is the length of the input string s.

### Space complexity
We only used an integer variable extra. So the space complexity is constant and it's O(1).