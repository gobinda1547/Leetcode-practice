### Problem name
[1299. Replace Elements with Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/description/)


### Solution approch
We are going to apply the general approch here. We will traverse from the last to first of the input array. We will also hold a currentMax value then while traversing we will replace existing items with the currentMax value and then we will also update the currentMax value by checking with the currentItem.


### Code
```java
class Solution {
    public int[] replaceElements(int[] arr) {
        int currentMax = -1;
        for (int i=arr.length-1; i>=0; i--) {
            int currentNumber = arr[i];
            arr[i] = currentMax;
            currentMax = Math.max(currentMax, currentNumber);
        }
        return arr;
    }
}
```


### Time complexity
It's O(n) since we traverse the entire array once.


### Space complexity
We just used one extra variable to store an integer. so the space complexity is constant which is O(1)