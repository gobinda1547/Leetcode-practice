### Problem name
[217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)


### Solution approch
We are going to take a number, and loop through the entire array whether any second occurrence is present or not,
If it is present then we can have our answer. We must have to do this for all the input numbers. So you can assuming
that the time complexity is going to be O(n^2).


### Code
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        for (int i=0; i<nums.length; i++) {
            for (int j=i+1; j<nums.length; j++) {
                if (nums[i] == nums[j]) {
                    return true;
                }
            }
        }
        return false;
    }
}
```


### Time complexity
As you can see, we are searching to the second occurrence for each of the number from the input array. And each
searching operation for one number is taking (n-1). So the complexity is n*(n-1) for all the numbers. Which is 
ultimately O(n^2).


### Space complexity
We didn't use any extra memory.
