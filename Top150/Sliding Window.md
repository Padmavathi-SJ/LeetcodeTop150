## Sliding Window

### 03. Leetcode_30 - Substring with Concatenation of All Words
```
#include<stdio.h>
#include<string.h>
#include<ctype.h>
#include<stdbool.h>
bool compare(char str[], char concat[][100], int n, int s, int e){
    char temp[100];
    int l=0;
    for(int i=s; i<=e; i++){
        temp[l++]=str[i];
    }
    temp[l]='\0';
    for(int i=0; i<n; i++){
        if(strcmp(temp, concat[i])==0) {
            return true;
        }
    }
    return false;
}
void main(){
    char str[256];
    fgets(str, 256, stdin);
    str[strcspn(str, "\n")]='\0';
    int l=strlen(str);
    int n;
    scanf("%d", &n);
     getchar();
    char words[n][100];
    for(int i=0; i<n; i++){
        fgets(words[i], 100, stdin);
        words[i][strcspn(words[i], "\n")]='\0';
    }
    char concat[100][100];
    int index=0;
    for(int i=0; i<n; i++){
        for(int j=0; j<n; j++){
            if(i!=j){
                strcpy(concat[index], words[i]);
                strcat(concat[index], words[j]);
                index++;
            }
        }
    }
    int result[100];
    int m=0;
    for(int i=0; i<l; i++){
        for(int j=i; j<l; j++){
            if(compare(str, concat, index, i, j)){
                result[m++]=i;
            }
        }
    }
    for(int i=0; i<m; i++){
        printf("%d ", result[i]);
    }
}
```

### Leetcode_76. Minimum Window Substring
```
class Solution {
    public boolean check(String str, String t, int s, int e){
        for(int i=0; i<t.length(); i++){
            int found=0;
            for(int j=s; j<=e; j++){
                if(t.charAt(i) == str.charAt(j)){
                    found=1;
                    break;
                }
            }
            if(found==0){
                return false;
            }
        }
        return true;
    }
    public String minWindow(String s, String t) {
        String result="";
        if(s.length()<t.length()) return result;

        int l=s.length();
        int minLen=Integer.MAX_VALUE, startIndex=0;
        for(int i=0; i<l; i++){
            for(int j=i; j<l; j++){
                int currLen=j-i+1;
                if(check(s, t, i, j)){
                    if(currLen < minLen){
                        minLen=currLen;
                        startIndex=i;
                    }
                }
            }
        }
        for(int i=startIndex; i<startIndex+minLen; i++){
            result=result + s.charAt(i);
        }
        return result;
    }
}
"""
Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
Example 2:

Input: s = "a", t = "a"
Output: "a"
Explanation: The entire string s is the minimum window.
Example 3:

Input: s = "a", t = "aa"
Output: ""
Explanation: Both 'a's from t must be included in the window.
Since the largest window of s only has one 'a', return empty string.
"""
```
