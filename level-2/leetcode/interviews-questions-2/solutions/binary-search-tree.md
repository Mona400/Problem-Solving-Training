<a href="/level-2/leetcode/interviews-questions-2/solutions/binary-search-tree.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 2 <br> Binary Tree and Binary Search `25 problems`

## binary search
Problem Link: https://leetcode.com/problems/binary-search

<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        f, e = 0, len(nums)-1
        while f <= e:
            m = (f+e)//2
            if nums[m] == target:
                return m
            if nums[m] > target:
                e = m-1
            else:
                f = m+1
        return -1
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int search(vector<int> &nums, int target) {
        int f = 0, e = size(nums)-1;
        while (f <= e) {
            int m = (f+e)/2;
            if (nums[m] == target)
                return m;
            if (nums[m] > target)
                e = m-1;
            else
                f = m+1;
        }
        return -1;
    }
};
```

</details>

## find smallest letter greater than target
Problem Link: https://leetcode.com/problems/find-smallest-letter-greater-than-target

<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:
        f, e = 0, len(letters)-1
        while f <= e:
            m = (f+e)//2
            if letters[m] > target:
                e = m-1
            else:
                f = m+1
        return letters[f%len(letters)]
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    char nextGreatestLetter(vector<char> &letters, char target) {
        int f = 0, e = size(letters)-1;
        while (f <= e) {
            int m = (f+e)/2;
            if (letters[m] > target)
                e = m-1;
            else
                f = m+1;
        }
        return letters[f%size(letters)];
    }
};
```

</details>

## index pairs of a string
Problem Link: https://leetcode.com/problems/index-pairs-of-a-string

<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## majority element
Problem Link: https://leetcode.com/problems/majority-element

<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        cnt = {}
        for i in nums:
            cnt[i] = cnt.get(i, 0) + 1
        for i, j in cnt.items():
            if j > len(nums)//2:
                return i
        return -1
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int majorityElement(vector<int> &nums) {
        map<int, int> cnt;
        for (int i : nums)
            cnt[i] ++;
        for (auto &[i, j] : cnt) {
            if (j > size(nums)/2)
                return i;
        }
        return -1;
    }
};
```

</details>

## partition to k equal sum subsets
Problem Link: https://leetcode.com/problems/partition-to-k-equal-sum-subsets

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def canPartitionKSubsets(self, nums: List[int], k: int) -> bool:
        def check_partitions(i, k, curr_total):
            if k == 0:
                return True
            if curr_total > target:
                return False
            if curr_total == target:
                return check_partitions(0, k-1, 0)
            for j in range(i, len(nums)):
                if visited[j]:
                    continue
                visited[j] = True
                if check_partitions(j+1, k, curr_total+nums[j]):
                    return True
                visited[j] = False
            return False

        nums_sum = sum(nums)
        if nums_sum % k:
            return False
        target = nums_sum // k
        nums.sort(reverse=True)
        visited = [0] * len(nums)
        return check_partitions(0, k, 0)
```
`TODO` TIME-LIMIT-EXCEEDED


</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool check_partitions(int i, int k, int curr_total,
                          const int &target, const vector<int> &nums, bool visited[]) {
        if (k == 0)
            return true;
        if (curr_total > target)
            return false;
        if (curr_total == target)
            return check_partitions(0, k-1, 0, target, nums, visited);
        for (int j=i; j<size(nums); j++) {
            if (visited[j])
                continue;
            visited[j] = true;
            if (check_partitions(j+1, k, curr_total+nums[j], target, nums, visited))
                return true;
            visited[j] = false;
        }
        return false;
    }
public:
    bool canPartitionKSubsets(vector<int> &nums, int k) {
        int nums_sum = accumulate(nums.begin(), nums.end(), 0);
        if (nums_sum % k)
            return false;
        int target = nums_sum / k;
        sort(nums.rbegin(), nums.rend());
        bool visited[16] = {0};
        return check_partitions(0, k, 0, target, nums, visited);
    }
};
```
`TODO` TIME-LIMIT-EXCEEDED

</details>

## best time to buy and sell stock with cooldown
Problem Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        def dp(i, buy):
            if i >= len(prices):
                return 0
            if memo[i][buy] != -1:
                return memo[i][buy]
            cooldown = dp(i+1, buy)
            if buy:
                memo[i][buy] = max(dp(i+1, 1-buy) - prices[i], cooldown)
            else:
                memo[i][buy] = max(dp(i+2, 1-buy) + prices[i], cooldown)
            return memo[i][buy]

        memo = [[-1 for i in range(2)] for j in range(5003)]
        return dp(0, 1)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int memo[5003][2];
    int dp(int i, bool buy, const vector<int> &prices) {
        if (i >= size(prices))
            return 0;
        if (memo[i][buy] != -1)
            return memo[i][buy];
        int cooldown = dp(i+1, buy, prices);
        if (buy)
            memo[i][buy] = max(dp(i+1, 1-buy, prices) - prices[i], cooldown);
        else
            memo[i][buy] = max(dp(i+2, 1-buy, prices) + prices[i], cooldown);
        return memo[i][buy];
    }
public:
    int maxProfit(vector<int> &prices) {
        memset(memo, -1, sizeof memo);
        return dp(0, 1, prices);
    }
};
```

</details>

## find minimum in rotated sorted array
Problem Link: https://leetcode.com/problems/find-minimum-in-rotated-sorted-array

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        l, r = 0, len(nums)-1
        while l+1 < r:
            m = (l+r) // 2
            if nums[m] > nums[r]:
                l = m
            else:
                r = m
        return min(nums[l], nums[r])
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findMin(vector<int> &nums) {
        int l = 0, r = size(nums)-1;
        while (l+1 < r) {
            int m = (l+r) / 2;
            if (nums[m] > nums[r])
                l = m;
            else
                r = m;
        }
        return min(nums[l], nums[r]);
    }
};
```

</details>

## find peak element
Problem Link: https://leetcode.com/problems/find-peak-element

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        l, r = 0, len(nums)-1
        while l < r:
            m = (l+r) // 2
            if nums[m] > nums[m+1]:
                r = m
            else:
                l = m+1
        return l
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findPeakElement(vector<int> &nums) {
        int l = 0, r = size(nums)-1;
        while (l < r) {
            int m = (l+r) / 2;
            if (nums[m] > nums[m+1])
                r = m;
            else
                l = m+1;
        }
        return l;
    }
};
```

</details>

## search in rotated sorted array
Problem Link: https://leetcode.com/problems/search-in-rotated-sorted-array

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums)-1
        while l <= r:
            m = (l+r) // 2
            if target == nums[m]:
                return m
            if nums[l] <= nums[m]:
                if target > nums[m] or target < nums[l]:
                    l = m+1
                else:
                    r = m-1
            else:
                if target < nums[m] or target > nums[r]:
                    r = m-1
                else:
                    l = m+1
        return -1
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-II.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int l = 0, r = size(nums)-1;
        while (l <= r) {
            int m = (l+r) / 2;
            if (target == nums[m])
                return m;
            if (nums[l] <= nums[m]) {
                if (target > nums[m] or target < nums[l])
                    l = m+1;
                else
                    r = m-1;
            }
            else {
                if (target < nums[m] or target > nums[r])
                    r = m-1;
                else
                    l = m+1;
            }
        }
        return -1;
    }
};
```

</details>

## word search
Problem Link: https://leetcode.com/problems/word-search

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        def dfs(x, y, idx):
            if idx == len(word):
                return True
            if not(0 <= x < n and 0 <= y < m) or visited[x][y] or \
                board[x][y] != word[idx]:
                return False
            visited[x][y] = 1
            for i, j in d:
                if dfs(x+i, y+j, idx+1):
                    return True
            visited[x][y] = 0
            return False

        n, m = len(board), len(board[0])
        visited = [[0 for i in range(m)] for j in range(n)]
        d = [(0, 1), (1, 0), (-1, 0), (0, -1)]
        for i in range(n):
            for j in range(m):
                if dfs(i, j, 0):
                    return True
        return False
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int n, m;
    vector<vector<int>> visited;
    int dx[] = {0, 0, 1, -1};
    int dy[] = {1, -1, 0, 0};

    bool dfs(int x, int y, int idx, const vector<vector<char>> &board, const string &word) {
        if (idx == size(word))
            return true;
        if (not(0 <= x < n and 0 <= y < m) or visited[x][y] or
            board[x][y] != word[idx])
            return false;
        visited[x][y] = 1;
        for (int i=0; i<4; i++) {
            if (dfs(x+dx[i], y+dy[i], idx+1, board, word))
                return true;
        }
        visited[x][y] = 0;
        return false;
    }
public:
    bool exist(vector<vector<char>> &board, string word) {
        n = size(board), m = size(board[0]);
        visited.assign(n, vector<int>(m, 0));
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                if (dfs(i, j, 0, board, word))
                    return true;
            }
        }
        return false;
    }
};
```
`TODO` RUN-TIME ERROR

</details>

## subsets ii
Problem Link: https://leetcode.com/problems/subsets-ii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        n = len(nums)
        res = set()
        for i in range(1<<n):
            curr_list = []
            for j in range(n):
                if 1<<j & i:
                    curr_list.append(nums[j])
            res.add(tuple(sorted(curr_list)))
        return list(res)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int> &nums) {
        int n = size(nums);
        set<vector<int>> res;
        for (int i=0; i<(1<<n); i++) {
            vector<int> curr_list;
            for (int j=0; j<n; j++)
                if (1<<j & i)
                    curr_list.push_back(nums[j]);
            sort(curr_list.begin(), curr_list.end());
            res.insert(curr_list);
        }
        vector<vector<int>> ans(res.begin(), res.end());
        return ans;
    }
};
```

</details>

## combination sum
Problem Link: https://leetcode.com/problems/combination-sum

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        def generate_combinations(i, arr, curr_total):
            if curr_total == target:
                res.append(sorted(arr[:]))
                return
            if i == len(candidates) or curr_total > target:
                return
            arr.append(candidates[i])
            generate_combinations(i, arr, curr_total+candidates[i])
            arr.pop()
            generate_combinations(i+1, arr, curr_total)

        res = []
        generate_combinations(0, [], 0)
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<vector<int>> res;

    void generate_combinations(int i, vector<int> &arr, int curr_total, vector<int> &candidates, int target) {
        if (curr_total == target) {
            sort(arr.begin(), arr.end());
            res.push_back(arr);
            return;
        }
        if (i == size(candidates) or curr_total > target)
            return;
        arr.push_back(candidates[i]);
        generate_combinations(i, arr, curr_total+candidates[i], candidates, target);
        arr.pop_back();
        generate_combinations(i+1, arr, curr_total, candidates, target);
    }
public:
    vector<vector<int>> combinationSum(vector<int> &candidates, int target) {
        generate_combinations(0, {}, 0, candidates, target);
        return res;
    }
};
```

</details>

## generate parentheses
Problem Link: https://leetcode.com/problems/generate-parentheses

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        def generate(cnt_open, cnt_close, s):
            if cnt_open == cnt_close == n:
                res.append(s)
                return
            if cnt_open < n:
                generate(cnt_open+1, cnt_close, s+'(')
            if cnt_close < cnt_open:
                generate(cnt_open, cnt_close+1, s+')')

        res = []
        generate(0, 0, '')
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    vector<string> res;

    void generate(int cnt_open, int cnt_close, string s, const int &n) {
        if (cnt_open == cnt_close and cnt_close == n) {
            res.push_back(s);
            return;
        }
        if (cnt_open < n)
            generate(cnt_open+1, cnt_close, s+"(", n);
        if (cnt_close < cnt_open)
            generate(cnt_open, cnt_close+1, s+")", n);
    }
public:
    vector<string> generateParenthesis(int n) {
        generate(0, 0, "", n);
        return res;
    }
};
```

</details>

## palindrome linked list
Problem Link: https://leetcode.com/problems/palindrome-linked-list

<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        stk = []
        curr = head
        while curr:
            stk.append(curr.val)
            curr = curr.next
        stk = stk[::-1]
        i = 0
        curr = head
        while curr:
            if stk[i] != curr.val:
                return False
            curr = curr.next
            i += 1
        return True
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool isPalindrome(ListNode *head) {
        vector<int> stk;
        ListNode *curr = head;
        while (curr) {
            stk.push_back(curr->val);
            curr = curr->next;
        }
        reverse(stk.begin(), stk.end());
        int i = 0;
        curr = head;
        while (curr) {
            if (stk[i] != curr->val)
                return false;
            curr = curr->next;
            i ++;
        }
        return true;
    }
};
```

</details>

## sudoku solver
Problem Link: https://leetcode.com/problems/sudoku-solver

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def solveSudoku(self, grid: List[List[str]]) -> None:
        def check_valid_value(i, j, v):
            for k in range(9):
                if grid[i][k] == v or grid[k][j] == v:
                    return False
            b, e = i//3*3, j//3*3
            for k in range(b, b+3):
                for w in range(e, e+3):
                    if grid[k][w] == v:
                        return False
            return True

        def solve_grid(i, j):
            if j == 9:
                i += 1
                j = 0
            if i == 9:
                return True
            if cpy_grid[i][j] != '.':
                return solve_grid(i, j+1)
            for k in range(1, 10):
                t = chr(k+ord('0'))
                if check_valid_value(i, j, t):
                    grid[i][j] = t
                    cpy_grid[i][j] = t
                    if solve_grid(i, j+1):
                        return True
                    grid[i][j] = '.'
                    cpy_grid[i][j] = '.'
            return False

        cpy_grid = [[i for i in j] for j in grid]
        solve_grid(0, 0)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool check_valid_value(vector<vector<char>> &grid, int i, int j, int v) {
        for (int k = 0; k < 9; k++)
            if (grid[i][k] == v or grid[k][j] == v)
                return false;
        int b = i/3*3, e = j/3*3;
        for (int k = b; k < b+3; k++)
            for (int w = e; w < e+3; w++)
                if (grid[k][w] == v)
                    return false;
        return true;
    }
    bool solve_grid(vector<vector<char>> &cpy_grid, vector<vector<char>> &grid, int i, int j) {
        if (j == 9) {
            i ++;
            j = 0;
        }
        if (i == 9)
            return true;
        if (cpy_grid[i][j] != '.')
            return solve_grid(cpy_grid, grid, i, j+1);
        for (int k = 1; k < 10; k++) {
            char t = k+'0';
            if (check_valid_value(grid, i, j, t)) {
                grid[i][j] = t;
                cpy_grid[i][j] = t;
                if (solve_grid(cpy_grid, grid, i, j+1))
                    return true;
            }
            grid[i][j] = '.';
            cpy_grid[i][j] = '.';
        }
        return false;
    }
public:
    void solveSudoku(vector<vector<char>> &grid) {
        vector<vector<char>> cpy_grid(grid);
        solve_grid(cpy_grid, grid, 0, 0);
    }
};
```

</details>

## reverse nodes in k group
Problem Link: https://leetcode.com/problems/reverse-nodes-in-k-group

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        def reverseList(head, tail):
            if head == None:
                return head
            prv = None
            cur = head
            nxt = cur.next
            while nxt != tail:
                cur.next = prv
                prv = cur
                cur = nxt
                nxt = nxt.next
            cur.next = prv
            return cur

        i = 0
        res = ListNode(0, head)
        curr_tail = res.next
        curr_head = res
        last_head = res.next
        while curr_tail:
            i += 1
            curr_tail = curr_tail.next
            if i % k == 0:
                curr_head.next = reverseList(curr_head.next, curr_tail)
                last_head.next = curr_tail
                curr_head = last_head
                last_head = curr_tail
        return res.next
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
     ListNode* reverseList(ListNode *head, ListNode *tail) {
            if (head == NULL)
                return head;
            ListNode *prv = NULL;
            ListNode *cur = head;
            ListNode *nxt = cur->next;
            while (nxt != tail) {
                cur->next = prv;
                prv = cur;
                cur = nxt;
                nxt = nxt->next;
            }
            cur->next = prv;
            return cur;
     }
public:
    ListNode* reverseKGroup(ListNode *head, int k) {
        int i = 0;
        ListNode *res = new ListNode(0, head);
        ListNode *curr_tail = res->next;
        ListNode *curr_head = res;
        ListNode *last_head = res->next;
        while (curr_tail) {
            i ++;
            curr_tail = curr_tail->next;
            if (i % k == 0) {
                curr_head->next = reverseList(curr_head->next, curr_tail);
                last_head->next = curr_tail;
                curr_head = last_head;
                last_head = curr_tail;
            }
        }
        return res->next;
    }
};
```

</details>

## employee free time
Problem Link: https://leetcode.com/problems/employee-free-time

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## count of range sum
Problem Link: https://leetcode.com/problems/count-of-range-sum

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def countRangeSum(self, nums: List[int], lower: int, upper: int) -> int:
        def merge_sort(l, r):
            m = (l+r) // 2
            if l == m:
                return 0
            res = merge_sort(l, m) + merge_sort(m, r)
            i, j = m, m
            for k in range(l, m):
                while i < r and cumulative_sum[i] - cumulative_sum[k] <  lower:
                    i += 1
                while j < r and cumulative_sum[j] - cumulative_sum[k] <= upper:
                    j += 1
                res += j - i
            cumulative_sum[l:r] = sorted(cumulative_sum[l:r])
            return res

        cumulative_sum = [0] * (len(nums)+1)
        for i in range(len(nums)):
            cumulative_sum[i+1] = cumulative_sum[i] + nums[i]
        return merge_sort(0, len(cumulative_sum))
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int merge_sort(int l, int r, vector<long> &cumulative_sum, int lower, int upper) {
        int m = (l+r) / 2;
        if (l == m)
            return 0;
        int res = merge_sort(l, m, cumulative_sum, lower, upper) +
                  merge_sort(m, r, cumulative_sum, lower, upper);
        int i = m, j = m;
        for (int k=l; k<m; k++) {
            while (i < r and cumulative_sum[i] - cumulative_sum[k] <  lower)
                i ++;
            while (j < r and cumulative_sum[j] - cumulative_sum[k] <= upper)
                j ++;
            res += j - i;
        }
        sort(cumulative_sum.begin()+l, cumulative_sum.begin()+r);
        return res;
    }
public:
    int countRangeSum(vector<int> &nums, int lower, int upper) {
        vector<long> cumulative_sum(size(nums)+1, 0);
        for (int i=0; i<size(nums); i++)
            cumulative_sum[i+1] = cumulative_sum[i] + nums[i];
        return merge_sort(0, size(cumulative_sum), cumulative_sum, lower, upper);
    }
};
```

</details>

## rearrange string k distance apart
Problem Link: https://leetcode.com/problems/rearrange-string-k-distance-apart

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## alien dictionary
Problem Link: https://leetcode.com/problems/alien-dictionary

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## serialize and deserialize binary tree
Problem Link: https://leetcode.com/problems/serialize-and-deserialize-binary-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Codec:
    def serialize(self, root):
        def dfs(node):
            if not node:
                res.append("NA")
                return
            res.append(str(node.val))
            dfs(node.left)
            dfs(node.right)

        res = []
        dfs(root)
        return ','.join(res)

    def deserialize(self, s):
        def dfs():
            nonlocal i
            if vals[i] == "NA":
                return None
            node = TreeNode(int(vals[i]))
            i += 1
            node.left  = dfs()
            i += 1
            node.right = dfs()
            return node

        vals = s.split(",")
        i = 0
        return dfs()
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Codec {
    vector<string> vals;
    vector<string> res;

    void dfs1(TreeNode *node) {
        if (not node) {
            res.push_back("NA");
            return;
        }
        res.push_back(to_string(node->val));
        dfs1(node->left);
        dfs1(node->right);
    }
    TreeNode* dfs2(int &i) {
        if (vals[i] == "NA")
            return NULL;
        TreeNode *node = new TreeNode(stoi(vals[i]));
        i ++;
        node->left  = dfs2(i);
        i ++;
        node->right = dfs2(i);
        return node;
    }
public:
    string serialize(TreeNode *root) {
        dfs1(root);
        stringstream temp;
        copy(res.begin(), res.end(), ostream_iterator<string>(temp, ","));
        return temp.str();
    }
    TreeNode* deserialize(string s) {
        int pos = 0;
        string token;
        while ((pos = s.find(',')) != string::npos) {
            token = s.substr(0, pos);
            vals.push_back(token);
            s.erase(0, pos+1);
        }
        int i = 0;
        return dfs2(i);
    }
};
```

</details>

## trapping rain water
Problem Link: https://leetcode.com/problems/trapping-rain-water

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def trap(self, height: List[int]) -> int:
        if not height:
            return 0
        l, r = 0, len(height)-1
        l_max, r_max = height[l], height[r]
        res = 0
        while l < r:
            if l_max < r_max:
                l += 1
                l_max = max(l_max, height[l])
                res += l_max - height[l]
            else:
                r -= 1
                r_max = max(r_max, height[r])
                res += r_max - height[r]
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int trap(vector<int> &height) {
        if (not size(height))
            return 0;
        int l = 0, r = size(height)-1;
        int l_max = height[l], r_max = height[r];
        int res = 0;
        while (l < r) {
            if (l_max < r_max) {
                l ++;
                l_max = max(l_max, height[l]);
                res += l_max - height[l];
            }
            else {
                r --;
                r_max = max(r_max, height[r]);
                res += r_max - height[r];
            }
        }
        return res;
    }
};
```

</details>

## concatenated words
Problem Link: https://leetcode.com/problems/concatenated-words

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findAllConcatenatedWordsInADict(self, words: List[str]) -> List[str]:
        words_set = set(words)
        res = []
        for word in words:
            dp = [False] * (len(word)+1)
            dp[0] = True
            for i in range(len(word)):
                if not dp[i]:
                    continue
                for j in range(i+1, len(word)+1):
                    if j - i < len(word) and word[i:j] in words_set:
                        dp[j] = True
                if dp[len(word)]:
                    res.append(word)
                    break
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<string> findAllConcatenatedWordsInADict(vector<string>& words) {
        set<string> words_set(words.begin(), words.end());
        vector<string> res;
        for (string word : words) {
            vector<bool> dp(size(word), false);
            dp[0] = true;
            for (int i=0; i<size(word); i++) {
                if (not dp[i])
                    continue;
                for (int j=i+1; j<size(word)+1; j++) {
                    if (j - i < size(word) and words_set.find(word.substr(i, j-i)) != words_set.end())
                        dp[j] = true;
                }
                if (dp[size(word)]) {
                    res.push_back(word);
                    break;
                }
            }
        }
        return res;
    }
};
```

</details>

## prefix and suffix search
Problem Link: https://leetcode.com/problems/prefix-and-suffix-search

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Trie:
    class TrieNode:
        def __init__(self):
            self.child = [None] * 26
            self.idx = []

    def __init__(self):
        self.root = self.TrieNode()

    def insert(self, word, j):
        curr = self.root
        curr.idx.append(j)
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] == None:
                curr.child[i] = self.TrieNode()
            curr = curr.child[i]
            curr.idx.append(j)

    def find(self, word):
        curr = self.root
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] != None:
                curr = curr.child[i]
            else:
                return []
        return curr.idx

class WordFilter:
    def __init__(self, words: List[str]):
        self.pref_trie = Trie()
        self.suff_trie = Trie()
        for i in range(len(words)-1, -1, -1):
            self.pref_trie.insert(words[i], i)
            self.suff_trie.insert(words[i][::-1], i)

    def f(self, pref: str, suff: str) -> int:
        pref_idx = self.pref_trie.find(pref)
        suff_idx = self.suff_trie.find(suff[::-1])
        i, j = 0, 0
        while i != len(pref_idx) and j != len(suff_idx):
            if pref_idx[i] > suff_idx[j]:
                i += 1
            elif pref_idx[i] < suff_idx[j]:
                j += 1
            else:
                return pref_idx[i]
        return -1
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Trie {
    class TrieNode {
    public:
        map<int, TrieNode*> child;
        int weight;
    };
public:
    TrieNode *root;
    Trie() {
        this->root = new TrieNode();
    }
    void insert(string word, int j) {
        TrieNode *curr = this->root;
        curr->weight = j;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                curr->child[i] = new TrieNode();
            curr = curr->child[i];
            curr->weight = j;
        }
    }
    int find(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] != NULL)
                curr = curr->child[i];
            else
                return -1;
        }
        return curr->weight;
    }
};

class WordFilter {
    Trie t;
public:
     WordFilter(vector<string> &words) {
        for (int i=0; i<size(words); i++) {
            for (int j=0; j<size(words[i])+1; j++)
                t.insert(words[i].substr(j) + "." + words[i], i);
        }
     }
     int f(string pref, string suff) {
        return t.find(suff + "." + pref);
    }
};
```

</details>

## design search autocomplete system
Problem Link: https://leetcode.com/problems/design-search-autocomplete-system

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## word squares
Problem Link: https://leetcode.com/problems/word-squares

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## median of two sorted arrays
Problem Link: https://leetcode.com/problems/median-of-two-sorted-arrays

<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        def findKth(A, B, k):
            n, m = len(A), len(B)
            if n > m:
                A, B = B, A
                n, m = m, n
            l, r = 0, n
            while l < r:
                mid = (l+r) // 2
                if 0 <= k-1-mid < m and A[mid] >= B[k-1-mid]:
                    r = mid
                else:
                    l = mid + 1
            x = A[l-1]   if l-1 >= 0   else -2e9
            y = B[k-1-l] if k-1-l >= 0 else -2e9
            return max(x, y)

        n, m = len(nums1), len(nums2)
        return (findKth(nums1, nums2, (n+m+1) // 2) +
                findKth(nums1, nums2, (n+m+2) // 2)) / 2.0
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/hard-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int> &nums1, vector<int> &nums2) {
        int n = size(nums1), m = size(nums2);
        return (findKth(nums1, nums2, (n+m+1) / 2) +
                findKth(nums1, nums2, (n+m+2) / 2)) / 2.0;
    }
    int findKth(vector<int> &A, vector<int> &B, int k) {
        int n = size(A), m = size(B);
        if (n > m) {
            swap(A, B);
            swap(n, m);
        }
        int l = 0, r = n;
        while (l < r) {
            int mid = (l+r) / 2;
            if (0 <= k-1-mid and k-1-mid < m and A[mid] >= B[k-1-mid])
                r = mid;
            else
                l = mid + 1;
        }
        int x = l-1 >= 0?   A[l-1]   : -2e9;
        int y = k-1-l >= 0? B[k-1-l] : -2e9;
        return max(x, y);
    }
};
```

</details>

## sort characters by frequency
Problem Link: https://leetcode.com/problems/sort-characters-by-frequency

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
import queue

class Solution:
    def frequencySort(self, s: str) -> str:
        cnt = {}
        for i in s:
            cnt[i] = cnt.get(i, 0) + 1
        max_heap = queue.PriorityQueue()
        for i, j in cnt.items():
            max_heap.put((-j, i))
        res = ''
        while not max_heap.empty():
            v, j = max_heap.get()
            res += j * -v
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    string frequencySort(string s) {
        map<char, int> cnt;
        for (char i : s)
            cnt[i] ++;
        priority_queue<pair<int, char>> max_heap;
        for (auto &[i, j] : cnt)
            max_heap.push({j, i});
        string res = "";
        while (not max_heap.empty()) {
            auto [v, j] = max_heap.top();
            max_heap.pop();
            res += string(v, j);
        }
        return res;
    }
};
```

</details>

## reorganize string
Problem Link: https://leetcode.com/problems/reorganize-string

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
import queue

class Solution:
    def reorganizeString(self, s: str) -> str:
        cnt = {}
        for i in s:
            cnt[i] = cnt.get(i, 0) + 1
        if max(cnt.values()) > (len(s)+1) // 2:
            return ''
        max_heap = queue.PriorityQueue()
        for i, j in cnt.items():
            max_heap.put((-j, i))
        res, prev = '', None
        while not max_heap.empty():
            v, j = max_heap.get()
            res += j
            if prev:
                max_heap.put(prev)
                prev = None
            if v+1 != 0:
                prev = (v+1, j)
        return res

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    string reorganizeString(string s) {
        map<char, int> cnt;
        for (char i : s)
            cnt[i] ++;
        auto comp = [](const pair<char,int> &a, const pair<char,int> &b) { return a.second < b.second; };
        auto max_val = max_element(cnt.begin(), cnt.end(), comp);
        if (max_val->second > (size(s)+1) / 2)
            return "";
        priority_queue<pair<int, char>> max_heap;
        for (auto &[i, j] : cnt)
            max_heap.push({j, i});
        string res = "";
        pair<int, char> prev = {-1, '$'};
        while (not max_heap.empty()) {
            auto [v, j] = max_heap.top();
            max_heap.pop();
            res += j;
            if (prev.first != -1) {
                max_heap.push(prev);
                prev = {-1, '$'};
            }
            if (v-1 != 0)
                prev = {v-1, j};
        }
        return res;
    }
};
```

</details>

## minimum height trees
Problem Link: https://leetcode.com/problems/minimum-height-trees

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
        if n == 1:
            return [0]
        degree = [0] * n
        adj = {i: [] for i in range(n)}
        for i, j in edges:
            adj[i].append(j)
            adj[j].append(i)
            degree[i] += 1
            degree[j] += 1
        que = []
        for i in range(len(degree)):
            if degree[i] == 1:
                que.append(i)
        res = []
        while que:
            res.clear()
            queue_len = len(que)
            for i in range(queue_len):
                u = que.pop(0)
                res.append(u)
                for v in adj[u]:
                    degree[v] -= 1
                    if degree[v] == 1:
                        que.append(v)
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> findMinHeightTrees(int n, vector<vector<int>> &edges) {
        if (n == 1)
            return {0};
        vector<int> degree(n, 0);
        vector<vector<int>> adj(n);
        for (auto v : edges) {
            adj[v[0]].push_back(v[1]);
            adj[v[1]].push_back(v[0]);
            degree[v[0]] ++;
            degree[v[1]] ++;
        }
        vector<int> que;
        for (int i=0; i<size(degree); i++) {
            if (degree[i] == 1)
                que.push_back(i);
        }
        vector<int> res;
        while (size(que)) {
            res.clear();
            int queue_len = size(que);
            for (int i=0; i<queue_len; i++) {
                int u = que[0];
                que.erase(que.begin());
                res.push_back(u);
                for (int v : adj[u]) {
                    degree[v] --;
                    if (degree[v] == 1)
                        que.push_back(v);
                }
            }
        }
        return res;
    }
};
```

</details>

## sequence reconstruction
Problem Link: https://leetcode.com/problems/sequence-reconstruction

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## path sum iii
Problem Link: https://leetcode.com/problems/path-sum-iii

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> int:
        def dfs(curr_node, curr_sum):
            res_left, res_right = 0, 0
            if curr_node.left:
                res_left  = dfs(curr_node.left,  curr_sum-curr_node.left.val)
            if curr_node.right:
                res_right = dfs(curr_node.right, curr_sum-curr_node.right.val)
            return res_left + res_right + int(curr_sum == 0)

        def dfs_tree(curr_node):
            if not curr_node:
                return 0
            return dfs_tree(curr_node.left) + \
                   dfs_tree(curr_node.right) + \
                   dfs(curr_node, targetSum-curr_node.val)

        return dfs_tree(root)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    int dfs(TreeNode *curr_node, long curr_sum) {
        int res_left = 0, res_right = 0;
        if (curr_node->left)
            res_left  = dfs(curr_node->left,  curr_sum-curr_node->left->val);
        if (curr_node->right)
            res_right = dfs(curr_node->right, curr_sum-curr_node->right->val);
        return res_left + res_right + int(curr_sum == 0);
    }

    int dfs_tree(TreeNode *curr_node, int targetSum) {
        if (not curr_node)
            return 0;
        return dfs_tree(curr_node->left, targetSum) +
               dfs_tree(curr_node->right, targetSum) +
               dfs(curr_node, targetSum-curr_node->val);
    }
public:
    int pathSum(TreeNode *root, int targetSum) {
        return dfs_tree(root, targetSum);
    }
};
```

</details>

## maximum binary tree
Problem Link: https://leetcode.com/problems/maximum-binary-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def constructMaximumBinaryTree(self, nums: List[int]) -> Optional[TreeNode]:
        def build_tree(nums):
            if len(nums) == 0:
                return None
            i = nums.index(max(nums))
            left_nums  = nums[:i]
            right_nums = nums[i+1:]
            root = TreeNode(max(nums))
            root.left  = build_tree(left_nums)
            root.right = build_tree(right_nums)
            return root

        return build_tree(nums)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* build_tree(vector<int> nums) {
        if (size(nums) == 0)
            return NULL;
        int i = max_element(nums.begin(), nums.end()) - nums.begin();
        vector<int> left_nums(nums.begin(), nums.begin()+i);
        vector<int> right_nums(nums.begin()+i+1, nums.end());
        TreeNode *root = new TreeNode(*max_element(nums.begin(), nums.end()));
        root->left  = build_tree(left_nums);
        root->right = build_tree(right_nums);
        return root;
    }
public:
    TreeNode* constructMaximumBinaryTree(vector<int> &nums) {
        return build_tree(nums);
    }
};
```

</details>

## maximum width of binary tree
Problem Link: https://leetcode.com/problems/maximum-width-of-binary-tree

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def widthOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        que = [(root, 0)]
        res = 0
        while que:
            curr_len = len(que)
            prt_width = que[0][1]
            last_width = -1
            for i in range(curr_len):
                curr, width = que.pop(0)
                if curr.left:
                    que.append((curr.left,  2*width - 2*prt_width))
                if curr.right:
                    que.append((curr.right, 2*width+1 - 2*prt_width))
                last_width = width
            res = max(res, last_width-prt_width+1)
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int widthOfBinaryTree(TreeNode *root) {
        vector<pair<TreeNode*, long>> que = {{root, 0}};
        int res = 0;
        while (size(que)) {
            int curr_len = size(que);
            int prt_width = que[0].second;
            int last_width;
            for (int i=0; i<curr_len; i++) {
                auto [curr, width] = que[0];
                que.erase(que.begin());
                if (curr->left)
                    que.push_back({curr->left,  2*width - 2*prt_width});
                if (curr->right)
                    que.push_back({curr->right, 2*width+1 - 2*prt_width});
                last_width = width;
            }
            res = max(res, last_width-prt_width+1);
        }
        return res;
    }
};
```

</details>

## construct binary tree from preorder and inorder traversal
Problem Link: https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        def build_tree(preorder, inorder):
            if len(preorder) == 0 or len(inorder) == 0:
                return None
            i = inorder.index(preorder[0])
            left_inorder  = inorder[:i]
            right_inorder = inorder[i+1:]
            left_preorder  = preorder[1:i+1]
            right_preorder = preorder[i+1:]
            root = TreeNode(preorder[0])
            root.left  = build_tree(left_preorder, left_inorder)
            root.right = build_tree(right_preorder, right_inorder)
            return root

        return build_tree(preorder, inorder)
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    TreeNode* build_tree(vector<int> preorder, vector<int> inorder) {
        if (size(preorder) == 0 or size(inorder) == 0)
            return NULL;
        int i = find(inorder.begin(), inorder.end(), preorder[0]) - inorder.begin();
        vector<int> left_inorder(inorder.begin(), inorder.begin()+i);
        vector<int> right_inorder(inorder.begin()+i+1, inorder.end());
        vector<int> left_preorder(preorder.begin()+1, preorder.begin()+i+1);
        vector<int> right_preorder(preorder.begin()+i+1, preorder.end());
        TreeNode *root = new TreeNode(preorder[0]);
        root->left  = build_tree(left_preorder, left_inorder);
        root->right = build_tree(right_preorder, right_inorder);
        return root;
    }
public:
    TreeNode* buildTree(vector<int> &preorder, vector<int> &inorder) {
        return build_tree(preorder, inorder);
    }
};
```

</details>

## 3Sum
Problem Link: https://leetcode.com/problems/3sum

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        res = set()
        nums.sort()
        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l, r = i+1, len(nums)-1
            while l < r:
                s = nums[i] + nums[l] + nums[r]
                if s > 0:
                    r -= 1
                elif s <= 0:
                    if s == 0 and (nums[i], nums[l], nums[r]) not in res:
                        res.add((nums[i], nums[l], nums[r]))
                    l += 1
        ans = list(res)
        return ans
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int> &nums) {
        set<vector<int>> res;
        sort(nums.begin(), nums.end());
        for (int i=0; i<size(nums); i++) {
            if (i > 0 and nums[i] == nums[i-1])
                continue;
            int l = i+1, r = size(nums)-1;
            while (l < r) {
                int s = nums[i] + nums[l] + nums[r];
                if (s > 0)
                    r --;
                else if (s <= 0) {
                    if (s == 0 and res.find({nums[i], nums[l], nums[r]}) == res.end())
                        res.insert({nums[i], nums[l], nums[r]});
                    l ++;
                }
            }
        }
        vector<vector<int>> ans(res.begin(), res.end());
        return ans;
    }
};
```

</details>

## container with most water
Problem Link: https://leetcode.com/problems/container-with-most-water

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l, r = 0, len(height)-1
        res = 0
        while l < r:
            res = max(res, min(height[l], height[r]) * (r - l))
            if height[l] < height[r]:
                l += 1
            elif height[r] < height[l]:
                r -= 1
            else:
                l += 1
                r -= 1
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int l = 0, r = size(height)-1;
        int res = 0;
        while (l < r) {
            res = max(res, min(height[l], height[r]) * (r - l));
            if (height[l] < height[r])
                l ++;
            else if (height[r] < height[l])
                r --;
            else {
                l ++;
                r --;
            }
        }
        return res;
    }
};
```

</details>

## maximum xor of two numbers in an array
Problem Link: https://leetcode.com/problems/maximum-xor-of-two-numbers-in-an-array

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMaximumXOR(self, nums: List[int]) -> int:
        mask, res = 0, 0
        for i in range(31, -1, -1):
            mask |= (1 << i)
            prefixes = set()
            for n in nums:
                prefixes.add(mask & n)
            temp = res | (1 << i)
            for p in prefixes:
                if (temp ^ p) in prefixes:
                    res = temp
                    break
        return res
```

</details>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-III.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findMaximumXOR(vector<int> &nums) {
        int mask = 0, res = 0;
        for (int i = 31; i >= 0; i--) {
            mask |= (1 << i);
            set<int> prefixes;
            for (int n : nums)
                prefixes.insert(mask & n);
            int temp = res | (1 << i);
            for (int p : prefixes) {
                if (prefixes.find((temp ^ p)) != prefixes.end()) {
                    res = temp;
                    break;
                }
            }
        }
        return res;
    }
};
```

</details>
