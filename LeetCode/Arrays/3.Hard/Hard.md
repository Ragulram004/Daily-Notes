# [42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
```java
class Solution {
    public int trap(int[] height) {
        int n = height.length; int ans = 0;
        int lm = 0 ; int rm = 0;
        int left = 0; int right =n-1;
        while(left<right){
            if(height[left] < height[right]){
                if(lm < height[left]) lm = height[left];
                else ans += lm - height[left];
                ++left;
            }
            else{
                if(rm < height[right]) rm = height[right];
                else ans += rm - height[right];
                --right;
            }
        }
        return ans;
    }
}
```
