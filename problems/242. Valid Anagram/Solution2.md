### Problem name
[242. Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)


### Solution approch
Since anagram have something common, so we will use that property to calculate a hash value for each of the input. And if the hash value matches then we will say they are valid anagram. Now to calculate the hash value we will use an integer array of length 26, where we will store each character's occurrence number. Cause each anagram will have same occurrence number.


### Code
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] sHash = hashValue(s);
        int[] tHash = hashValue(t);
        return isArraySame(sHash, tHash);
    }

    private int[] hashValue(String input) {
        int[] retValue = new int[26];
        for (int i=0; i<input.length(); i++) {
            int position = input.charAt(i) - 'a';
            retValue[position]++;
        }
        return retValue;
    }

    private boolean isArraySame(int[] input1, int[] input2) {
        if (input1.length != input2.length) {
            return false;
        }
        for(int i=0; i<input1.length; i++) {
            if (input1[i] != input2[i]) {
                return false;
            }
        }
        return true;
    }
}
```


### Time complexity
We have 3 loops here. 1 for calculating the first hash value which have complexity of O(n) - where n is the length of input String s.
Then 2 for calculating the second hash value - which has complexity of O(m) - where m is the length of the input String t. And finally the 3 loop to calculate if both input array is same or not - which has a complexity of O(26). So finally the complexity can be calculated by O(n) + O(m) + O(26) = which is ultimately O(n+m).


### Space complexity
The space complexity is constant here cause we only used 2 character array of length 26.
