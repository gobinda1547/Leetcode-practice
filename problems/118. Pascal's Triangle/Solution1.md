### Problem name
[118. Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/description/)


### Solution approch
Brute force solution. We will add the first row for free. Then we will iterate from the next row. And for each item we will try to fetch the previous row's nth and (n-1)th value. Thus there sum will be the new value. Now there could be situation like previous row may not have the nth or (n-1)th position. In that case we have to handle them so that we are not getting any ArrayIndexOutOfBound exception.


### Code
```java
class Solution {

    ArrayList<List<Integer>> answer;

    public List<List<Integer>> generate(int numRows) {
        answer = new ArrayList();

        ArrayList<Integer> firstItem = new ArrayList();
        firstItem.add(1);
        answer.add(firstItem);

        for (int currentRow=1; currentRow<numRows; currentRow++) {
            ArrayList<Integer> currentValues = new ArrayList();
            int value1, value2;

            for (int currentPos=0; currentPos<=currentRow; currentPos++) {
                value1 = dd(currentRow-1, currentPos-1);
                value2 = dd(currentRow-1 , currentPos);
                currentValues.add(value1 + value2);
            }

            answer.add(currentValues);
        }

        return answer;
    }

    private int dd(int rowNumber, int position) {
        if (position < 0 || rowNumber < position) {
            return 0;
        }
        return answer.get(rowNumber).get(position);
    }
}
```


### Time complexity
for each p'th row we are looping from 0 to p, and since we have n number of row. So the time complexity is 1+2+3+...+n which is ultimately O(n^2).


### Space complexity
In each iteration we are adding consecutive values so the space complexity also O(n^2).