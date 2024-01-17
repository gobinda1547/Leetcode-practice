### Problem name
[242. Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)


### Solution approch
Each anagram have the same value - If we sorted them alphabetically. Lets say we have "cat" & "tac" - If we sorted both of them alphabetically then we will have "act" for both of them. Thus we can validating Anagram or not. Now java don't have API to sort a String alphabetically but we can do the same thing by converting the String to Character Array.


### Code
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


### Time complexity
Since we are sorting the array using Arrays.sort() API, so the time complexity will be O(nlog(n)).


### Space complexity
We have used 2 Character array. Input1 array will have the length of input String s (lets say its n).
And Input2 array will have the length of input String t (lets say its m). So the space complexity will be
O(n+m). 
