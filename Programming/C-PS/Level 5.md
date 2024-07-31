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
```jsx
const Stars = (props) => {
  const ref = useRef();
  const [positions] = useState(() => {
    const pos = new Float32Array(5000 * 3);
    for (let i = 0; i < 5000; i++) {
      pos[i * 3] = (Math.random() - 0.5) * 2.4; // X position
      pos[i * 3 + 1] = (Math.random() - 0.5) * 2.4; // Y position
      pos[i * 3 + 2] = Math.random() * -2.4; // Z position behind the screen
    }
    return pos;
  });

  useFrame((state, delta) => {
    for (let i = 0; i < 5000; i++) {
      positions[i * 3 + 2] += delta * 0.5; // Move forward
      if (positions[i * 3 + 2] > 1.2) { // Reset to behind the screen when reaching the front
        positions[i * 3 + 2] = Math.random() * -2.4; // New random position behind the screen
      }
    }
    ref.current.geometry.attributes.position.needsUpdate = true;
  });

  return (
    <group>
      <Points ref={ref} positions={positions} stride={3} frustumCulled {...props}>
        <PointMaterial
          transparent
          color='#f272c8'
          size={0.002}
          sizeAttenuation={true}
          depthWrite={false}
        />
      </Points>
    </group>
  );
};


```

```jsx
const Stars = (props) => { const ref = useRef(); const [positions] = useState(() => { const pos = new Float32Array(5000 * 3); for (let i = 0; i < 5000; i++) { pos[i * 3] = (Math.random() - 0.5) * 2.4; // X position pos[i * 3 + 1] = (Math.random() - 0.5) * 2.4; // Y position pos[i * 3 + 2] = (Math.random() - 0.5) * 2.4; // Z position } return pos; }); useFrame((state) => { const time = state.clock.getElapsedTime(); for (let i = 0; i < 5000; i++) { positions[i * 3 + 1] = Math.sin(time + positions[i * 3]) * 0.1; // Smaller Y position wave } ref.current.geometry.attributes.position.needsUpdate = true; }); return ( <group> <Points ref={ref} positions={positions} stride={3} frustumCulled {...props}> <PointMaterial transparent color='#f272c8' size={0.002} sizeAttenuation={true} depthWrite={false} /> </Points> </group> ); };
```