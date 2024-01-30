## Problem name
[205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/description/)


## Solution 1
As the problem says we will replace each character of s from t. Now while making the replacement we will track each fromCharacter and toCharacter - so that we can identify if the replacement & replaced characters are new or old. So easily we can track them by using a hash map. Now one hash map is not enough for this solution. Because thing about a case where s = "bd" and t = "mm". Here both 'b' & 'd' are getting replaced by 'm'. So in one hash map its not possible to track which replacement we have already used. So we can use another data structure (hash set) to track that replacement is new or old.


#### Code
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int sLen = s.length();
        int tLen = t.length();

        HashMap<Character, Character> hashMap = new HashMap();
        HashSet<Character> hashSet = new HashSet();
        for (int i=0; i<sLen; i++) {
            char sChar = s.charAt(i);
            char tChar = t.charAt(i);

            if(hashMap.containsKey(sChar)) {
                if(hashMap.get(sChar) != tChar) {
                    return false;
                }
            } else {
                hashMap.put(sChar, tChar);
                if (hashSet.add(tChar) == false) {
                    return false;
                }
            }
        }
        return true;
    }
}
```


#### Time complexity
Time complexity is O(n) - where n is the length of the string. Here s.length = t.length;


#### Space complexity
Space complexity is O(n) for hash map + O(n) for hash set = which is ultimately O(n).