## Problem name
[27. Remove Element](https://leetcode.com/problems/remove-element/description/)


## Solution approch
The easiest solution is to traverse each value in the array, if the value is not equal to the input val then store it in a new array. And finally copy the new array to the input array and return the result.


#### Code
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int[] temp = new int[nums.length];
        int k = 0;
        for (int i=0, tempPosition=0; i<nums.length; i++) {
            if (nums[i] != val) {
                k++;
                temp[tempPosition++] = nums[i];
            }
        }
        for (int i=0; i<nums.length; i++) {
            nums[i] = temp[i];
        }
        return k;
    }
}
```


#### Time complexity
Time complexity is O(n) - though in worst case both loop will be running from 0 to n-1. Which is result as O(2n) - but it's again ultimately O(n).


#### Space complexity
We are using one extra array - which can have numbers as much as the input array in worst case. So the space complexity is O(n).




## Solution 2
The best solution is not to use any extra memory here. We can do it by swapping the values. We will keep an extra value to track in which position we can put the current item. If the current item is equal to the input val, then we will not increase the tracker value. Thus we can remove all the matching element from the left.


#### Code
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


#### Time complexity
O(n).


#### Space complexity
No extra memory.