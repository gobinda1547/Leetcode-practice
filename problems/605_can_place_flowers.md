## Problem name
[605. Can Place Flowers](https://leetcode.com/problems/can-place-flowers/description/)


## Solution 1
We will traverse the entire array once. while traversing for each position we can get 0 and 1. Now we will track isLeftSide okay or not for each index by a boolean variable. When traversing if we get a 1 - then simply for the next position isLeftSize will be not okay so we will mark it as false and if we get a 0 then again we can have 2 case whether left side is okay or not. If left side is okay then we calculate the right side okay not. If both side okay then we will increase our counter. On the other hand if left side is not okay then for the next position left side is going to be okay, so we will set isLeftOkay = true and continue traversing the next position. Thus we will have the counter finally.


#### Code
```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int counter = 0;

        if(flowerbed.length == 1) {
            counter = (flowerbed[0] == 0) ? 1 : 0;
            return n <= counter;
        }

        boolean isLeftOkay = true;

        for (int i=0; i<flowerbed.length; i++) {
            if (flowerbed[i] != 0) {
                isLeftOkay = false;
                continue;
            }
            if (isLeftOkay == false) {
                isLeftOkay = true;
                continue;
            }
            
            boolean rCon1 = i+1 == flowerbed.length;
            boolean rCon2 = i+1 < flowerbed.length && flowerbed[i+1] == 0;

            if (rCon1 || rCon2) {
                counter++;
                isLeftOkay = false;
            } 
        }

        return n <= counter;
    }
}
```


#### Time complexity
O(n) - since we loop though once in the entire array.


#### Space complexity
Constant space used so O(1).