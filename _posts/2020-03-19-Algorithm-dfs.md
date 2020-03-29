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

**2. Critical Connections in a Network (Leetcode 1192)**
* find the circle, remove the edges in the circle. 
* use dfs find circle.
Python code
```javascript
import collections
class Solution:
    def criticalConnections(self, n: int, connections: List[List[int]]) -> List[List[int]]:
        def _makegraph(connections):
            graph = collections.defaultdict(list)
            for conn in connections:
                graph[conn[0]].append(conn[1])
                graph[conn[1]].append(conn[0])
            return graph
        graph = _makegraph(connections)
        connections = set(map(tuple, (map(sorted, connections))))
        rank = [-2]*n
        def dfs(node,depth):
            if rank[node]>=0:
                return rank[node]
            rank[node] = depth
            min_back_depth = n
            for neighbor in graph[node]:
                if rank[neighbor] == depth - 1:
                    continue
                min_depth = dfs(neighbor,depth+1)
                if min_depth<=depth:
                    connections.discard(tuple(sorted((node, neighbor))))
                min_back_depth = min(min_depth, min_back_depth)
            return min_back_depth
        
        dfs(0,0)
        return connections    
```
