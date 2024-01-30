## Problem name
[49. Group Anagrams](https://leetcode.com/problems/group-anagrams/description/)


## Solution approch
We will write a hashFunction() to generate the same hash value for these string which goes under one anagram. The idea is simple and the is to sort the values alphabetically. And strings can't be sort alphabetically - I mean there is no direct API - you have to write that code of your own, so what we can do is to convert the string to character array and then sort the character array then again make it string. So finally we will start a loop for each input string - and then we will make the hashValue and we will store the result in a HashMap so that if the same hashValue we find previously, then we can add the new string with the previous answer list accordingly. And finally we will have the output inside hashMap values.


#### Code
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, ArrayList<String>> hashMap = new HashMap();
        for (int i=0; i<strs.length; i++) {
            String hashKey = hashFun(strs[i]);
            
            ArrayList<String> allValues = hashMap.get(hashKey);
            if (allValues == null) allValues = new ArrayList<String>();
            allValues.add(strs[i]);

            hashMap.put(hashKey, allValues);
        }

        return new ArrayList(hashMap.values());
    }

    private String hashFun(String input) {
        char[] convertedValue = input.toCharArray();
        Arrays.sort(convertedValue);
        return new String(convertedValue);
    }
}
```


#### Time complexity
The time complexity is n * m log(m). Where n is the number of input string. And m is the maximum possible input string length.
Since we have sorted every input string that's why it's time complexity is O(n * m log(m)).


#### Space complexity
/* enter space complexity */