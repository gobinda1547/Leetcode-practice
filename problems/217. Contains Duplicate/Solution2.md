### Problem name
[217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)


### Solution approch
First we are gonna sort the input array, then we will traverse the array once with O(n) complexity to find out the duplicate occurrence, cause now the array is sorted - so any duplicate occurrence will be placed next to another. And if we find any
such pair (next to another same item) then we will have our answer.


### Code
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        for (int i=0; i<nums.length-1; i++) {
            if (nums[i] == nums[i+1]) {
                return true;
            }
        }
        return false;
    }
}
```


### Time complexity
We are sorting the input array by using Arrays.sort() - which gives us result using O(nlog(n)) + we have traversed the input array once which will add the complexity by O(n). So ultimately the complexity is O(nlog(n)).


### Space complexity
We didn't use any extra memory.
