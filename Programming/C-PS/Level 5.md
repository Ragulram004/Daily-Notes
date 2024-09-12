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
## Sentence Palindrome Checker
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
    if(n<0) return 0;
    if(n==0||n==1) return 1;
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

# Edit Distance
```c
#include <stdio.h>
#include<string.h>

int min(int x,int y, int z){
    return (x < y) ? (x < z ? x : z) : (y < z ? y : z);
}


int editdistance(char* s1, char* s2){
    int l1 = strlen(s1);
    int l2 = strlen(s2);
    
    int dp[l1+1][l2+1];
    
    for(int i = 0; i <= l1;i++){
        for(int j = 0 ; j <= l2 ; j++){
            if(i == 0){
                dp[i][j] = j;
            }
            else if(j == 0){
                dp[i][j] = i;
            }else if(s1[i-1] == s2[j-1]){
                dp[i][j] = dp[i-1][j-1];
            }
            else{
                dp[i][j] = 1+ min(dp[i][j-1],dp[i-1][j],dp[i-1][j-1]);
            }
        }
    }
    return dp[l1][l2];
}

int main(){
    char str1[100];
    char str2[100];
    scanf("%s %s",str1,str2);
    printf("%d",editdistance(str1,str2));
}
```
# Longest Palindrome Substring
```c
#include<stdio.h>
#include<string.h>
#include<stdbool.h>

bool ispali(int i , int j , char * str){
    while(i<j){
        if(str[i] != str[j]) return false;
        i++;
        j--;
    }
    return true;
}

int main(){
    char str[100];
    scanf("%s",str);
    int l = strlen(str);
    char max[100];
    for(int i = 0 ; i < l ; i++){
        for(int j = i+1 ; j < l ; j ++){
            if(ispali(i,j,str)){
                int count = j-i+1;
                int m = strlen(max);
                if( m < count){
                    m = count;
                    strncpy(max , str+i,count);
                    max[count] = '\0';
                }
            }
        }
    }
    printf("%s",max);
}
```
# Coordinate min distance
```c
#include<stdio.h>
#include<string.h>

int max(int x,int y){
    if(x<0) x*=-1;
    if(y<0) y*=-1;
    return (x<y)?y:x;
}

int sum(int * arr , int n){
    int x,y,sum=0;
    for(int i = 0; i < n ; i+=2){
        x = arr[i]- arr[i+2];
        y = arr[i+1] - arr[i+3];
        sum += max(x,y);
    }
    return sum;
}

int main(){
    int a;
    scanf("%d",&a);
    int res[a*2];
    for(int i =0;i<a*2;i++){
        scanf("%d",&res[i]);
    }
    printf("%d",sum(res,a*2));
}
```
# Group Anagram
```c
#include<stdio.h>
#include<string.h>

int anagram(char * s1, char * s2){
    int a[256] = {0};
    if(strlen(s1) != strlen(s2)) return 0;
    for(int i = 0 ; i < strlen(s1) ; i++){
        a[s1[i]]++;
        a[s2[i]]--;
    }
    for(int i = 0 ; i < 256; i++){
        if(a[i] != 0 ) return 0;
    }
    return 1;
}

int main(){
    int n;
    scanf("%d",&n);
    char strs[n][100];
    int arr[100] = {0};
    for(int i = 0 ; i < n ; i++){
        scanf("%s",strs[i]);
    }
    
    for(int i = 0 ; i < n ; i++){
        if(arr[i] == 0){
            printf("%s",strs[i]);
            arr[i] == 1;
            for(int j = i+1; j < n ; j++){
                int a = anagram(strs[i],strs[j]);
                if(a == 1){
                    printf(" %s",strs[j]);
                    arr[j] = 1;
                }
            }
            printf("\n");
        }
    }
}
```
# Pivot Index
```c
#include<stdio.h>
#include<string.h>
int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i = 0 ;i<n;i++){
        scanf("%d",&arr[i]);
    }
    for(int i = 0 ; i < n; i++){
        int a = 0, b = 0;
        for(int j = 0 ; j <i;j++){
            a +=arr[j];
        }
        for(int j = i+1;j<n;j++){
            b+=arr[j];
        }
        if(a == b){
            printf("%d",i);
            return 0;
        }
    }
    printf("-1");
    
}
```
# Prime Anagram
```c
#include <stdio.h>
#include<string.h>

int isprime(int n){
    if (n ==0 || n == 1) return 0;
    for(int i = 2; i <=n/2 ; i++){
        if(n%i == 0) return 0; 
    }
    return 1;
}

int anagram(char*s1,char*s2){
    int arr[256] = {0};
    if(strlen(s1) != strlen(s2)) return 0;
    for(int i = 0 ; i <strlen(s1);i++){
        arr[s1[i]]++;
        arr[s2[i]]--;
    }
    for(int i = 0 ; i < 256;i++){
        if(arr[i] != 0) return 0;
    }
    return 1;
}

int main(){
    int a;
    int b;
    int limit = 0;
    scanf("%d %d" ,&a,&b);
    int arr[b-a+1];
    char word[b-a+1][100];
    for(int i = a ; i <=b;i++ ){
        if(isprime(i)){
            // printf("%d",i);
            arr[limit++] = i;
        }
    }
    int visit[limit];
    for(int i = 0; i < limit ; i++){
        sprintf(word[i],"%d",arr[i]);
        visit[i] = 1;
    }
    for(int i = 0 ; i< limit ; i++){
        int flag = 1;
        if(visit[i] != 1) continue;
        for(int j = i+1; j<limit;j++){
            if(anagram(word[i],word[j])){
                printf("%s %s",word[i],word[j]);
                flag = 0;
            }
        }
        if(!flag) printf("\n");
    }
}
```
# MAXIMUM THREE PRODUCT
```c
#include <stdio.h>
#include <stdlib.h>

int compare(const void*x,const void*y){
    int a = *(int *)x;
    int b = *(int *)y;
    return b-a;
}


int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i = 0 ; i < n; i++){
        scanf("%d",&arr[i]);
    }
    qsort(arr,n,sizeof(int),compare);
    int pro1 = arr[0]*arr[1]*arr[2];
    int pro2 = arr[0]*arr[n-1]*arr[n-2];
    (pro1>pro2)? printf("%d",pro1) : printf("%d",pro2);
    
}
```
# Binary to Int
```c
#include<stdio.h>
#include<string.h>
#include <math.h>

int integer(char *s){
    int j = 0;
    int sum = 0;
    for(int i = strlen(s)-1;i>=0;i--){
        int bit = s[i]-'0';
        sum += bit * pow(2,j);
        j++;
    }
    return sum;
}

int main(){
    char s[100];
    scanf("%s",s);
    printf("%d",integer(s));
}
```
# Matrix Addition
```c
#include <stdio.h>
#include <string.h>


int max(int arr[100][100], int r, int c){
    int pcount = 0; int sum =0;
    for(int i = 0 ; i < r;i++){
        int max = 0;
        for(int j = 0 ; j < c ; j++){
            if(arr[i][j]>0) pcount++;
            if(arr[i][j] > max)  max = arr[i][j];
        }
        sum += max;
    }
    sum += pcount;
    for(int i = 0 ; i < c;i++){
        int max = 0;
        for(int j = 0 ; j < r ; j++){
            if(arr[j][i] > max)  max = arr[j][i];
        }
        sum += max;
    }
    return sum;
    
}

int main(){
    int r,c;
    scanf("%d %d",&r ,&c);
    int arr[100][100];
    for(int i = 0 ; i < r ; i++){
        for(int j = 0 ; j < c ; j++){
            scanf("%d",&arr[i][j]);
        }
    }
    printf("%d",max(arr,r,c));
}
```
# Circular Prime
```c
#include<stdio.h>
#include<string.h>
#include<math.h>

int isprime(int n){
    if(n == 0 || n == 1) return 0;
    for(int i = 2; i<= n/2; i++){
        if(n%i == 0) return 0;
    }
    return 1;
}

int main(){
    int n;
    scanf("%d",&n);
    int len = log10(n)+1;
    int k = pow(10,len-1);
    int flag = 1;
    
    for(int i = 0 ; i < len ;i++){
        int m = n/k;
        n= (n%k)*10+m;
        if(!isprime(n)){
            flag = 0; break;
        }
    }
    if (flag){
        printf("Circular");
    }else{
        printf("Not");
    }
}
```