## HashMap

### 383. Ransom Note
* Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.

* Each letter in magazine can only be used once in ransomNote.

```
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
		if(ransomNote.length() > magazine.length()) return false;
        int[] charCount=new int[26];
        for(char c:magazine.toCharArray()){
            charCount[c-'a']++;
        }
        for(char c:ransomNote.toCharArray()){
            if(charCount[c-'a'] == 0) return false;
            charCount[c-'a']--;
        }
        return true;
    }
}
"""
Input: ransomNote = "a", magazine = "b"
Output: false
Example 2:

Input: ransomNote = "aa", magazine = "ab"
Output: false
Example 3:

Input: ransomNote = "aa", magazine = "aab"
Output: true
"""
```
