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

### 205. Isomorphic Strings

* Given two strings s and t, determine if they are isomorphic.Two strings s and t are isomorphic if the characters in s can be replaced to get t.All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.


```
class Solution {
    public boolean isIsomorphic(String s, String t) {
        if(s.length() > t.length()) return false;
        int[] sCount=new int[256];
        int[] tCount=new int[256];
        Arrays.fill(sCount, -1);
        Arrays.fill(tCount, -1);
        for(int i=0; i<s.length(); i++){
            char sChar=s.charAt(i);
            char tChar=t.charAt(i);
            if(sCount[sChar] == -1 && tCount[tChar]==-1){
                sCount[sChar]=tChar;
                tCount[tChar]=sChar;
            }
            else{
                if(sCount[sChar]!=tChar || tCount[tChar]!=sChar){
                    return false;
                }
            }
        }
        return true;

    }
}

"""
Input: s = "egg", t = "add"

Output: true

Explanation:

The strings s and t can be made identical by:

Mapping 'e' to 'a'.
Mapping 'g' to 'd'.
Example 2:

Input: s = "foo", t = "bar"

Output: false
"""
```

### 
* **brute force**
```
import java.util.*;
public class Main{
    public static boolean isomorphic(String p, String[] words){
        int[] pCount=new int[256];
        String[] sCount=new String[256];
        Arrays.fill(pCount, -1);
        Arrays.fill(sCount, null);
        for(int i=0; i<p.length(); i++){
            char pChar=p.charAt(i);
            String sWord=words[i];
            if(pCount[pChar]==-1 && sCount[pChar]==null){
                pCount[pChar] = i;
                sCount[pChar]=sWord;
            }
            else{
                if(!sWord.equals(sCount[pChar])){
                    return false;
                }
            }
        }
        return true;
    }
    public static void main(String[] args){
        Scanner input=new Scanner(System.in);
        
        String p=input.next();
        input.nextLine();
        String s=input.nextLine(); 
        String[] words=s.split(" ");
        if(isomorphic(p, words)){
            System.out.printf("yes");
        }
        else{
            System.out.printf("No");
        }
    }
}
"""
abba
dog cat cat dog
yes
"""
```

* **Optimized**
  

