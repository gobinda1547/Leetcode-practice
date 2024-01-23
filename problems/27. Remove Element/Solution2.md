### Problem name
[27. Remove Element](https://leetcode.com/problems/remove-element/description/)


### Solution approch
The best solution is not to use any extra memory here. We can do it by swapping the values. We will keep an extra value to track in which position we can put the current item. If the current item is equal to the input val, then we will not increase the tracker value. Thus we can remove all the matching element from the left.


### Code
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0;
        for (int i=0; i<nums.length; i++) {
            if (nums[i] != val) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
}
```


### Time complexity
O(n).


### Space complexity
No extra memory.