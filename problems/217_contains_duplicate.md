## Problem name
[217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/)


## Solution 1
We are going to take a number, and loop through the entire array whether any second occurrence is present or not,
If it is present then we can have our answer. We must have to do this for all the input numbers. So you can assuming
that the time complexity is going to be O(n^2).


#### Code
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


#### Time complexity
As you can see, we are searching to the second occurrence for each of the number from the input array. And each
searching operation for one number is taking (n-1). So the complexity is n*(n-1) for all the numbers. Which is 
ultimately O(n^2).


#### Space complexity
We didn't use any extra memory.




## Solution 2
First we are gonna sort the input array, then we will traverse the array once with O(n) complexity to find out the duplicate occurrence, cause now the array is sorted - so any duplicate occurrence will be placed next to another. And if we find any
such pair (next to another same item) then we will have our answer.


#### Code
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


#### Time complexity
We are sorting the input array by using Arrays.sort() - which gives us result using O(nlog(n)) + we have traversed the input array once which will add the complexity by O(n). So ultimately the complexity is O(nlog(n)).


#### Space complexity
We didn't use any extra memory.




## Solution 3
We are going to traverse the input array once, and we will try to insert each item in a HashSet while looping through. If the HashSet can add an item then the item is unique. On the other hand - When the HashSet won't be able to add an item then that item is duplicate. Thus we can have our answer.


#### Code
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


#### Time complexity
We are looping through the input array once, so the complexity is O(n).


#### Space complexity
We used a HashSet - which can have items as much as the size of the input array. So the complexity is O(n). Think of input {1,2,3,4,5,6} - this will make the HashSet length 6.