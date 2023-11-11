<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Graph and Backtracking `20 problems`

## clone graph
Problem Link: https://leetcode.com/problems/clone-graph

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def cloneGraph(self, node: 'Node') -> 'Node':
        def dfs(u):
            if u in adj:
                return adj[u]
            new_u = Node(u.val)
            adj[u] = new_u
            for v in u.neighbors:
                new_u.neighbors.append(dfs(v))
            return new_u

        adj = {}
        return dfs(node) if node else None
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    map<Node*, Node*> adj;

    Node* dfs(Node *u) {
        if (adj.find(u) != adj.end())
            return adj[u];
        Node *new_u = new Node(u->val);
        adj[u] = new_u;
        for (Node *v : u->neighbors)
            new_u->neighbors.push_back(dfs(v));
        return new_u;
    }
public:
    Node* cloneGraph(Node* node) {
        return node? dfs(node) : NULL;
    }
};
```

</details>

## course schedule ii
Problem Link: https://leetcode.com/problems/course-schedule-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
        def dfs(u):
            if u in cycle:
                return False
            if u in visited:
                return True
            cycle.add(u)
            for v in adj[u]:
                if not dfs(v):
                    return False
            cycle.remove(u)
            visited.add(u)
            res.append(u)
            return True

        adj = {i: [] for i in range(numCourses)}
        for i, j in prerequisites:
            adj[i].append(j)
        res = []
        visited, cycle = set(), set()
        for i in range(numCourses):
            if not dfs(i):
                return []
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool dfs(int u, set<int> &visited, set<int> &cycle,
             vector<vector<int>> &adj, vector<int> &res) {
        if (cycle.find(u) != cycle.end())
            return false;
        if (visited.find(u) != visited.end())
            return true;
        cycle.insert(u);
        for (auto v : adj[u]) {
            if (not dfs(v, visited, cycle, adj, res))
                return false;
        }
        cycle.erase(cycle.find(u));
        visited.insert(u);
        res.push_back(u);
        return true;
    }
public:
    vector<int> findOrder(int numCourses, vector<vector<int>> &prerequisites) {
        vector<vector<int>> adj(numCourses);
        for (auto v : prerequisites)
            adj[v[0]].push_back(v[1]);
        vector<int> res;
        set<int> visited, cycle;
        for (int i=0; i<numCourses; i++) {
            if (not dfs(i, visited, cycle, adj, res))
                return {};
        }
        return res;
    }
};
```

</details>

## number of islands
Problem Link: https://leetcode.com/problems/number-of-islands

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        def dfs(r, c):
            if (r, c) in visit or not(0 <= r < n) or not(0 <= c < m) or grid[r][c] == '0':
                return
            visit.add((r, c))
            for i in range(4):
                dfs(r+dx[i], c+dy[i])

        n, m = len(grid), len(grid[0])
        visit = set()
        dx = [0, 0, 1, -1]
        dy = [-1, 1, 0, 0]
        res = 0
        for r in range(n):
            for c in range(m):
                if grid[r][c] == '1' and (r, c) not in visit:
                    dfs(r, c)
                    res += 1
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    set<pair<int, int>> visited;
    int dx[4] = {0, 0, 1, -1};
    int dy[4] = {-1, 1, 0, 0};

    void dfs(int r, int c, const vector<vector<char>> &grid, int n, int m) {
        if (visited.find({r, c}) != visited.end() or
            not(0 <= r and r < n) or not(0 <= c and c < m) or grid[r][c] == '0')
            return;
        visited.insert({r, c});
        for (int i=0; i<4; i++)
            dfs(r+dx[i], c+dy[i], grid, n, m);
    }
public:
    int numIslands(vector<vector<char>> &grid) {
        int n = size(grid), m = size(grid[0]);
        int res = 0;
        for (int r=0; r<n; r++) {
            for (int c=0; c<m; c++) {
                if (grid[r][c] == '1' and visited.find({r, c}) == visited.end()) {
                    dfs(r, c, grid, n, m);
                    res ++;
                }
            }
        }
        return res;
    }
};
```

</details>

## course schedule
Problem Link: https://leetcode.com/problems/course-schedule

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        def dfs(u):
            if u in visited:
                return False
            if len(adj[u]) == 0:
                return True
            visited.add(u)
            for v in adj[u]:
                if not dfs(v):
                    return False
            visited.remove(u)
            adj[u] = []
            return True

        adj = {i: [] for i in range(numCourses)}
        for i, j in prerequisites:
            adj[i].append(j)
        visited = set()
        for i in range(numCourses):
            if not dfs(i):
                return False
        return True
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool dfs(int u, set<int> &visited, vector<vector<int>> &adj) {
        if (visited.find(u) != visited.end())
            return false;
        if (size(adj[u]) == 0)
            return true;
        visited.insert(u);
        for (auto v : adj[u]) {
            if (not dfs(v, visited, adj))
                return false;
        }
        visited.erase(visited.find(u));
        adj[u].clear();
        return true;
    }
public:
    bool canFinish(int numCourses, vector<vector<int>> &prerequisites) {
        vector<vector<int>> adj(numCourses);
        for (auto v : prerequisites)
            adj[v[0]].push_back(v[1]);
        set<int> visited;
        for (int i=0; i<numCourses; i++) {
            if (not dfs(i, visited, adj))
                return false;
        }
        return true;
    }
};
```

</details>

## subsets
Problem Link: https://leetcode.com/problems/subsets

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        res = []
        for i in range(1<<n):
            curr_list = []
            for j in range(n):
                if 1<<j & i:
                    curr_list.append(nums[j])
            res.append(curr_list)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int> &nums) {
        int n = size(nums);
        vector<vector<int>> res;
        for (int i=0; i<(1<<n); i++) {
            vector<int> curr_list;
            for (int j=0; j<n; j++)
                if (1<<j & i)
                    curr_list.push_back(nums[j]);
            res.push_back(curr_list);
        }
        return res;
    }
};
```

</details>

## palindrome partitioning
Problem Link: https://leetcode.com/problems/palindrome-partitioning

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def partition(self, s: str) -> List[List[str]]:
        def is_palindrome(s):
            return s == s[::-1]

        def dfs(i):
            if i == len(s):
                res.append(curr_parts[:])
                return
            for j in range(i, len(s)):
                if is_palindrome(s[i:j+1]):
                    curr_parts.append(s[i:j+1])
                    dfs(j+1)
                    curr_parts.pop()

        res = []
        curr_parts = []
        dfs(0)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<vector<string>> res;
    vector<string> curr_parts;

    bool is_palindrome(string s) {
        string t = s;
        reverse(t.begin(), t.end());
        return s == t;
    }
    void dfs(int i, const string &s) {
        if (i == size(s)) {
            res.push_back(curr_parts);
            return;
        }
        for (int j=i; j<size(s); j++) {
            if (is_palindrome(s.substr(i, j-i+1))) {
                curr_parts.push_back(s.substr(i, j-i+1));
                dfs(j+1, s);
                curr_parts.pop_back();
            }
        }
    }
public:
    vector<vector<string>> partition(string s) {
        dfs(0, s);
        return res;
    }
};
```

</details>

## n queens
Problem Link: https://leetcode.com/problems/n-queens

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def solveNQueens(self, n: int) -> List[List[str]]:
        def backtrack(r):
            if r == n:
                curr_board = ["".join(row) for row in board]
                res.append(curr_board)
                return
            for c in range(n):
                if c in col or (r+c) in pos_diag or (r-c) in neg_diag:
                    continue
                col.add(c)
                pos_diag.add(r+c)
                neg_diag.add(r-c)
                board[r][c] = 'Q'
                backtrack(r+1)
                col.remove(c)
                pos_diag.remove(r+c)
                neg_diag.remove(r-c)
                board[r][c] = '.'

        col = set()
        pos_diag = set()
        neg_diag = set()
        res = []
        board = [['.' for j in range(n)] for i in range(n)]
        backtrack(0)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    set<int> col;
    set<int> pos_diag;
    set<int> neg_diag;

    void backtrack(int r, int n, vector<string> &board, vector<vector<string>> &res) {
        if (r == n) {
            vector<string> curr_board(board);
            res.push_back(curr_board);
            return;
        }
        for (int c=0; c<n; c++) {
            if (col.find(c) != col.end() or
                pos_diag.find(r+c) != pos_diag.end() or
                neg_diag.find(r-c) != neg_diag.end())
                continue;
            col.insert(c);
            pos_diag.insert(r+c);
            neg_diag.insert(r-c);
            board[r][c] = 'Q';
            backtrack(r+1, n, board, res);
            col.erase(col.find(c));
            pos_diag.erase(pos_diag.find(r+c));
            neg_diag.erase(neg_diag.find(r-c));
            board[r][c] = '.';
        }
    }
public:
    vector<vector<string>> solveNQueens(int n) {
        vector<vector<string>> res;
        vector<string> board(n, string(n, '.'));
        backtrack(0, n, board, res);
        return res;
    }
};
```

</details>

## letter combinations of a phone number
Problem Link: https://leetcode.com/problems/letter-combinations-of-a-phone-number

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        def generate_letters(i, curr_s):
            if len(curr_s) == len(digits):
                res.append(curr_s)
                return
            for j in digits_chars[digits[i]]:
                generate_letters(i+1, curr_s+j)

        res = []
        digits_chars = {'2':'abc', '3':'def', '4':'ghi', '5':'jkl',
                        '6':'mno', '7':'pqrs', '8':'tuv', '9':'wxyz'}
        if digits:
            generate_letters(0, '')
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<string> res;
    map<char, string> digits_chars = {{'2',"abc"}, {'3',"def"}, {'4',"ghi"}, {'5',"jkl"},
                                      {'6',"mno"}, {'7',"pqrs"}, {'8',"tuv"}, {'9',"wxyz"}};

    void generate_letters(int i, string curr_s, const string &digits) {
        if (size(curr_s) == size(digits)) {
            res.push_back(curr_s);
            return;
        }
        for (char j : digits_chars[digits[i]])
            generate_letters(i+1, curr_s+j, digits);
    }
public:
    vector<string> letterCombinations(string digits) {
        if (digits != "")
            generate_letters(0, "", digits);
        return res;
    }
};
```

</details>

## combinations
Problem Link: https://leetcode.com/problems/combinations

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        def generate_combinations(p, arr):
            if len(arr) == k:
                res.append(arr[:])
                return
            for i in range(p, n+1):
                arr.append(i)
                generate_combinations(i+1, arr)
                arr.pop()

        res = []
        generate_combinations(1, [])
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<vector<int>> res;

    void generate_combinations(int p, vector<int> &arr, int n, int k) {
        if (size(arr) == k) {
            res.push_back(arr);
            return;
        }
        for (int i=p; i<n+1; i++) {
            arr.push_back(i);
            generate_combinations(i+1, arr, n, k);
            arr.pop_back();
        }
    }
public:
    vector<vector<int>> combine(int n, int k) {
        generate_combinations(1, {}, n, k);
        return res;
    }
};
```

</details>

## permutations
Problem Link: https://leetcode.com/problems/permutations

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        def generate_permutation(arr):
            if len(arr) == 0:
                return []
            if len(arr) == 1:
                return [arr]
            res = []
            for i in range(len(arr)):
                m = arr[i]
                for p in generate_permutation(arr[:i] + arr[i+1:]):
                    res.append([m] + p)
            return res

        return generate_permutation(nums)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<vector<int>> generate_permutation(vector<int> &arr) {
        if (size(arr) == 0)
            return {};
        if (size(arr) == 1)
            return {arr};
        vector<vector<int>> res;
        for (int i=0; i<size(arr); i++) {
            int m = arr[i];
            vector<int> sub1(arr.begin(), arr.begin()+i);
            vector<int> sub2(arr.begin()+i+1, arr.end());
            vector<int> sub;
            sub.insert(sub.begin(), sub1.begin(), sub1.end());
            sub.insert(sub.end(),   sub2.begin(), sub2.end());
            for (auto p : generate_permutation(sub)) {
                vector<int> temp(p.begin(), p.end());
                temp.insert(temp.begin(), m);
                res.push_back(temp);
            }
        }
        return res;
    }
public:
    vector<vector<int>> permute(vector<int> &nums) {
        return generate_permutation(nums);
    }
};
```

</details>

## sort items by groups respecting dependencies
Problem Link: https://leetcode.com/problems/sort-items-by-groups-respecting-dependencies

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## letter case permutation
Problem Link: https://leetcode.com/problems/letter-case-permutation

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def letterCasePermutation(self, s: str) -> List[str]:
        def generate_permutation(i, curr_s):
            if i == len(s):
                res.add(curr_s)
                return
            generate_permutation(i+1, curr_s+s[i].lower())
            generate_permutation(i+1, curr_s+s[i].upper())

        res = set()
        generate_permutation(0, '')
        return list(res)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    set<string> res;

    void generate_permutation(int i, string curr_s, const string &s) {
        if (i == size(s)) {
            res.insert(curr_s);
            return;
        }
        generate_permutation(i+1, curr_s+char(tolower(s[i])), s);
        generate_permutation(i+1, curr_s+char(toupper(s[i])), s);
    }
public:
    vector<string> letterCasePermutation(string s) {
        generate_permutation(0, "", s);
        vector<string> ans(res.begin(), res.end());
        return ans;
    }
};
```

</details>

## permutations ii
Problem Link: https://leetcode.com/problems/permutations-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        def generate_permutation(arr):
            if len(arr) == 0:
                return []
            if len(arr) == 1:
                return [arr]
            res = []
            for i in range(len(arr)):
                m = arr[i]
                for p in generate_permutation(arr[:i] + arr[i+1:]):
                    res.append([m] + p)
            return res

        res = list(set(tuple(i) for i in generate_permutation(nums)))
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<vector<int>> generate_permutation(vector<int> &arr) {
        if (size(arr) == 0)
            return {};
        if (size(arr) == 1)
            return {arr};
        vector<vector<int>> res;
        for (int i=0; i<size(arr); i++) {
            int m = arr[i];
            vector<int> sub1(arr.begin(), arr.begin()+i);
            vector<int> sub2(arr.begin()+i+1, arr.end());
            vector<int> sub;
            sub.insert(sub.begin(), sub1.begin(), sub1.end());
            sub.insert(sub.end(),   sub2.begin(), sub2.end());
            for (auto p : generate_permutation(sub)) {
                vector<int> temp(p.begin(), p.end());
                temp.insert(temp.begin(), m);
                res.push_back(temp);
            }
        }
        return res;
    }
public:
    vector<vector<int>> permuteUnique(vector<int> &nums) {
        vector<vector<int>> perm = generate_permutation(nums);
        set<vector<int>> res_set(perm.begin(), perm.end());
        vector<vector<int>> res(res_set.begin(), res_set.end());
        return res;
    }
};
```

</details>

## combination sum ii
Problem Link: https://leetcode.com/problems/combination-sum-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        def generate_combinations(i, arr, curr_total):
            if curr_total == target:
                res.append(sorted(arr[:]))
                return
            if curr_total > target:
                return
            prev = -1
            for j in range(i, len(candidates)):
                if candidates[j] == prev:
                    continue
                arr.append(candidates[j])
                generate_combinations(j+1, arr, curr_total+candidates[j])
                arr.pop()
                prev = candidates[j]

        res = []
        candidates.sort()
        generate_combinations(0, [], 0)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    set<vector<int>> res;

    void generate_combinations(int i, vector<int >arr, int curr_total, vector<int> &candidates, int target) {
        if (curr_total == target) {
            sort(arr.begin(), arr.end());
            res.insert(arr);
            return;
        }
        if (curr_total > target)
            return;
        int prev = -1;
        for (int j=i; j<size(candidates); j++) {
            if (candidates[j] == prev)
                continue;
            arr.push_back(candidates[j]);
            generate_combinations(j+1, arr, curr_total+candidates[j], candidates, target);
            arr.pop_back();
            prev = candidates[j];
        }
    }
public:
    vector<vector<int>> combinationSum2(vector<int> &candidates, int target) {
        generate_combinations(0, {}, 0, candidates, target);
        vector<vector<int>> ans(res.begin(), res.end());
        return ans;
    }
};
```

</details>

## combination sum iii
Problem Link: https://leetcode.com/problems/combination-sum-iii

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        def generate_combinations(p, arr, curr_total):
            if len(arr) == k and curr_total == n:
                res.append(arr[:])
                return
            if sum(arr) > n:
                return
            for i in range(p, min(10, n+1)):
                arr.append(i)
                generate_combinations(i+1, arr, curr_total+i)
                arr.pop()

        res = []
        generate_combinations(1, [], 0)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<vector<int>> res;

    void generate_combinations(int p, vector<int> &arr, int curr_total, int n, int k) {
        if (size(arr) == k and curr_total == n) {
            res.push_back(arr);
            return;
        }
        if (curr_total > n) {
            return;
        }
        for (int i=p; i<min(10, n+1); i++) {
            arr.push_back(i);
            generate_combinations(i+1, arr, curr_total+i, n, k);
            arr.pop_back();
        }
    }
public:
    vector<vector<int>> combinationSum3(int k, int n) {
        generate_combinations(1, {}, 0, n, k);
        return res;
    }
};
```

</details>

## target sum
Problem Link: https://leetcode.com/problems/target-sum

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        def dp(i, curr_total):
            if i == len(nums):
                return curr_total == target
            if memo[i][curr_total+N] != -1:
                return memo[i][curr_total+N]
            memo[i][curr_total+N] = dp(i+1, curr_total+nums[i]) + \
                                    dp(i+1, curr_total-nums[i])
            return memo[i][curr_total+N]

        N = int(2e4+3)
        memo = [[-1 for i in range(N*2)] for j in range(23)]
        return dp(0, 0)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    static const int N = 2e4+3;
    int memo[23][N*2];

    int dp(int i, int curr_total, const vector<int> &nums, const int &target) {
        if (i == size(nums))
            return curr_total == target;
        if (memo[i][curr_total+N] != -1)
            return memo[i][curr_total+N];
        memo[i][curr_total+N] = dp(i+1, curr_total+nums[i], nums, target) +
                                dp(i+1, curr_total-nums[i], nums, target);
        return memo[i][curr_total+N];
    }
public:
    int findTargetSumWays(vector<int> &nums, int target) {
        memset(memo, -1, sizeof memo);
        return dp(0, 0, nums, target);
    }
};
```

</details>

## generalized abbreviation
Problem Link: https://leetcode.com/problems/generalized-abbreviation

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## pacific atlantic water flow
Problem Link: https://leetcode.com/problems/pacific-atlantic-water-flow

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
        def dfs(r, c, visited, prev_h):
            if (r, c) in visited or not(0 <= r < n) or not(0 <= c < m) or heights[r][c] < prev_h:
                return
            visited.add((r, c))
            for i in range(4):
                dfs(r+dx[i], c+dy[i], visited, heights[r][c])

        n, m = len(heights), len(heights[0])
        visited1, visited2 = set(), set()
        dx = [0, 0, 1, -1]
        dy = [-1, 1, 0, 0]
        for c in range(m):
            dfs(0,   c, visited1, heights[0][c])
            dfs(n-1, c, visited2, heights[n-1][c])
        for r in range(n):
            dfs(r, 0,   visited1, heights[r][0])
            dfs(r, m-1, visited2, heights[r][m-1])
        res = list(visited1 & visited2)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    set<pair<int, int>> visited1, visited2;
    int dx[] = {0, 0, 1, -1};
    int dy[] = {-1, 1, 0, 0};

    void dfs(int r, int c, set<pair<int, int>> &visited, int prev_h,
             const vector<vector<int>> &heights, int n, int m) {
        if (visited.find({r, c}) != visited.end() or
            not(0 <= r and r < n) or not(0 <= c and c < m) or heights[r][c] < prev_h)
            return;
        visited.insert({r, c});
        for (int i=0; i<4; i++)
            dfs(r+dx[i], c+dy[i], visited, heights[r][c], heights, n, m);
    }
public:
    vector<vector<int>> pacificAtlantic(vector<vector<int>> &heights) {
        int n = size(heights), m = size(heights[0]);
        for (int c=0; c<m; c++) {
            dfs(0,   c, visited1, heights[0][c], heights, n, m);
            dfs(n-1, c, visited2, heights[n-1][c], heights, n, m);
        }
        for (int r=0; r<n; r++) {
            dfs(r, 0,   visited1, heights[r][0], heights, n, m);
            dfs(r, m-1, visited2, heights[r][m-1], heights, n, m);
        }
        vector<pair<int, int>> res;
        set_intersection(visited1.begin(), visited1.end(), visited2.begin(), visited2.end(),
                         back_inserter(res));
        vector<vector<int>> ans;
        for (auto &[i, j] : res)
            ans.push_back({i, j});
        return ans;
    }
};
```

</details>

## graph valid tree
Problem Link: https://leetcode.com/problems/graph-valid-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## number of connected components in an undirected graph
Problem Link: https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph

<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/graph-backtracking.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>
