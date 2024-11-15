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

### **Weather a num is pow of 2**
```java
class powof2{
  public static void main(String[] args){
    int n = 16; //exception for 0 will return true fix that.
    boolean ans = (n&(n-1)) == 0;
    System.out.println(ans);
  }
}
```
### **Power**
```java
class Power{
  public static void main(String[] args){
    int base = 4;
    int power = 3;
    int ans =1;
    while(power > 0){
      if((power & 1) == 1){
        ans *= base;
      }
      base *= base;
      power = power >> 1;
    }
    System.out.println(ans);
  }
}
```
### **Set bits**
```java
class Setbits{
  public static void main(String[] args){
    int n =7;
    int ans = 0;
    while(n >0){
      if((n & 1) == 1){
        ans++;
      }
      n = n >> 1;
    }
    System.out.println(ans);
  }
}
------------------- or ------------------------
while(n>0){
	count++;
	n = n & (n-1);
}
```

### **[832. Flipping an Image](https://leetcode.com/problems/flipping-an-image/)**
```java
class Solution {
    public int[][] flipAndInvertImage(int[][] image) {
        for(int[] row : image){
            for(int i = 0 ; i < (image[0].length+1)/ 2 ; i++){
                int temp = row[i] ^ 1;
                row[i] = row[image[0].length - i -1] ^ 1;
                row[image[0].length-i-1] = temp;
            }
        }
        return image;
    }
}
```