## Problem name
[929. Unique Email Addresses](https://leetcode.com/problems/unique-email-addresses/description/)


## Solution 1
We have to write such a hash function which will return the same hashValue for each unique email address. One way we can easily generate this by removing dots(.) and plus(+) which is described in the problem description. And then these hash values will be stored in the HashSet so that finally we can count - how many unique addresses are there. Now we can generate the hash value by using string class provided api and also by traversing each character by ourselves. Both the solutions are below.


#### Code 1
```java
class Solution {
    public int numUniqueEmails(String[] emails) {
        HashSet<String> hashSet = new HashSet();
        for (String current : emails) {
            hashSet.add(generateHashValue(current));
        }
        return hashSet.size();
    }

    private String generateHashValue(String email) {
        int positionOfAt = email.indexOf('@');

        String domainName = email.substring(positionOfAt + 1, email.length());
        String localName = email.substring(0, positionOfAt);

        localName = localName.replace(".", "");
        int positionOfPlus = localName.indexOf("+");
        if(positionOfPlus != -1) {
            localName = localName.substring(0, positionOfPlus);
        }

        return localName + "@" + domainName;
    }
}
```

#### Code 2
```java
class Solution {
    public int numUniqueEmails(String[] emails) {
        HashSet<String> hashSet = new HashSet();
        for (String current : emails) {
            hashSet.add(generateHashValue(current));
        }
        return hashSet.size();
    }

    private String generateHashValue(String email) {
        char[] ch = email.toCharArray();
        boolean atFound = false;
        int validChar = 0;
        for (int i=0; i<ch.length; i++) {
            if (atFound == false) {
                if (ch[i] == '.') {
                    continue;
                } else if (ch[i] == '+') {
                    while (ch[++i] != '@');
                    atFound = true;
                } else if (ch[i] == '@') {
                    atFound = true;
                }
            }
            ch[validChar++] = ch[i];
        }

        return String.valueOf(ch, 0, validChar);
    }
}
```


#### Time complexity
Both the solution has time complexity of O(mn) - where m is the maximum length possible for a single email and n is the total number of input emails. Though in the first solution generateHashFun will provide complexity of 5m~6m but which is ultimately O(m) - and that is why the final time complexity is O(mn)


#### Space complexity
The hashSet we used may have all the input emails in it - in worst case. So the complexity is O(n) - where n is the number of input emails.