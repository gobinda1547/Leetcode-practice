### Problem name
[392. Is Subsequence](https://leetcode.com/problems/is-subsequence/description/)


### Solution approch
We will follow the general approch to solve this problem. Here we have to find out if s is subsequence of t. that means s could be smaller than t for valid case. So we will use 2 pointer - 1 pointing over s string and the other one pointing over t string. Both the pointer will be initialized by 0. Then we will start matching s[pointer1] & t[pointer2]. If they match then we will increase both the pointers and if they don't match then we will increase only the pointer2. Cause only the t String can have extra characters. Thus if we couldn't find a match for any character in s String - we can return our result immediately. And if the matching loop ends normally that means we have a valid subsequence.


### Code 1
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        
        int pointer1 = 0;
        int pointer2 = 0;

        while (pointer1 < s.length()) {
            boolean isMatchFound = false;
            while (pointer2 < t.length()) {
                if (s.charAt(pointer1) == t.charAt(pointer2)) {
                    isMatchFound = true;
                    pointer1++;
                    pointer2++;
                    break;
                } else {
                    pointer2++;
                }
            }
            if(isMatchFound == false) {
                return false;
            }
        }

        return true;
    }
}
```


### Time complexity
Though there is a nested while loop but the complexity of this algorithm is O(n) where n is the length of t String. Cause we are not going to traverse the t string 2nd time.


### Space complexity
2 integer variables were declared. So space complexity is constant 


### Code 2
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        
        int pointer1 = 0;
        int pointer2 = 0;

        while (pointer1 < s.length() && pointer2 < t.length()) {
            if (s.charAt(pointer1) == t.charAt(pointer2)) {
                pointer1++;
                pointer2++;
            } else {
                pointer2++;
            }
        }

        return pointer1 == s.length();
    }
}
```