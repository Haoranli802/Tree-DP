# Tree-DP

树形直径问题dp专题

LC543：模版题，二叉树的直径
具体思路：用树形dp解决，一个节点的最大直径就是这个节点左右的最大深度相加。然后这个节点的最大深度就是左右最大深度的最大值加一。

O(N), O(H)

```

class Solution {
    int max = 0;
    public int diameterOfBinaryTree(TreeNode root) {
        inorder(root);
        return max;
    }
    private int inorder(TreeNode root){
        if(root == null) return 0;
        int left = inorder(root.left);
        int right = inorder(root.right);
        max = Math.max(max, left + right);
        return Math.max(left, right) + 1;
    }
}

```
LC687最长同值路径

具体思路和找直径一样，先找左右直径，如果左右不为null但是值不相同的话就设为0，然后返回最大相同长度即可。

O(N), O(H)

***

LC124最大路径值

具体思路：跟找最大直径类似，不过这里我们要加上的是树节点的值。注意如果有子节点的值是负的话，那么使用0来避免负增长。

O(N), O(H)

***

LC2246相邻字符不同的最长路径

O(N), O(N)

具体思路：先用一个ArrayList数组保存所有节点的子节点，然后从顶点开始遍历，遍历每一个子节点的深度，保存最大深度，把当前深度当为第二大深度，然后找到最长路径，然后返回最大深度。最后返回最大路径加1就是最长路径的子节点数量。
