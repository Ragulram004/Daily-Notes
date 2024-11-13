# [7. Reverse Integer](https://leetcode.com/problems/reverse-integer/)
```java
class Solution {
    public int reverse(int x) {  
        int res = 0;
        while(x !=0)
        {
            int tmp = x%10;
            res = res*10+tmp;
            x = (x-tmp)/10;
            if(res%10!=tmp) //exceed int range
            {
                return 0;
            }
        }
        return res;
    }
}
```
  
#  [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int currMax = nums[0] ,max = nums[0];
        for(int i= 1;i<nums.length;i++){
            currMax = Math.max(currMax + nums[i],nums[i]);
            max = Math.max(max,currMax);
        }
        return max;
    }
}
```
# [63. Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)
```java
class Solution {

    int[][] dp;

    public int uniquePathsWithObstacles(int[][] obstacleGrid) {

        int m = obstacleGrid.length;

        int n = obstacleGrid[0].length;

        dp = new int[m][n];

        for (int[] i : dp) Arrays.fill(i,-1);

        return up(obstacleGrid,0,0,m,n);

    }

    int up(int[][] obs, int i, int j , int m , int n){

        if(i>=m || j>= n) return 0;

        if(obs[i][j] == 1) return 0;

        if(i == m -1 && j == n-1) return 1;

        if(dp[i][j] != -1) return dp[i][j];

        return dp[i][j] = up(obs, i+1, j , m, n) + up(obs, i , j+1, m , n);

    }

}
```
# [74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)
```java
class Solution {

    public boolean searchMatrix(int[][] matrix, int target) {

        int m = matrix.length; //no of rows

        int n = matrix[0].length; // no of cols

        int left = 0; int right = m*n-1;

        while(left <= right){

            int mid = (left+right)/2;

            int row = mid/n;

            int col = mid%n;

            if(matrix[row][col] == target) return true;

            else if(target > matrix[row][col] ) left = mid+1;

            else right = mid-1;

        }

        return false;

    }

}
```
# [240. Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)
```java
class Solution {

    public boolean searchMatrix(int[][] matrix, int target) {

        int row = matrix.length-1;

        int col = 0;

        int collen = matrix[0].length;

        while(row >=0 && col < collen){

            if(matrix[row][col] == target) return true;

            else if(matrix[row][col] > target) row--;

            else col++;

        }

        return false;

    }

}
```
# [189. Rotate Array](https://leetcode.com/problems/rotate-array/)
```java
class Solution {
    private void rev(int[] nums ,int start ,int end){
        while(start<end){
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
    public void rotate(int[] nums, int k) {
       int n = nums.length;
       k = k%n;
       rev(nums,0,n-1);
       rev(nums,0,k-1);
       rev(nums,k,n-1);
    }
}
```
# [198. House Robber](https://leetcode.com/problems/house-robber/)
```java
class Solution {

    int[] dp;

    public int rob(int[] nums) {

        int n = nums.length;

        dp = new int[n];

        Arrays.fill(dp,-1);

        return robb(nums,0,n);

    }

  

    int robb(int[] nums , int i,int n){

        if(i>=n) return 0;

        if(dp[i] != -1) return dp[i];

        return dp[i] = Math.max(robb(nums,i+1,n) , robb(nums,i+2,n)+nums[i]);

    }

}
```
# [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] res = new int[nums.length];
        int leftproduct = 1;
        int rightproduct = 1;
        for(int i = 0; i < nums.length ; i++){
            res[i] = leftproduct;
            leftproduct *= nums[i];
        }
        for(int j = nums.length -1 ; j >= 0 ;j--){
            res[j] *= rightproduct;
            rightproduct *= nums[j]; 
        }
        return res;
    }
}
```
# [75. Sort Colors](https://leetcode.com/problems/sort-colors/)
```java
class Solution {
    public void sortColors(int[] nums) {
        int num0 = 0;
        int num1 = 0;
        for(int i = 0 ; i < nums.length;i++){
            num0 = (nums[i] == 0)?num0+1:num0;
            num1 = (nums[i] == 1)?num1+1:num1;
        }
        for(int i = 0;i<num0;i++){
            nums[i] = 0;
        }
        for(int i = num0;i<num1+num0;i++){
            nums[i] = 1;
        }
        for(int i = num1+num0;i<nums.length;i++){
            nums[i] = 2;
        }
    }
}
```
# [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)
```java
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals,(a,b)->Integer.compare(a[0],b[0]));
        List<int[]> res = new ArrayList<>();

        for(int[] interval : intervals ){
            if(res.isEmpty() || res.get(res.size() - 1)[1] < interval[0]){
                res.add(interval);
            }else{
                res.get(res.size() - 1)[1] = Math.max(res.get(res.size() - 1)[1],interval[1]);
            }
        }

        return res.toArray(new int[res.size() - 1][]);
    }
}
```
# 

