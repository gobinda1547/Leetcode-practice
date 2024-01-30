## Problem name
[1929. Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/description/)

## Solution 1
In kotlin just return input + input, this will automatically concat the input array with it. Cause Kotlin internally supports operator function for + sign.

#### Code
```kotlin
class Solution {
    fun getConcatenation(nums: IntArray): IntArray {
        return nums + nums;
    }
}
```


#### Time complexity
Kotlin will concat with complexity O(1).

#### Space complexity
We are using an IntArray to return the result which will have size 2*n  where n is the size of the IntArray.
So the space complexity is O(n)




## Solution 2
We will declare an array of size - twice as the size of input array. Then we will just insert corresponding items in the new array, then finally return the new array.

#### Code
```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int numLen = nums.length;
        int[] retValue = new int[2 * numLen];
        for (int i=0; i<numLen; i++) {
            retValue[i] = nums[i];
            retValue[i + numLen] = nums[i];
        }
        return retValue;
    }
}
```


#### Time complexity
We are preparing the result with a loop which costs O(n) - where n is the length of the input array.

#### Space complexity
We are using an int array to return the result which will have size 2*n  where n is the size of the input integer array.
So the space complexity is O(n)