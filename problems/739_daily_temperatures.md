## Problem name
[739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/description/)


## Solution 1
For the input array, we will travers each temperature once. And we will try to decide whether current temperature is the wormer then how many previous temperatures - cause the different will be the answer for that particular position. To get these previous temperatures we will use a stack. When we will find a warmer temperature then we will calculate the different for that position, and saved it in the answer array, then we will remove that temperature from the stack. Since we are using stack so we won't be able to find out the position of a specific temperature from the input array. So we will create a custom class with 2 parameter (one is the position and the other one is temperature value). And then we will add current temperature in the stack. This should be keep in mind that - for the last temperature we can't calculate the next warmer day since that's the last position. So we have to manually allocate Zero for that.


#### Code
```java
class Solution {

    private class TempInfo {

        int pos, value;

        public TempInfo(int pos, int value) {
            this.pos = pos;
            this.value = value;
        }
    }

    public int[] dailyTemperatures(int[] temp) {
        Stack<TempInfo> stack = new Stack();
        
        int[] answer = new int[temp.length];
        answer[temp.length-1] = 0;

        for (int i=0, cTemp; i<temp.length; i++) {
            cTemp = temp[i];

            while (stack.isEmpty() == false) {
                TempInfo cInfo = stack.peek();
                if(cInfo.value < cTemp) {
                    stack.pop();
                    answer[cInfo.pos] = i - cInfo.pos;
                } else {
                    break;
                }
            }

            stack.add(new TempInfo(i, cTemp));
        }

        return answer;
    }
}
```


#### Time complexity
It  may seem that the complexity is O(n^2) but the truth is that via the while loop - we will process previous temperatures only once then we will remove it from the stack - otherwise we are just breaking the while loop. So ultimately for n temperatures the while loop is going to take another total complexity of O(n). So the final time complexity is O(n).


#### Space complexity
In worst case, (n-1) items could be found in the stack - so the space complexity can be represent with O(n).
Think about a case where - for 9,8,7,6,5,4,3,2,1,10 temperatures input stack size could be maximum (n-1).