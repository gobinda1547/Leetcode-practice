## Problem name
[1207. Unique Number of Occurrences](https://leetcode.com/problems/unique-number-of-occurrences/description/)


## Solution 1
We will try to find out how many times a number exists. And after calculating the result for each number,
we will try to insert the value inside a HashSet. If the number is unique then HashSet will return true,
otherwise the HashSet will return false. Thus we can have our answer - if there is an unique number of 
occurrence or not.


#### Code
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


#### Time complexity
Every time for calculating the occurrence of one value - we had to traverse entire array - which is (n-1),
where n is the length of the array. And we have calculated the occurrence for each number of the array, so
the time complexity is n*(n-1) which is ultimately O(n^2).


#### Space complexity
The space complexity is O(n), since we used only a boolean array which is as long as the input array is, 
Also the HashSet could be as long as the input array is. So the final space complexity = O(n) for boolean
array + O(n) for HashSet = which is ultimately O(n)




## Solution 2
We will traverse the input array once and generate a map which will hold the number as a KEY and the occurrence
number as a VALUE. Then we will traverse the entire MAP and try to put each occurrence number ( the Map.Entry value)
into a HashSet, If the HashSet returns FALSE then we will have our answer as false cause we find duplicate occurrence
in the HashSet, otherwise when we will complete the entire MAP traversal then we can say the all the occurrences are
unique. 


#### Code
```java
class Solution {
    public boolean uniqueOccurrences(int[] arr) {
        HashMap<Integer, Integer> hashMap = new HashMap();

        for (int i=0; i<arr.length; i++) {
            int key = arr[i];
            if (hashMap.containsKey(key)) {
                hashMap.put(key, hashMap.get(key) + 1);
            } else {
                hashMap.put(key, 1);
            }
        }

        HashSet<Integer> hashSet = new HashSet();
        for (Map.Entry<Integer, Integer> mapEntry: hashMap.entrySet()) {
            if (false == hashSet.add(mapEntry.getValue())) {
                return false;
            }
        }

        return true;
    }
}
```


#### Time complexity
For calculating the HashMap we traverse the input array once so O(n) + We traverse entire Map to generate 
the HashSet so O(m) where m is the distinct input number. Total distinct number will be <= size of the input array.
So ultimately the time complexity is O(n).


#### Space complexity
Same as the time complexity. The HashMap can have a length of as much as the input array is so O(n). The hashSet can
have a length of m, where m is the distinct input number. So the complexity should be O(n) + O(m) = which is ultimately
O(n).
