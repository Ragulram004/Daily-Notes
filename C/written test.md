## sum of digit using recursion
```c
#include<stdio.h>
int digitsum(int num){
    int sum =0,c;
    if(num<10) return num;
    if(num>0){
        c=num%10;
        sum=c+digitsum(num/10);
    }
    return sum;
}


int main(){
    int num,sum=0,c;
    scanf("%d",&num);
    printf("%d",digitsum(num));
}
```
## Array Rotation for n times
```c
#include<stdio.h>
int main(){
    int n;
    scanf("%d",&n);
    int arr[100];
    for(int i = 0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    int d;
    scanf("%d", &d);
    for(int i = n-d;i<n;i++){
        printf("%d",arr[i]);
    }
    for(int i=0;i<n-d;i++){
        printf("%d",arr[i]);
    }
    
}
```
## Fibonacci
```c
#include<stdio.h>
int main(){
 int n;
 scanf("%d",&n);
 int t1 = 1,t2 =1;
 printf("%d %d ",t1,t2);
 
 for(int i = 0 ; i<n-2;i++){
     int t3 = t1+t2;
     t1 =t2;
     t2 = t3;
     printf("%d ",t3);
 }
 
}

----------------------recursion------------------
#include<stdio.h>
int fibo(int n){
    if(n==0) return 0;
    if(n==1) return 1;
    return fibo(n-1)+fibo(n-2);
}

int main(){
 int n;
 scanf("%d",&n);
 for(int i = 1;i<n;i++){
     printf("%d ",fibo(i));
 } 
}
```
## Amstrong
```c
#include<stdio.h>
#include<math.h>
int digit(int n){
    int d = 0;
    while(n>0){
        d++;
        n = n/10;
    }
    return d;
}

int main(){
 int n,sum=0;
 scanf("%d",&n);
 int n2 = n;
 int d = digit(n);
 while(n>0){
     int c = n%10;
     sum += pow(c,d);
     n = n/10;
 }

 if(sum == n2){
     printf("Amstrong");
 }else{
     printf("Not Amstrong");
 }
}
```
## palindrom
```c
#include<stdio.h>

int main(){
 int n;
 scanf("%d",&n);
 int arr[100];
 for(int i =0;i<n;i++){
     scanf("%d",&arr[i]);
 }
 int flag=0;
 for(int i=0;i<n;i++){
     if(arr[i]!=arr[n-i-1]){
         printf("Not a palindrome");
         break;
     }else{
         flag = 1;
     }
 }
 
 if(flag) printf("Palindrome");
}
```
## print non prime nums
```c
#include <stdio.h>

int isprime(int n){
    if(n==1 || n==0) return 1;
    for(int i = 2;i <=n/2;i++){
        if(n%i==0) return 1;
    }
    return 0;
}

int main() {
   int size;
   scanf("%d",&size);
   
   int arr[size];
   
   for(int i=0;i<size;i++){
       scanf("%d",&arr[i]);
   }

   for(int i=0;i<size;i++){
       if(isprime(arr[i])) printf("%d",arr[i]);
   }
   
}   
```
## replace the peak number by adding it neighbor elements  (example:-   input: 1 2 4 3    output: 1 2 9 3  )
```c
#include <stdio.h>

int main() {
    int i,j;
    int arr[]={1,2,3,4,3,4,5};
    int n=sizeof(arr)/sizeof(arr[0]);
    
    for(i=0;i<n;i++){
       if(i==0&&arr[i+1]<arr[i]){
            arr[i]=arr[i]+arr[i+1];
       }
        else if(i==n-1&&arr[i]>arr[i-1]){
            arr[i]=arr[i]+arr[i-1];
        }
        else if(arr[i-1]<arr[i]&&arr[i]>arr[i+1]){
            arr[i]=arr[i]+arr[i-1]+arr[i+1];
        }
    }
    for(int i=0;i<n;i++){
        printf("%d ",arr[i]);
    }
    return 0;
}
```
## print the median in an array
```c
#include <stdio.h>

int main() {
    int i,j;
    int arr[]={1,8,5,4,3,4,5,6};
    int n=sizeof(arr)/sizeof(arr[0]);
    
    for(i=0;i<n;i++){
       for(j=i+1;j<n;j++){
           if(arr[i]>arr[j]){
               int temp =arr[i];
               arr[i]=arr[j];
               arr[j] = temp;
           }
       }
    }
    for(int i = 0;i<n;i++){
        printf("%d",arr[i]);
    }
    printf("\n%d",arr[n/2]);
    
    return 0;
}
```