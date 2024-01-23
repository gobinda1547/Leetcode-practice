### Problem name
[14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)


### Solution approch
Brute force solution


### Code
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        for(int i=0; i<strs[0].length(); i++) {
            for(int j=1; j<strs.length; j++) {
                if(i >= strs[j].length() || strs[0].charAt(i) != strs[j].charAt(i)) {
                    return strs[0].substring(0, i);
                }
            }
        }
        return strs[0];
    }
}
```


### Time complexity
O(n^2)


### Space complexity
No extra space.
