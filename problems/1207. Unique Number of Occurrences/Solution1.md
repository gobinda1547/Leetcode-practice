### Problem name
[1207. Unique Number of Occurrences](https://leetcode.com/problems/unique-number-of-occurrences/description/)


### Solution approch
We will try to find out how many times a number exists. And after calculating the result for each number,
we will try to insert the value inside a HashSet. If the number is unique then HashSet will return true,
otherwise the HashSet will return false. Thus we can have our answer - if there is an unique number of 
occurrence or not.


### Code
```java
class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        boolean[] visibility = new boolean[arr.length];
        HashSet<Integer> hashSet = new HashSet();

        for (int i=0; i<arr.length; i++) {
            int counter = 0;
            if (false == visibility[i]) {

                visibility[i] = true;
                counter++;

                for (int j=i+1; j<arr.length; j++) {
                    if (false == visibility[j] && arr[i] == arr[j]) {
                        visibility[j] = true;
                        counter++;
                    }
                }

                if (false == hashSet.add(counter)) {
                    return false;
                }
            }
        }

        return true;
    }
}
```


### Time complexity
Every time for calculating the occurrence of one value - we had to traverse entire array - which is (n-1),
where n is the length of the array. And we have calculated the occurrence for each number of the array, so
the time complexity is n*(n-1) which is ultimately O(n^2).


### Space complexity
The space complexity is O(n), since we used only a boolean array which is as long as the input array is, 
Also the HashSet could be as long as the input array is. So the final space complexity = O(n) for boolean
array + O(n) for HashSet = which is ultimately O(n)
