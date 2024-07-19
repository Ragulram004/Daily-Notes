# 2d array 90deg rotation
```c
#include <stdio.h>
#include <string.h>

int main(){
    int n;
    scanf("%d",&n);
    char s[n][10];
    
    for(int i =0;i<n;i++){
        scanf("%s",s[i]);
    }
    
    for(int i =0 ;i<n;i++){
        for(int j=0;j<n;j++){
            printf("%c ",s[j][i]);
        }
        printf("\n");
    }
}
```
# Reverse the even position words
```c
#include <stdio.h>
#include <string.h>

void strrev(char s[]){
    int len =strlen(s);
    
    
    for(int i = len -1 ; i>=0 ;i--){
        printf("%c",s[i]);
    }
    printf("\n");
}

int main(){
    int n;
    scanf("%d",&n);
    
    char s[n][10];
    for(int i=0;i<n;i++){
        scanf("%s",s[i]);
    }
    
    for(int i =0;i<n;i++){
        if((i+1)%2 == 0){
            strrev(s[i]);
        }
    }
}
```
# Second Largest String
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main(){
    int k;
    scanf("%d",&k);
    char s[k][100];
    int max_len;
    char max2[100];
    
    for(int i=0;i<k;i++){
        scanf("%s",s[i]);
    }
    
    for(int i=0;i<k;i++){
        for(int j = i+1 ; j<k ;j++){
            if(strlen(s[i]) >= strlen(s[j]) ){
                max_len = strlen(s[i]); 
            }else max_len = strlen(s[j]);
        }
    }
    
    for(int i =0;i<k;i++){
        if(strlen(s[i]) < max_len && strlen(s[i]) > strlen(max2)){
            strcpy(max2,s[i]);
        }
    }
    
    printf("%s",max2);
    
    
}
```