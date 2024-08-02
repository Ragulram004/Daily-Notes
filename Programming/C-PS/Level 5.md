### Topic: (from all levels(1-4) but only using function call)
## Recursive Fibonacci Sequence Generator
```c
#include <stdio.h>
int fibonacci(int n){
    if(n<=1)
    return n;
    return fibonacci(n-1)+fibonacci(n-2);
}
int main() {
    int n;
    scanf("%d",&n);
    printf("%d",fibonacci(n)); 
    return 0;
}
```
## Palindrome Checker
```c
#include <stdio.h>
#include<string.h>
#include<ctype.h>

int ispali(char *s){
    int len = strlen(s);
    int start =0 , end = len-1;
    while(start<end){
        if(s[start] != s[end]) return 0;
        start++;end--;
    }
    return 1;
}

int main(){
    char s[100],s2[100];
    scanf("%[^\n]",s);
    int j =0;
    for(int i =0;i<strlen(s);i++){
        if(isalpha(s[i])){
            s2[j++] = tolower(s[i]);
        }
    }
    
    if(ispali(s2)){
        printf("True");
    }else{
        printf("False");
    }
}

```
## Prime Number Checker
```c
#include <stdio.h>

int isprime(int n){
    if(n < 0) return 0;
    if(n == 2) return 1;
    for(int i =2;i<=n/2;i++){
        if(n%i == 0) return 0;
    }
    return 1;
}

int main(){
    int n;
    scanf("%d",&n);

    if(isprime(n)){
        printf("True");
    }else{
        printf("False");
    }
    
}

```
## Anagram Detector
```c
#include <stdio.h>
#include<string.h>
#include <stdlib.h>

void isAnagram(char *s1, char *s2 , int len){
    int view[256] = {0};
    
    for(int i =0;i<len;i++){
        view[s1[i]]++;
    }
    for(int i =0;i<len;i++){
        view[s2[i]]--;
    }
    for(int i =0;i<256;i++){
        if(view[i] !=0){
            printf("Not Anagram");
            exit(0);
        }
    }
    printf("Anagram");
}

int main(){
   char s1[100];
   scanf("%s",s1);
   getchar();
   char s2[100];
   scanf("%s",s2);
   getchar();
   
   int l1 = strlen(s1);
   int l2 = strlen(s2);
    
    if(l1 == l2){
        isAnagram(s1,s2,l1);
    }else{
        printf("Not Anagram");
    }

}

```
## Recursive Factorial Calculator
```c
#include <stdio.h>

int fact(int n){
    if(n<=0) return 0;
    if(n==1) return 1;
    return n*fact(n-1);
}

int main(){
    int n;
    scanf("%d",&n);
    int result = fact(n);
    printf("%d",result);
}
```
## Power Function
```c
#include <stdio.h>

int power(int n,int n2){
    int sum =1;
    
    for(int i= 0; i<n2;i++){
        sum = sum * n;
    }
    return sum;
}

int main(){
    int n,n2;
    scanf("%d %d",&n,&n2);
    int result = power(n,n2);
    printf("%d",result);
}
```
## String Compression
```c
#include<stdio.h>
#include<string.h>

void stringcompress(char *s, char *result){
    int j = 0;
    int n = strlen(s);
    int count =1;
    
    for(int i =0; i<n;i++){
        result[j++] = s[i];
        while(i<n-1 && s[i] == s[i+1]){
            count++;
            i++;
        }
        if(count > 1){
            j += sprintf(&result[j],"%d",count);
        }
        count = 1;
    }
    result[j] = '\0';
}

int main(){
    char s[100];
    scanf("%s",s);
    char result[100];
    
    stringcompress(s,result);
    printf("%s\n",result);
}
```
## Matrix Transposition
```c
#include<stdio.h>

void matrixtrans(int r, int c, int matrix[r][c], int result[c][r]){
    for(int i = 0 ; i < r ; i++){
        for(int j = 0 ; j < c;j++){
            result[j][i] = matrix[i][j];
        }
    }
}

int main(){
    int r,c;
    scanf("%d %d",&r , &c);
    
    int matrix[r][c];
    int result[c][r];
    
    for(int i =0 ; i<r ;i++){
        for(int j = 0; j < c;j++){
            scanf("%d" , &matrix[i][j]);
        }
    }
    
    matrixtrans(r,c,matrix,result);
    
    for(int i =0 ; i < c; i++){
        for(int j = 0 ; j < r ;j++){
            printf("%d ", result[i][j]);
        }
        printf("\n");
    }
}
```
## Word Frequency Counter
```c
 #include <stdio.h>
#include <string.h>
#include <ctype.h>

void wordcount(char * s){
    int len = strlen(s);
    int now = 0;
    int k = 0 , j = 0 ;
    int count = 0 ;
    
    for(int i = 0 ; i <= len ;i++){
        if(s[i] == ' ' || s[i] == ',' || s[i] == '.' || s[i] == '\0'){
            now++;
        }
    }
    
    char words[now][100];
    
    for(int i = 0 ; i < len ;i++){
        if(s[i] == ' ' || s[i] == ',' || s[i] == '.' || s[i] == '\0'){
            words[k][j] = '\0';
            k++;
            j = 0;
        }else{
            words[k][j++] = tolower(s[i]);
        }
    }
    
    for(int i=0;i<now;i++ ){
        if(words[i][0] == '\0') continue;
        count = 1;
        for(int j = i+1;j<len;j++){
            if(!strcmp(words[i],words[j])){
                count++;
                words[j][0] = '\0';
            }
        }
        printf("%s:%d\n",words[i],count);
    }
    
    
}

int main(){
    char s[100];
    scanf("%[^\n]",s);
    wordcount(s);
    return 0;
}
```
## Sorting Algorithm Implementation
```c
#include <string.h>
#include <stdio.h>

void sort(int *nums,int n){
    for(int i = 0 ;i < n ;i++){
        for(int j = i+1;j<n;j++){
            if(nums[i] > nums[j]){
                int temp = nums[i];
                nums[i] = nums[j];
                nums[j] = temp;
            }
        }
    }
}

int main(){
    int n;
    scanf("%d",&n);
    int nums[n];
    
    for(int i = 0;i<n;i++){
        scanf("%d",&nums[i]);
    }
    sort(nums,n);
    
    for(int i = 0;i<n;i++){
        printf("%d ",nums[i]);
    }
}
```
