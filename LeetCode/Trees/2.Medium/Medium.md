# [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
```java
class Solution {

    public List<List<Integer>> levelOrder(TreeNode root) {

        List<List<Integer>> ans = new ArrayList<>();

        if(root == null) return ans;

        Deque<TreeNode>q = new ArrayDeque();

        q.offer(root);

        while(!q.isEmpty()){

            List<Integer> l1 = new ArrayList<>();

            int size = q.size();

            for(int i = 0 ; i < size;i++){

                TreeNode curr = q.poll();

                l1.add(curr.val);

                if(curr.left != null)q.offer(curr.left);

                if(curr.right != null) q.offer(curr.right);

            }

            ans.add(l1);

        }

        return ans;

    }

}
```
# [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/)
```java
class Solution {

    public int sumNumbers(TreeNode root) {

        int res = 0;

        return sum(root,res);

    }

    public  int sum(TreeNode root, int res){

        if(root == null) return 0;

        if(root.left == null && root.right == null){

            return res * 10 + root.val;

        }

        return sum(root.left , res * 10 + root.val) + sum(root.right, res * 10 + root.val);

    }

}
```
# [1325. Delete Leaves With a Given Value](https://leetcode.com/problems/delete-leaves-with-a-given-value/)
```java
class Solution {

    public TreeNode removeLeafNodes(TreeNode root, int target) {

        if(root == null) return null;

        root.left = removeLeafNodes(root.left,target);

        root.right = removeLeafNodes(root.right,target);

        if(root.left == null && root.right == null && root.val == target){

            return null;

        }        

        return root;

    }

}
```