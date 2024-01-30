## Problem name
[242. Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)


## Solution 1
Each anagram have the same value - If we sorted them alphabetically. Lets say we have "cat" & "tac" - If we sorted both of them alphabetically then we will have "act" for both of them. Thus we can validating Anagram or not. Now java don't have API to sort a String alphabetically but we can do the same thing by converting the String to Character Array.


#### Code
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        char[] input1 = s.toCharArray();
        char[] input2 = t.toCharArray();

        Arrays.sort(input1);
        Arrays.sort(input2);

        String sorted1 = new String(input1);
        String sorted2 = new String(input2);

        return sorted1.equals(sorted2);
    }
}
```


#### Time complexity
Since we are sorting the array using Arrays.sort() API, so the time complexity will be O(nlog(n)).


#### Space complexity
We have used 2 Character array. Input1 array will have the length of input String s (lets say its n).
And Input2 array will have the length of input String t (lets say its m). So the space complexity will be
O(n+m). 




## Solution 2
Since anagram have something common, so we will use that property to calculate a hash value for each of the input. And if the hash value matches then we will say they are valid anagram. Now to calculate the hash value we will use an integer array of length 26, where we will store each character's occurrence number. Cause each anagram will have same occurrence number.


#### Code
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


#### Time complexity
We have 3 loops here. 1 for calculating the first hash value which have complexity of O(n) - where n is the length of input String s.
Then 2 for calculating the second hash value - which has complexity of O(m) - where m is the length of the input String t. And finally the 3 loop to calculate if both input array is same or not - which has a complexity of O(26). So finally the complexity can be calculated by O(n) + O(m) + O(26) = which is ultimately O(n+m).


#### Space complexity
The space complexity is constant here cause we only used 2 character array of length 26.
