# Maximum Width of Binary Tree

No.: 662
Related to Untitled Database (Similar Problems) 2: https://www.notion.so/8a2d61656ed54b6f9c7df19b16d126f5
Tags: DFS, tree
URL-CN: https://leetcode-cn.com/problems/maximum-width-of-binary-tree/
language: c++
完成: No
改编: No
过一遍: No
重要性1-5: 1
难度: M

huahua code: [https://zxi.mytechroad.com/blog/tree/leetcode-662-maximum-width-of-binary-tree/](https://zxi.mytechroad.com/blog/tree/leetcode-662-maximum-width-of-binary-tree/)

```cpp
class Solution {
public:
  int widthOfBinaryTree(TreeNode* root) {
    vector<int> ids; // left most id of each level.
    function<int(TreeNode*, int, int)> dfs = [&](TreeNode* node, int d, int id) -> int {
      if (!node) return 0;
      if (d == ids.size()) ids.push_back(id);
      return max({id - ids[d] + 1, 
                 dfs(node->left, d + 1, (id - ids[d]) * 2), 
                 dfs(node->right, d + 1, (id - ids[d]) * 2 + 1)});
    };
    return dfs(root, 0, 0);
  }
};
```