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
