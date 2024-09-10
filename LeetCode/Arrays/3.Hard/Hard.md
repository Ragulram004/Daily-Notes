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

# [51. N-Queens](https://leetcode.com/problems/n-queens/)
```java
class Solution {

    public List<List<String>> solveNQueens(int n) {

        List<List<String>> res = new ArrayList<>();

        List<String> curr = new ArrayList<>();

        for(int i =0 ;i<n;i++){

            curr.add(".".repeat(n));

        }

        nqueen(0,curr,res);

        return res;

    }

    private void nqueen(int row, List<String> curr, List<List<String>> res){

        if(row == curr.size()){

            res.add(new ArrayList(curr));

            return;

        }

        for(int col = 0 ; col < curr.size(); col++){

            if(canplace(row,col,curr)){

                StringBuilder sb = new StringBuilder(curr.get(row));

                sb.setCharAt(col,'Q');

                curr.set(row,sb.toString());

                nqueen(row+1,curr,res);

                sb.setCharAt(col,'.');

                curr.set(row,sb.toString());

            }

        }

    }

    private boolean canplace(int row, int col, List<String> curr){

        for(int i = row-1;i>=0;i--){

            if(curr.get(i).charAt(col) == 'Q') return false;

        }

        for(int i = row-1,j=col-1;i>=0 && j >=0; i--,j--){

            if(curr.get(i).charAt(j) == 'Q') return false;

        }

        for(int i= row -1, j= col+1;i>=0 && j<curr.size();i--,j++){

            if(curr.get(i).charAt(j) == 'Q') return false;

        }

        return true;

    }

}
```
# [52. N-Queens II](https://leetcode.com/problems/n-queens-ii/)
```java
class Solution {

    public int totalNQueens(int n) {

        int[] res = {0};

        List<String> curr = new ArrayList<>();

        for(int i = 0 ; i < n ; i++){

            curr.add(".".repeat(n));

        }

        nqueen(0, curr , res);

        return res[0];

    }

    private void nqueen(int row , List<String> curr, int[] res){

        if(row == curr.size()){

            res[0]++;

            return;

        }

        for(int col = 0 ; col < curr.size(); col++){

                if(canplace(row , col , curr)){

                StringBuilder sb = new StringBuilder(curr.get(row));

                sb.setCharAt(col,'Q');

                curr.set(row, sb.toString());

                nqueen(row+1, curr , res);

                sb.setCharAt(col,'.');

                curr.set(row,sb.toString());

            }

        }

    }

    private boolean canplace(int row , int col , List<String> curr){

        for(int i = row -1 ; i >=0;i--){

            if(curr.get(i).charAt(col) == 'Q') return false;

        }

        for(int i = row -1, j = col -1; i>=0 && j>=0;i--,j--){

            if(curr.get(i).charAt(j) == 'Q') return false;

        }

        for(int i = row - 1 , j = col +1; i>=0 && j < curr.size();i--,j++){

            if(curr.get(i).charAt(j) == 'Q') return false;

        }

        return true;

    }

}
```