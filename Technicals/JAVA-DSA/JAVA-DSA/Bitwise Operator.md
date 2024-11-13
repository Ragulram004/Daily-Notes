## **Left Shift `<<`**
- (10) of base 10 = (1010) of base 2 
- if, 10 << 1 => (10100) of base 2 => (20) of base 10.
- `a << 1 = 2a`
- `a << n = a * 2^b`
## **Right Shift** `>>`
- 00011001 >> 1 = 001100 => remove the last digit.
- leading zeros are ignored for all number system(decimal, binary, octal, hexadecimal).
- `a >> n = a/2^b`

## **Questions**
#### **Magic Number**
```java
class MagicNumber{
  public static void main(String[] args){
    int n = 6;
    int base = 5;
    int res = 0;
    while(n > 0){
      int last = n & 1;
      n = n >> 1;
      res += last * base;
      base = base * 5;
    }
    System.out.println(res);
  }
}
```
### **No of digits based on base for a decimal**
```java
class Noofbasedigit{
  public static void main(String[] args){
    int n = 3;
    int count = 0;
    while(n > 0){
      int last = n & 1;
      n = n >> 1;
      count++;
    }
    System.out.print(count);
  }
}
--------------- another method -----------------
class Noofbasedigit{
  public static void main(String[] args){
    int n = 1232;
    int base = 10;
    int ans = (int) (Math.log(n)/Math.log(base)) + 1;
    System.out.println(ans);
  }
}
```
