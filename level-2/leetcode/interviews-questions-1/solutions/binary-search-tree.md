<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Binary Tree and Binary Search `25 problems`

## same tree
Problem Link: https://leetcode.com/problems/same-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        def dfs(cur1, cur2):
            if cur1 == None and cur2 == None:
                return True
            if cur1 == None or cur2 == None:
                return False
            if cur1.val != cur2.val:
                return False
            return dfs(cur1.left, cur2.left) and dfs(cur1.right, cur2.right)

        return dfs(p, q)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool dfs(TreeNode* cur1, TreeNode* cur2) {
        if (cur1 == NULL and cur2 == NULL)
            return true;
        if (cur1 == NULL or cur2 == NULL)
            return false;
        if (cur1->val != cur2->val)
            return false;
        return dfs(cur1->left, cur2->left) and dfs(cur1->right, cur2->right);
    }
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        return dfs(p, q);
    }
};
```

</details>

## path sum
Problem Link: https://leetcode.com/problems/path-sum

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        def dfs(curr, curr_sum):
            if curr == None:
                return curr_sum == 0
            is_valid_left = dfs(curr.left, curr_sum-curr.val)
            is_valid_right = dfs(curr.right, curr_sum-curr.val)
            if curr.right == None:
                return is_valid_left
            if curr.left == None:
                return is_valid_right
            return is_valid_left or is_valid_right

        if root == None:
            return False
        return dfs(root, targetSum)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool dfs(TreeNode *curr, int curr_sum) {
        if (curr == NULL)
            return curr_sum == 0;
        bool is_valid_left = dfs(curr->left, curr_sum-curr->val);
        bool is_valid_right = dfs(curr->right, curr_sum-curr->val);
        if (curr->right == NULL)
            return is_valid_left;
        if (curr->left == NULL)
            return is_valid_right;
        return is_valid_left or is_valid_right;
    }
public:
    bool hasPathSum(TreeNode *root, int targetSum) {
        if (root == NULL)
            return false;
        return dfs(root, targetSum);
    }
};
```

</details>

## populating next right pointers in each node ii
Problem Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if not root:
            return root
        que = [root]
        while que:
            level = []
            curr_len = len(que)
            for i in range(curr_len):
                curr = que.pop(0)
                level.append(curr)
                if curr.left:
                    que.append(curr.left)
                if curr.right:
                    que.append(curr.right)
            for i in range(len(level)-1):
                level[i].next = level[i+1]
        return root
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    Node* connect(Node *root) {
        if (not root)
            return root;
        vector<Node*> que = {root};
        while (size(que)) {
            vector<Node*> level;
            int curr_len = size(que);
            for (int i=0; i<curr_len; i++) {
                Node *curr = que[0];
                que.erase(que.begin());
                level.push_back(curr);
                if (curr->left)
                    que.push_back(curr->left);
                if (curr->right)
                    que.push_back(curr->right);
            }
            for (int i=0; i<size(level)-1; i++)
                level[i]->next = level[i+1];
        }
        return root;
    }
};
```

</details>

## average of levels in binary tree
Problem Link: https://leetcode.com/problems/average-of-levels-in-binary-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        sums = [0] * int(1e4)
        cnts = [0] * int(1e4)

        def dfs(curr, level):
            if curr == None:
                return
            sums[level] += curr.val
            cnts[level] += 1
            dfs(curr.left, level+1)
            dfs(curr.right, level+1)

        dfs(root, 0)
        avgs = [sums[i]/cnts[i] for i in range(int(1e4)) if cnts[i] != 0]
        return avgs
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<long long> sums;
    vector<long long> cnts;

    void dfs(TreeNode *curr, int level) {
        if (curr == NULL)
            return;
        sums[level] += curr->val;
        cnts[level] ++;
        dfs(curr->left, level+1);
        dfs(curr->right, level+1);
    }
public:
    vector<double> averageOfLevels(TreeNode *root) {
        sums.assign(1e4, 0LL);
        cnts.assign(1e4, 0LL);
        dfs(root, 0);
        vector<double> avgs;
        for (int i=0; i<1e4; i++) {
            if (cnts[i] != 0)
                avgs.push_back(1.0*sums[i]/cnts[i]);
        }
        return avgs;
    }
};
```

</details>

## binary tree zigzag level order traversal
Problem Link: https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        que = [root]
        res = []
        is_reverse = 0
        while que:
            level = []
            curr_len = len(que)
            for i in range(curr_len):
                curr = que.pop(0)
                level.append(curr.val)
                if curr.left:
                    que.append(curr.left)
                if curr.right:
                    que.append(curr.right)
            if is_reverse:
                level = level[::-1]
            is_reverse = 1 - is_reverse
            res.append(level)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode *root) {
        if (not root)
            return {};
        vector<TreeNode*> que = {root};
        vector<vector<int>> res;
        bool is_reverse = 0;
        while (size(que)) {
            vector<int> level;
            int curr_len = size(que);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = que[0];
                que.erase(que.begin());
                level.push_back(curr->val);
                if (curr->left)
                    que.push_back(curr->left);
                if (curr->right)
                    que.push_back(curr->right);
            }
            if (is_reverse)
                reverse(level.begin(), level.end());
            is_reverse = 1 - is_reverse;
            res.push_back(level);
        }
        return res;
    }
};

```

</details>

## maximum depth of binary tree
Problem Link: https://leetcode.com/problems/maximum-depth-of-binary-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        def dfs(curr):
            if curr == None:
                return 0
            return max(dfs(curr.left), dfs(curr.right)) + 1

        return dfs(root)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int dfs(TreeNode *curr) {
        if (curr == NULL)
            return 0;
        return max(dfs(curr->left), dfs(curr->right)) + 1;
    }
public:
    int maxDepth(TreeNode *root) {
        return dfs(root);
    }
};
```

</details>

## invert binary tree
Problem Link: https://leetcode.com/problems/invert-binary-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        def dfs(curr):
            if curr == None:
                return
            curr.left, curr.right = curr.right, curr.left
            dfs(curr.left)
            dfs(curr.right)

        dfs(root)
        return root
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    void dfs(TreeNode *curr) {
        if (curr == NULL)
            return;
        TreeNode* temp = curr->left;
        curr->left = curr->right;
        curr->right = temp;
        dfs(curr->left);
        dfs(curr->right);
    }
public:
    TreeNode* invertTree(TreeNode *root) {
        dfs(root);
        return root;
    }
};
```

</details>

## diameter of binary tree
Problem Link: https://leetcode.com/problems/diameter-of-binary-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        def dfs(curr):
            if curr == None:
                return 0
            return max(dfs(curr.left), dfs(curr.right)) + 1

        def max_diameter(curr):
            if curr == None:
                return 0
            return max(max_diameter(curr.left), max_diameter(curr.right),
                       dfs(curr.left) + dfs(curr.right))

        return max_diameter(root)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int dfs(TreeNode *curr) {
        if (curr == NULL)
            return 0;
        return max(dfs(curr->left), dfs(curr->right)) + 1;
    }
    int max_diameter(TreeNode *curr) {
        if (curr == NULL)
            return 0;
        return max(max(max_diameter(curr->left), max_diameter(curr->right)),
                   dfs(curr->left) + dfs(curr->right));
    }
public:
    int diameterOfBinaryTree(TreeNode *root) {
        return max_diameter(root);
    }
};
```

</details>

## validate binary search tree
Problem Link: https://leetcode.com/problems/validate-binary-search-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        def check_BST(curr, min_val, max_val):
            if not curr:
                return True
            return min_val <= curr.val <= max_val and \
                   check_BST(curr.left, min_val, curr.val-1) and \
                   check_BST(curr.right, curr.val+1, max_val)

        return check_BST(root, -1<<31, 1<<31)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool check_BST(TreeNode *curr, long min_val, long max_val) {
        if (not curr)
            return true;
        return min_val <= curr->val and curr->val <= max_val and
               check_BST(curr->left, min_val, curr->val-1LL) and
               check_BST(curr->right, curr->val+1LL, max_val);
    }
public:
    bool isValidBST(TreeNode *root) {
        return check_BST(root, -long(1LL<<31), long(1LL<<31));
    }
};
```

</details>

## binary tree level order traversal
Problem Link: https://leetcode.com/problems/binary-tree-level-order-traversal

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        que = [root]
        res = []
        while que:
            level = []
            curr_len = len(que)
            for i in range(curr_len):
                curr = que.pop(0)
                level.append(curr.val)
                if curr.left:
                    que.append(curr.left)
                if curr.right:
                    que.append(curr.right)
            res.append(level)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode *root) {
        if (not root)
            return {};
        vector<TreeNode*> que = {root};
        vector<vector<int>> res;
        while (size(que)) {
            vector<int> level;
            int curr_len = size(que);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = que[0];
                que.erase(que.begin());
                level.push_back(curr->val);
                if (curr->left)
                    que.push_back(curr->left);
                if (curr->right)
                    que.push_back(curr->right);
            }
            res.push_back(level);
        }
        return res;
    }
};
```

</details>

## binary tree right side view
Problem Link: https://leetcode.com/problems/binary-tree-right-side-view

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        que = [root]
        res = []
        while que:
            level = []
            curr_len = len(que)
            for i in range(curr_len):
                curr = que.pop(0)
                level.append(curr.val)
                if curr.left:
                    que.append(curr.left)
                if curr.right:
                    que.append(curr.right)
            res.append(level[-1])
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> rightSideView(TreeNode* root) {
        if (not root)
            return {};
        vector<TreeNode*> que = {root};
        vector<int> res;
        while (size(que)) {
            vector<int> level;
            int curr_len = size(que);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = q[0];
                que.erase(que.begin());
                level.push_back(curr->val);
                if (curr->left)
                    que.push_back(curr->left);
                if (curr->right)
                    que.push_back(curr->right);
            }
            res.push_back(level[size(level)-1]);
        }
        return res;
    }
};
```

</details>

## kth smallest element in a bst
Problem Link: https://leetcode.com/problems/kth-smallest-element-in-a-bst

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        stk = []
        curr = root
        while stk or curr:
            while curr:
                stk.append(curr)
                curr = curr.left
            k -= 1
            curr = stk.pop()
            if k == 0:
                return curr.val
            curr = curr.right
        return -1
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int kthSmallest(TreeNode *root, int k) {
        stack<TreeNode*> stk;
        TreeNode *curr = root;
        while (size(stk) or curr) {
            while (curr) {
                stk.push(curr);
                curr = curr->left;
            }
            k --;
            curr = stk.top();
            stk.pop();
            if (k == 0)
                return curr->val;
            curr = curr->right;
        }
        return -1;
    }
};
```

</details>

## lowest common ancestor of a binary tree
Problem Link: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def search(curr, p, q):
            if not curr:
                return curr
            if curr.val == p.val or curr.val == q.val:
                return curr
            left  = search(curr.left,  p, q)
            right = search(curr.right, p, q)
            if left and right:
                return curr
            return left if left else right

        if not root or not p or not q:
            return None
        return search(root, p, q)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* search(TreeNode *curr, TreeNode *p, TreeNode *q) {
        if (not curr)
            return curr;
        if (curr->val == p->val or curr->val == q->val)
            return curr;
        TreeNode *left  = search(curr->left,  p, q);
        TreeNode *right = search(curr->right, p, q);
        if (left and right)
            return curr;
        return left? left : right;
    }
public:
    TreeNode* lowestCommonAncestor(TreeNode *root, TreeNode *p, TreeNode *q) {
        if (not root or not p or not q)
            return NULL;
        return search(root, p, q);
    }
};
```

</details>

## binary tree maximum path sum
Problem Link: https://leetcode.com/problems/binary-tree-maximum-path-sum

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def maxPathSum(self, root: Optional[TreeNode]) -> int:
        def dfs(root):
            nonlocal res
            if not root:
                return 0
            left_max  = max(dfs(root.left), 0)
            right_max = max(dfs(root.right), 0)
            res = max(res, root.val + left_max + right_max)
            return root.val + max(left_max, right_max)

        res = -2e3
        dfs(root)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int res;

    int dfs(TreeNode *root) {
        if (not root)
            return 0;
        int left_max  = max(dfs(root->left), 0);
        int right_max = max(dfs(root->right), 0);
        res = max(res, root->val + left_max + right_max);
        return root->val + max(left_max, right_max);
    }
public:
    int maxPathSum(TreeNode *root) {
        res = -2e3;
        dfs(root);
        return res;
    }
};
```

</details>

## search a 2d matrix
Problem Link: https://leetcode.com/problems/search-a-2d-matrix

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        n, m = len(matrix), len(matrix[0])
        l, r = 0, n*m-1
        while l <= r:
            k = (l+r) // 2
            i, j = k//m, k%m
            if matrix[i][j] > target:
                r = k-1
            elif matrix[i][j] < target:
                l = k+1
            else:
                return True
        return False
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>> &matrix, int target) {
        int n = size(matrix), m = size(matrix[0]);
        int l = 0, r = n*m-1;
        while (l <= r) {
            int k = (l+r) / 2;
            int i = k/m, j = k%m;
            if (matrix[i][j] > target)
                r = k-1;
            else if (matrix[i][j] < target)
                l = k+1;
            else
                return true;
        }
        return false;
    }
};
```

</details>

## minimum depth of binary tree
Problem Link: https://leetcode.com/problems/minimum-depth-of-binary-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        def dfs(curr):
            if curr == None:
                return 0
            if curr.left == None:
                return dfs(curr.right)+1
            if curr.right == None:
                return dfs(curr.left)+1
            return min(dfs(curr.left), dfs(curr.right)) + 1

        return dfs(root)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int dfs(TreeNode *curr) {
        if (curr == NULL)
            return 0;
        if (curr->left == NULL)
            return dfs(curr->right)+1;
        if (curr->right == NULL)
            return dfs(curr->left)+1;
        return min(dfs(curr->left), dfs(curr->right)) + 1;
    }
public:
    int minDepth(TreeNode *root) {
        return dfs(root);
    }
};
```

</details>

## merge two binary trees
Problem Link: https://leetcode.com/problems/merge-two-binary-trees

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def mergeTrees(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> Optional[TreeNode]:
        def dfs(cur, cur1, cur2):
            if cur1 == None and cur2 == None:
                return None
            if cur1 == None:
                return cur2
            if cur2 == None:
                return cur1
            cur = TreeNode(cur1.val + cur2.val, TreeNode(), TreeNode())
            cur.left = dfs(cur.left, cur1.left, cur2.left)
            cur.right = dfs(cur.right, cur1.right, cur2.right)
            return cur

        root = TreeNode()
        return dfs(root, root1, root2)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* dfs(TreeNode* cur, TreeNode* cur1, TreeNode* cur2) {
        if (cur1 == NULL and cur2 == NULL)
            return NULL;
        if (cur1 == NULL)
            return cur2;
        if (cur2 == NULL)
            return cur1;
        cur = new TreeNode(cur1->val + cur2->val, new TreeNode(), new TreeNode());
        cur->left = dfs(cur->left, cur1->left, cur2->left);
        cur->right = dfs(cur->right, cur1->right, cur2->right);
        return cur;
    }
public:
    TreeNode* mergeTrees(TreeNode *root1, TreeNode *root2) {
        TreeNode *root = new TreeNode();
        return dfs(root, root1, root2);
    }
};
```

</details>

## lowest common ancestor of a binary search tree
Problem Link: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def LCA(curr, p, q):
            if curr == None:
                return None
            if p < curr.val and curr.val < q:
                return curr
            if curr.val > max(p, q):
                return LCA(curr.left, p, q)
            if curr.val < min(p, q):
                return LCA(curr.right, p, q)
            return curr

        return LCA(root, p.val, q.val)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* LCA(TreeNode *curr, int p, int q) {
        if (curr == NULL)
            return NULL;
        if (p < curr->val and curr->val < q)
            return curr;
        if (curr->val > max(p, q))
            return LCA(curr->left, p, q);
        if (curr->val < min(p, q))
            return LCA(curr->right, p, q);
        return curr;
    }
public:
    TreeNode* lowestCommonAncestor(TreeNode *root, TreeNode* p, TreeNode* q) {
        return LCA(root, p->val, q->val);
    }
};
```

</details>

## subtree of another tree
Problem Link: https://leetcode.com/problems/subtree-of-another-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        def isSameTree(cur1, cur2):
            if cur1 == None and cur2 == None:
                return True
            if cur1 == None or cur2 == None:
                return False
            if cur1.val != cur2.val:
                return False
            return isSameTree(cur1.left, cur2.left) and isSameTree(cur1.right, cur2.right)

        def find_subtree(curr, subRoot):
            if curr == None:
                return False
            if isSameTree(curr, subRoot):
                return True
            return find_subtree(curr.left, subRoot) or find_subtree(curr.right, subRoot)

        return find_subtree(root, subRoot)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool isSameTree(TreeNode* cur1, TreeNode* cur2) {
        if (cur1 == NULL and cur2 == NULL)
            return true;
        if (cur1 == NULL or cur2 == NULL)
            return false;
        if (cur1->val != cur2->val)
            return false;
        return isSameTree(cur1->left, cur2->left) and isSameTree(cur1->right, cur2->right);
    }
    bool find_subtree(TreeNode *curr, TreeNode* subRoot) {
        if (curr == NULL)
            return false;
        if (isSameTree(curr, subRoot))
            return true;
        return find_subtree(curr->left, subRoot) or find_subtree(curr->right, subRoot);
    }
public:
    bool isSubtree(TreeNode *root, TreeNode* subRoot) {
        return find_subtree(root, subRoot);
    }
};
```

</details>

## search in rotated sorted array ii
Problem Link: https://leetcode.com/problems/search-in-rotated-sorted-array-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def search(self, nums: List[int], target: int) -> bool:
        l, r = 0, len(nums)-1
        while l <= r:
            m = (l+r) // 2
            if target == nums[m]:
                return True
            if nums[l] < nums[m]:
                if target > nums[m] or target < nums[l]:
                    l = m+1
                else:
                    r = m-1
            elif nums[l] > nums[m]:
                if target < nums[m] or target > nums[r]:
                    r = m-1
                else:
                    l = m+1
            else:
                l += 1
        return False
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool search(vector<int> &nums, int target) {
        int l = 0, r = size(nums)-1;
        while (l <= r) {
            int m = (l+r) / 2;
            if (target == nums[m])
                return true;
            if (nums[l] < nums[m]) {
                if (target > nums[m] or target < nums[l])
                    l = m+1;
                else
                    r = m-1;
            }
            else if (nums[l] > nums[m]) {
                if (target < nums[m] or target > nums[r])
                    r = m-1;
                else
                    l = m+1;
            }
            else
                l ++;
        }
        return false;
    }
};
```

</details>

## find k closest elements
Problem Link: https://leetcode.com/problems/find-k-closest-elements

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
        l, r = 0, len(arr)-k
        while l < r:
            m = (l+r) // 2
            if x - arr[m] > arr[m+k] - x:
                l = m+1
            else:
                r = m
        return arr[l:l+k]
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        int l = 0, r = size(arr)-k;
        while (l < r) {
            int m = (l+r) / 2;
            if (x - arr[m] > arr[m+k] - x)
                l = m+1;
            else
                r = m;
        }
        vector<int> res(arr.begin()+l, arr.begin()+l+k);
        return res;
    }
};
```

</details>

## populating next right pointers in each node
Problem Link: https://leetcode.com/problems/populating-next-right-pointers-in-each-node

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root:
            return root
        que = [root]
        while que:
            level = []
            curr_len = len(que)
            prev = None
            for i in range(curr_len):
                curr = que.pop(0)
                if curr.left and curr.right:
                    curr.left.next = curr.right
                    que.append(curr.left)
                    que.append(curr.right)
                    if prev != None:
                        prev.right.next = curr.left
                prev = curr
        return root
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    Node* connect(Node *root) {
        if (not root)
            return root;
        vector<Node*> que = {root};
        while (size(que)) {
            vector<int> level;
            int curr_len = size(que);
            Node *prev = NULL;
            for (int i=0; i<curr_len; i++) {
                Node *curr = que[0];
                que.erase(que.begin());
                level.push_back(curr->val);
                if (curr->left and curr->right) {
                    curr->left->next = curr->right;
                    que.push_back(curr->left);
                    que.push_back(curr->right);
                    if (prev != NULL)
                        prev->right->next = curr->left;
                }
                prev = curr;
            }
        }
        return root;
    }
};
```

</details>

## binary tree level order traversal ii
Problem Link: https://leetcode.com/problems/binary-tree-level-order-traversal-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def levelOrderBottom(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        que = [root]
        res = []
        while que:
            level = []
            curr_len = len(que)
            for i in range(curr_len):
                curr = que.pop(0)
                level.append(curr.val)
                if curr.left:
                    que.append(curr.left)
                if curr.right:
                    que.append(curr.right)
            res.append(level)
        res = res[::-1]
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode *root) {
        if (not root)
            return {};
        vector<TreeNode*> que = {root};
        vector<vector<int>> res;
        while (size(que)) {
            vector<int> level;
            int curr_len = size(que);
            for (int i=0; i<curr_len; i++) {
                TreeNode *curr = que[0];
                que.erase(que.begin());
                level.push_back(curr->val);
                if (curr->left)
                    que.push_back(curr->left);
                if (curr->right)
                    que.push_back(curr->right);
            }
            res.push_back(level);
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```

</details>

## all nodes distance k in binary tree
Problem Link: https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def distanceK(self, root: TreeNode, target: TreeNode, k: int) -> List[int]:
        def bfs():
            que = [(-1, root)]
            while que:
                curr_len = len(que)
                for i in range(curr_len):
                    p, u = que.pop(0)
                    if p != -1:
                        adj[u.val].append(p.val)
                        adj[p.val].append(u.val)
                    if u.left:
                        que.append((u, u.left))
                    if u.right:
                        que.append((u, u.right))

        def dfs(p, u, k):
            if k == 0:
                res.add(u)
                return
            for v in adj[u]:
                if v != p and v not in res:
                    dfs(u, v, k-1)

        adj = {i:[] for i in range(501)}
        bfs()
        res = set()
        dfs(-1, target.val, k)
        res = list(res)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    void bfs(vector<vector<int>> &adj, TreeNode* root) {
        vector<pair<TreeNode*, TreeNode*>> que = {{NULL, root}};
        while (size(que)) {
            int curr_len = size(que);
            for (int i=0; i<curr_len; i++) {
                auto [p, u] = que[0];
                que.erase(que.begin());
                if (p != NULL) {
                    adj[u->val].push_back(p->val);
                    adj[p->val].push_back(u->val);
                }
                if (u->left)
                    que.push_back({u, u->left});
                if (u->right)
                    que.push_back({u, u->right});
            }
        }
    }
    void dfs(int p, int u, int k, set<int> &res, const vector<vector<int>> &adj) {
        if (k == 0) {
            res.insert(u);
            return;
        }
        for (int v : adj[u]) {
            if (v != p and res.find(v) == res.end())
                dfs(u, v, k-1, res, adj);
        }
    }
public:
    vector<int> distanceK(TreeNode *root, TreeNode *target, int k) {
        vector<vector<int>> adj(501);
        bfs(adj, root);
        set<int> res;
        dfs(-1, target->val, k, res, adj);
        vector<int> ans(res.begin(), res.end());
        return ans;
    }
};
```

</details>

## path sum ii
Problem Link: https://leetcode.com/problems/path-sum-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        def dfs(curr_node, curr_sum, curr_path):
            if not curr_node.left and not curr_node.right:
                if curr_sum == 0:
                    res.append(curr_path)
                return
            if curr_node.left:
                dfs(curr_node.left,  curr_sum-curr_node.left.val,
                    curr_path+[curr_node.left.val])
            if curr_node.right:
                dfs(curr_node.right, curr_sum-curr_node.right.val,
                    curr_path+[curr_node.right.val])

        if not root:
            return []
        res = []
        dfs(root, targetSum-root.val, [root.val])
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    void dfs(TreeNode *curr_node, int curr_sum, vector<int> curr_path,
             vector<vector<int>> &res) {
        if (not curr_node->left and not curr_node->right) {
            if (curr_sum == 0)
                res.push_back(curr_path);
            return;
        }
        if (curr_node->left) {
            curr_path.push_back(curr_node->left->val);
            dfs(curr_node->left,  curr_sum-curr_node->left->val,
                curr_path, res);
            curr_path.pop_back();
        }
        if (curr_node->right) {
            curr_path.push_back(curr_node->right->val);
            dfs(curr_node->right, curr_sum-curr_node->right->val,
                curr_path, res);
            curr_path.pop_back();
        }
    }
public:
    vector<vector<int>> pathSum(TreeNode *root, int targetSum) {
        if (not root)
            return {};
        vector<vector<int>> res;
        dfs(root, targetSum-root->val, {root->val}, res);
        return res;
    }
};
```

</details>

## peak index in a mountain array
Problem Link: https://leetcode.com/problems/peak-index-in-a-mountain-array

<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def peakIndexInMountainArray(self, arr: List[int]) -> int:
        f, e = 0, len(arr)-1
        while f <= e:
            m = (f+e)//2
            if arr[m] < arr[m+1]:
                f = m+1
            else:
                e = m-1
        return f
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/binary-search-tree.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int> &arr) {
        int f = 0, e = size(arr)-1;
        while (f <= e) {
            int m = (f+e)/2;
            if (arr[m] < arr[m+1])
                f = m+1;
            else
                e = m-1;
        }
        return f;
    }
};
```

</details>
