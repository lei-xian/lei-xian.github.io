### DFS
**1. Binary Tree Maximum Path Sum (Leetcode 124)**

Java code
```javascript
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
    int max_sum = Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        dfs(root);
        return max_sum;
    }
    public int dfs(TreeNode node){
        if (node == null) return 0;
        int left_sum = Math.max(0,dfs(node.left));
        int right_sum = Math.max(0,dfs(node.right));
        max_sum = Math.max(left_sum+right_sum+node.val,max_sum);
        return Math.max(node.val+left_sum,node.val+right_sum);
    }
}
```
