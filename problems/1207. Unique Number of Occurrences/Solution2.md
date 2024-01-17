### Problem name
[1207. Unique Number of Occurrences](https://leetcode.com/problems/unique-number-of-occurrences/description/)


### Solution approch
We will traverse the input array once and generate a map which will hold the number as a KEY and the occurrence
number as a VALUE. Then we will traverse the entire MAP and try to put each occurrence number ( the Map.Entry value)
into a HashSet, If the HashSet returns FALSE then we will have our answer as false cause we find duplicate occurrence
in the HashSet, otherwise when we will complete the entire MAP traversal then we can say the all the occurrences are
unique. 


### Code
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


### Time complexity
For calculating the HashMap we traverse the input array once so O(n) + We traverse entire Map to generate 
the HashSet so O(m) where m is the distinct input number. Total distinct number will be <= size of the input array.
So ultimately the time complexity is O(n).


### Space complexity
Same as the time complexity. The HashMap can have a length of as much as the input array is so O(n). The hashSet can
have a length of m, where m is the distinct input number. So the complexity should be O(n) + O(m) = which is ultimately
O(n).
