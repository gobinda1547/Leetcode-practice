### Problem name
[217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)


### Solution approch
We are going to traverse the input array once, and we will try to insert each item in a HashSet while looping through. If the HashSet can add an item then the item is unique. On the other hand - When the HashSet won't be able to add an item then that item is duplicate. Thus we can have our answer.


### Code
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> hashSet = new HashSet();
        for (int num : nums) {
            if (false == hashSet.add(num)) {
                return true;
            }
        }
        return false;
    }
}
```


### Time complexity
We are looping through the input array once, so the complexity is O(n).


### Space complexity
We used a HashSet - which can have items as much as the size of the input array. So the complexity is O(n). Think of input {1,2,3,4,5,6} - this will make the HashSet length 6.