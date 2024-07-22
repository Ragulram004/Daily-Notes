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


# Camal Case
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>


int main(){
    char s[100];
    scanf("%[^\n]s",s);
    int len =strlen(s),start =0;
    
    for(int i=0;i<len;i++){
        s[0] = toupper(s[0]);
        if(s[i] == ' '){
            s[i+1]= toupper(s[i+1]);
            i++;
        }
        else{
            s[i] = tolower(s[i]);
        }
    }
    printf("%s\n",s);
}
```
# Remove Vowels and print
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int main(){
    char s[100];
    scanf("%[^\n]s",s);
    for(int i =0;s[i];i++){
        if( s[i] == 'a'|| s[i] == 'u'||s[i] == 'o'||s[i] == 'i'||s[i] == 'e'||s[i] == 'A'||s[i] == 'U'||s[i] == 'O'||s[i] == 'I'||s[i] == 'E'){
            continue;
        }
        printf("%c",s[i]);
    }
}


```

# Max Char Repeated
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int main(){
    char s[100];
    scanf("%[^\n]s",s);
    int max =0;char maxc;
    for(int i =0;s[i];i++){
        int count =0;
        for(int j=0;s[j];j++){
            if(s[i] == s[j] && !isspace(s[j])){
                count++;
            }
        }
        
        if(max<count){
            max = count;
            maxc = s[i];
        }
    }
    printf("%d %c",max,maxc);
}


```
# Add Of nums in string
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int isnum(int i ,char * s){
    int result =0;
    while(isdigit(s[i])){
            result = result * 10 + (s[i] -'0');
        i++;
    }
    return result;
}

int cdigit(int i){
    int count = 0;
    while(i>0){
        i = i%10;
        count++;
        i = i/10;
    }
    return count;
}


int main(){
    char s[100];
    scanf("%[^\n]s",s);
    
    int result =0;
    for(int i =0;i<strlen(s);i++){
        if(isdigit(s[i])){
          result += isnum(i,s);
          i += cdigit(result)+1;
        }
    }
    printf("%d",result);
}

--------------------------------------------------
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int main(){
    char s[100];
    scanf("%[^\n]s",s);
    
    int result =0, result2=0;
    for(int i =0;i<strlen(s);i++){
        if(isdigit(s[i])){
          result = result * 10 + (s[i] -'0');
        }else{
            result2 +=result;
            result =0;
        }
    }
    result2+=result;
    printf("%d",result2);
}


```

