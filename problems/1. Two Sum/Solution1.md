### Problem name
[1. Two Sum](https://leetcode.com/problems/two-sum/description/)


### Solution approch
Since we have to find out the sum of 2 numbers that matches with the target input. So in one approch we can find out all the combination that is possible by using the array by an n^2 loop. The pair for which the sum will be equal to the target will be the answer. 


### Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i=0; i<nums.length-1; i++) {
            for (int j=i+1; j<nums.length;j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i,j};
                }
            }
        }
        return null;
    }
}
```


### Time complexity
We tried to find out all the combinations by 2 for loop. Whose complexity is n*(n-1) which is equivalent to n^2. So the time complexity is O(n^2).


### Space complexity
We didn't use any extra space.