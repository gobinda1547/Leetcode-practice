### Problem name
[1929. Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/description/)

### Solution approch
In kotlin just return input + input, this will automatically concat the input array with it. Cause Kotlin internally supports operator function for + sign.

### Code
```kotlin
class Solution {
    fun getConcatenation(nums: IntArray): IntArray {
        return nums + nums;
    }
}
```


### Time complexity
Kotlin will concat with complexity O(1).

### Space complexity
We are using an IntArray to return the result which will have size 2*n  where n is the size of the IntArray.
So the space complexity is O(n)