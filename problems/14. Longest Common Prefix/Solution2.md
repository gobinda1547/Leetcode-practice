### Problem name
[14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/description/)


### Solution approch
Brute force solution


### Code
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        StringBuilder sb = new StringBuilder("");
        int minLen = getMinimumLength(strs);
        for(int i=0; i<minLen; i++) {
            char ch = strs[0].charAt(i);
            for(int j=1; j<strs.length; j++) {
                if(ch != strs[j].charAt(i)) {
                    return sb.toString();
                }
            }
            sb.append(ch);
        }
        return sb.toString();
    }
    
    public int getMinimumLength(String[] input) {
        int result = Integer.MAX_VALUE;
        for(int i=0; i<input.length; i++) {
            result = Math.min(result, input[i].length());
        }
        return result;
    }
}
```


### Time complexity
O(mn) where m is the value of minimum common prefix length & n is the total number of string.



### Space complexity
O(m) where m is the value of minimum common prefix length.
