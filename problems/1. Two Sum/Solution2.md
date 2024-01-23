### Problem name
1. Two Sum


### Solution approch
Since the target is already provided as an input. So if we loop through each number by a for loop then we will be able to find out what is the required number to match with the target. Suppose our target is 9 and in the array at first position we got number 3, that means we need a 6 to match with the target. So we can somehow know that whether there is a 6 or not - and what is it's position, then we will have our answer. To store that information we can use a HashMap. So the key will be the number and the value will be the position. Since HashMap get() works in O(1). So we will have our time complexity O(n).


### Code
```java
/**
* It is possible that this function is being invoked when the activity or fragment
* is destroyed already, In that case the binding object will be null. So we have to
* handle this using try-catch block. Also it's a good practice to destroy previous
* native ad while showing the new one to ignore memory leak.
*/
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> hashMap = new HashMap();
        for(int i=0, needed=0; i<nums.length; i++) {
            needed = target - nums[i];
            if (hashMap.containsKey(needed)) {
                return new int[] {i, hashMap.get(needed)};
            }
            hashMap.put(nums[i], i);
        }
        return null;
    }
}
```


### Time complexity
O(n) - already discussed the reason in solution approch.


### Space complexity
we have used an extra HashMap. In worst case it can the upto the size of the input array. So the space complexity is O(n) - where n is the size of the input array.