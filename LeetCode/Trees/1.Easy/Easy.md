# [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)
```java
class Solution {

    public List<Integer> inorderTraversal(TreeNode root) {

        List<Integer> res = new ArrayList<>();

        inorder(root,res);

        return res;

    }

    public void inorder(TreeNode root, List<Integer> res){

        if(root == null) return;

        inorder(root.left , res);

        res.add(root.val);

        inorder(root.right,res);

    }

}
```
# [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)
```java
class Solution {

    public List<Integer> preorderTraversal(TreeNode root) {

        List<Integer> res = new ArrayList<Integer>();

        preorder(root,res);

        return res;

    }

    void preorder(TreeNode root , List<Integer> res){

        if(root == null) return;

        res.add(root.val);  

        preorder(root.left, res);

        preorder(root.right,res);

    }

}

```
# [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)
```java
class Solution {

    public List<Integer> postorderTraversal(TreeNode root) {

        List<Integer> res = new ArrayList<>();

        postorder(root,res);

        return res;

    }

    public void postorder(TreeNode root, List<Integer> res){

        if (root == null) return;

        postorder(root.left,res);

        postorder(root.right,res);

        res.add(root.val);

    }

}
```
# [100. Same Tree](https://leetcode.com/problems/same-tree/)
```java
class Solution {

    public boolean isSameTree(TreeNode p, TreeNode q) {

        if(p == null && q == null) return true;

        if(p == null || q == null) return false;

        if(p.val != q.val) return false;

        return isSameTree(p.left,q.left) && isSameTree(p.right,q.right);

    }

}
```
# [101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)
```java
	class Solution {

    public boolean isSymmetric(TreeNode root) {

        return mirror(root.left,root.right);

    }

    public boolean mirror(TreeNode a, TreeNode b){

        if(a == null && b == null) return true;

        if(a == null || b == null) return false;

        if(a.val != b.val) return false;

        return mirror(a.left,b.right) && mirror(a.right , b.left);

    }

}
```
# [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)
```java
class Solution {

    public TreeNode invertTree(TreeNode root) {

        if(root == null) return root;

        invertTree(root.left);

        invertTree(root.right);

        TreeNode temp = root.left;

        root.left = root.right;

        root.right = temp;

        return root;

    }

}

```
# [222. Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/)
```java
class Solution {

    public int countNodes(TreeNode root) {

        if (root == null) return 0;

        return 1+countNodes(root.left)+countNodes(root.right);

    }

}
```
# 