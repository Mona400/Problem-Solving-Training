<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Array and String `20 problems`

## Majority Element
Problem Link: https://leetcode.com/problems/majority-element

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>

## Jump Game
Problem Link: https://leetcode.com/problems/jump-game

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        res = len(nums)-1
        for i in range(len(nums)-1, -1, -1):
            if i + nums[i] >= res:
                res = i
        return res == 0
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool canJump(vector<int> &nums) {
        int res = size(nums)-1;
        for (int i=size(nums)-1; i>-1; i--) {
            if (i + nums[i] >= res)
                res = i;
        }
        return res == 0;
    }
};
```

</details>

## product of array except self
Problem Link: https://leetcode.com/problems/product-of-array-except-self

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        res = [1] * len(nums)
        for i in range(len(nums)-1):
            res[i+1] *= res[i] * nums[i]
        prod = 1
        for i in range(len(nums)-1, -1, -1):
            res[i] *= prod
            prod *= nums[i]
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> productExceptSelf(vector<int> &nums) {
        vector<int> res(size(nums), 1);
        for (int i=0; i<size(nums)-1; i++)
            res[i+1] *= res[i] * nums[i];
        int prod = 1;
        for (int i=size(nums)-1; i>-1; i--) {
            res[i] *= prod;
            prod *= nums[i];
        }
        return res;
    }
};
```

</details>

## search a 2d matrix ii
Problem Link: https://leetcode.com/problems/search-a-2d-matrix-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        n, m = len(matrix), len(matrix[0])
        i, j = 0, m-1
        while i < n and j >= 0:
            if matrix[i][j] > target:
                j -= 1
            elif matrix[i][j] < target:
                i += 1
            else:
                return True;
        return False
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>> &matrix, int target) {
        int n = size(matrix), m = size(matrix[0]);
        int i = 0, j = m-1;
        while (i < n and j >= 0) {
            if (matrix[i][j] > target)
                j --;
            else if (matrix[i][j] < target)
                i ++;
            else
                return true;
        }
        return false;
    }
};
```

</details>

## spiral matrix
Problem Link: https://leetcode.com/problems/spiral-matrix

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        d = [(0, 1), (1, 0), (0, -1), (-1, 0)]
        curr_dir, x, y = 0, 0, -1
        n, m = len(matrix), len(matrix[0])
        visited = [[0 for i in range(m)] for j in range(n)]
        res = [0] * (n*m)
        res_idx = 0
        for i in range(n):
            for j in range(m):
                x += d[curr_dir][0]
                y += d[curr_dir][1]
                res[res_idx] = matrix[x][y]
                res_idx += 1
                visited[x][y] = 1
                if not (0 <= x+d[curr_dir][0] < n and 0 <= y+d[curr_dir][1] < m) or \
                   visited[x+d[curr_dir][0]][y+d[curr_dir][1]]:
                    curr_dir = (curr_dir + 1) % 4
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>> &matrix) {
        vector<pair<int, int>> d = {{0, 1}, {1, 0}, {0, -1}, {-1, 0}};
        int curr_dir = 0, x = 0, y = -1;
        int n = size(matrix), m = size(matrix[0]);
        vector<vector<int>> visited(n, vector<int>(m, 0));
        vector<int> res(n*m, 0);
        int res_idx = 0;
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                x += d[curr_dir].first;
                y += d[curr_dir].second;
                res[res_idx] = matrix[x][y];
                res_idx ++;
                visited[x][y] = 1;
                if (not (0 <= x+d[curr_dir].first and x+d[curr_dir].first < n and
                         0 <= y+d[curr_dir].second and y+d[curr_dir].second < m) or
                    visited[x+d[curr_dir].first][y+d[curr_dir].second])
                    curr_dir = (curr_dir + 1) % 4;
            }
        }
        return res;
    }
};
```

</details>

## rotate image
Problem Link: https://leetcode.com/problems/rotate-image

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        n = len(matrix)
        for i in range(n//2):
            for j in range(i, n-i-1):
                k                    = matrix[i][j]
                matrix[i][j]         = matrix[n-j-1][i]
                matrix[n-j-1][i]     = matrix[n-i-1][n-j-1]
                matrix[n-i-1][n-j-1] = matrix[j][n-i-1]
                matrix[j][n-i-1]     = k
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    void rotate(vector<vector<int>> &matrix) {
        int n = size(matrix);
        for (int i = 0; i < n/2; i++) {
            for (int j = i; j < n-i-1; j++) {
                int k                = matrix[i][j];
                matrix[i][j]         = matrix[n-j-1][i];
                matrix[n-j-1][i]     = matrix[n-i-1][n-j-1];
                matrix[n-i-1][n-j-1] = matrix[j][n-i-1];
                matrix[j][n-i-1]     = k;
            }
        }
    }
};
```

</details>

## set matrix zeroes
Problem Link: https://leetcode.com/problems/set-matrix-zeroes

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        n, m = len(matrix), len(matrix[0])
        zero_rows = [0] * n
        zero_cols = [0] * m
        for i in range(n):
            for j in range(m):
                if matrix[i][j] == 0:
                    zero_rows[i] = zero_cols[j] = 1
        for i in range(n):
            for j in range(m):
                if zero_rows[i] or zero_cols[j]:
                    matrix[i][j] = 0
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>> &matrix) {
        int n = size(matrix), m = size(matrix[0]);
        vector<int> zero_rows(n, 0);
        vector<int> zero_cols(m, 0);
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                if (matrix[i][j] == 0)
                    zero_rows[i] = zero_cols[j] = 1;
            }
        }
        for (int i=0; i<n; i++) {
            for (int j=0; j<m; j++) {
                if (zero_rows[i] or zero_cols[j])
                    matrix[i][j] = 0;
            }
        }
    }
};
```

</details>

## add two numbers
Problem Link: https://leetcode.com/problems/add-two-numbers

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        cry = 0
        head = ListNode()
        curr = head
        while l1 or l2 or cry:
            cry += (l1.val if l1 else 0) + (l2.val if l2 else 0)
            curr.next = ListNode(cry % 10)
            cry //= 10
            curr = curr.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        return head.next
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode *l1, ListNode *l2) {
        int cry = 0;
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (l1 or l2 or cry) {
            cry += (l1? l1->val : 0) + (l2? l2->val : 0);
            curr->next = new ListNode(cry % 10);
            cry /= 10;
            curr = curr->next;
            l1 = l1? l1->next : NULL;
            l2 = l2? l2->next : NULL;
        }
        return head->next;
    }
};
```

</details>

## sort colors
Problem Link: https://leetcode.com/problems/sort-colors

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        def heapify(arr, n, i):
            j = -1
            while i != j:
                j = i
                left_idx  = 2*i+1
                right_idx = 2*i+2
                if left_idx < n and arr[left_idx] > arr[i]:
                    i = left_idx
                if right_idx < n and arr[right_idx] > arr[i]:
                    i = right_idx
                arr[i], arr[j] = arr[j], arr[i]

        def heap_sort(arr, n):
            for i in range(n//2, -1, -1):
                heapify(arr, n, i)
            for i in range(n-1, -1, -1):
                arr[0], arr[i] = arr[i], arr[0]
                heapify(arr, i, 0)

        heap_sort(nums, len(nums))
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    void heapify(vector<int> &arr, int n, int i) {
        int j = -1;
        while (i != j) {
            j = i;
            int left_idx  = 2*i+1;
            int right_idx = 2*i+2;
            if (left_idx < n and arr[left_idx] > arr[i])
                i = left_idx;
            if (right_idx < n and arr[right_idx] > arr[i])
                i = right_idx;
            swap(arr[i], arr[j]);
        }
    }
    void heap_sort(vector<int> &arr, int n) {
        for (int i = n/2; i >= 0; i--)
            heapify(arr, n, i);
        for (int i = n-1; i >= 0; i--) {
            swap(arr[0], arr[i]);
            heapify(arr, i, 0);
        }
    }
public:
    void sortColors(vector<int> &nums) {
        heap_sort(nums, size(nums));
    }
};
```

</details>

## find the duplicate number
Problem Link: https://leetcode.com/problems/find-the-duplicate-number

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        p1, p2 = nums[0], nums[0]
        for i in range(len(nums)):
            p1 = nums[p1]
            p2 = nums[nums[p2]]
            if p1 == p2:
                break
        p2 = nums[0]
        for i in range(len(nums)):
            if p1 == p2:
                break
            p1 = nums[p1]
            p2 = nums[p2]
        return p1
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findDuplicate(vector<int> &nums) {
        int p1 = nums[0], p2 = nums[0];
        for (int i=0; i<size(nums); i++) {
            p1 = nums[p1];
            p2 = nums[nums[p2]];
            if (p1 == p2)
                break;
        }
        p2 = nums[0];
        for (int i=0; i<size(nums); i++) {
            if (p1 == p2)
                break;
            p1 = nums[p1];
            p2 = nums[p2];
        }
        return p1;
    }
};
```

</details>

## first missing positive
Problem Link: https://leetcode.com/problems/first-missing-positive

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            if nums[i] < 0:
                nums[i] = 0
        for i in range(len(nums)):
            val = abs(nums[i])
            if 1 <= val <= len(nums):
                if nums[val-1] > 0:
                    nums[val-1] *= -1
                elif nums[val-1] == 0:
                    nums[val-1] = -(len(nums)+1)
        for i in range(len(nums)):
            if nums[i] >= 0:
                return i+1
        return len(nums)+1
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        for (int i=0; i<size(nums); i++) {
            if (nums[i] < 0)
                nums[i] = 0;
        }
        for (int i=0; i<size(nums); i++) {
            int val = abs(nums[i]);
            if (1 <= val and val <= size(nums)) {
                if (nums[val-1] > 0)
                    nums[val-1] *= -1;
                else if (nums[val-1] == 0)
                    nums[val-1] = -(size(nums)+1);
            }
        }
        for (int i=0; i<size(nums); i++) {
            if (nums[i] >= 0)
                return i+1;
        }
        return size(nums)+1;
    }
};
```

</details>

## best time to buy and sell stock
Problem Link: https://leetcode.com/problems/best-time-to-buy-and-sell-stock

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_vals = [1e4] * int(1e5+1)
        max_vals = [0]   * int(1e5+1)
        for i in range(len(prices)):
            min_vals[i+1] = min(min_vals[i], prices[i])
        for i in range(len(prices)-1, -1, -1):
            max_vals[i+1] = max(max_vals[i], prices[i])
        max_profit = 0
        for i in range(1, len(prices)+1):
            max_profit = max(max_profit, max_vals[i]-min_vals[i])
        return max_profit
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int maxProfit(vector<int> &prices) {
        vector<int> min_vals(1e5+1, 1e4);
        vector<int> max_vals(1e5+1, 0);
        for (int i=0; i<size(prices); i++)
            min_vals[i+1] = min(min_vals[i], prices[i]);
        for (int i=size(prices)-1; i>-1; i--)
            max_vals[i+1] = max(max_vals[i], prices[i]);
        int max_profit = 0;
        for (int i=1; i<size(prices)+1; i++)
            max_profit = max(max_profit, max_vals[i]-min_vals[i]);
        return max_profit;
    }
};
```

</details>

## missing number
Problem Link: https://leetcode.com/problems/missing-number

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        n = len(nums)
        return n*(n+1)//2 - sum(nums)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int missingNumber(vector<int> &nums) {
        int n = size(nums);
        return n*(n+1)/2 - accumulate(nums.begin(), nums.end(), 0);
    }
};
```

</details>

## find all numbers disappeared in an array
Problem Link: https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
        set_nums = set(nums)
        disappeared_num  = []
        for i in range(1, len(nums)+1):
            if i not in set_nums:
                disappeared_num.append(i)
        return disappeared_num
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int> &nums) {
        set<int> set_nums(nums.begin(), nums.end());
        vector<int> disappeared_num;
        for (int i=1; i<size(nums)+1; i++) {
            if (set_nums.find(i) == set_nums.end())
                disappeared_num.push_back(i);
        }
        return disappeared_num;
    }
};
```

</details>

## squares of a sorted array
Problem Link: https://leetcode.com/problems/squares-of-a-sorted-array

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        return sorted([i*i for i in nums])
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> sortedSquares(vector<int> &nums) {
        vector<int> res(nums);
        for (int &i : res)
            i *= i;
        sort(res.begin(), res.end());
        return res;
    }
};
```

</details>

## convert 1d array into 2d array
Problem Link: https://leetcode.com/problems/convert-1d-array-into-2d-array

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def construct2DArray(self, original: List[int], m: int, n: int) -> List[List[int]]:
        if n*m != len(original):
            return []
        res = [[[0] for i in range(n)] for j in range(m)]
        for i in range(len(original)):
            res[i//n][i%n] = original[i]
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> construct2DArray(vector<int> &original, int m, int n) {
        if (n*m != size(original))
            return {};
        vector<vector<int>> res(m);
        for (vector<int> &i : res)
            i = vector<int>(n);
        for (int i=0; i<size(original); i++)
            res[i/n][i%n] = original[i];
        return res;
    }
};
```

</details>

## find all duplicates in an array
Problem Link: https://leetcode.com/problems/find-all-duplicates-in-an-array

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findDuplicates(self, nums: List[int]) -> List[int]:
        res = []
        for i in range(len(nums)):
            if nums[abs(nums[i])-1] > 0:
                nums[abs(nums[i])-1] *= -1
            else:
                res.append(abs(nums[i]))
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> findDuplicates(vector<int> &nums) {
        vector<int> res;
        for (int i=0; i<size(nums); i++) {
            if (nums[abs(nums[i])-1] > 0)
                nums[abs(nums[i])-1] *= -1;
            else
                res.push_back(abs(nums[i]));
        }
        return res;
    }
};
```

</details>

## fruit into baskets
Problem Link: https://leetcode.com/problems/fruit-into-baskets

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        cnt = {}
        res, i = 0, 0
        for j in range(len(fruits)):
            cnt[fruits[j]] = cnt.get(fruits[j], 0) + 1
            while len(cnt) > 2:
                cnt[fruits[i]] -= 1
                if cnt[fruits[i]] == 0:
                    cnt.pop(fruits[i])
                i += 1
            res = max(res, j-i+1)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int totalFruit(vector<int> &fruits) {
        map<int, int> cnt;
        int res = 0, i = 0;
        for (int j=0; j<size(fruits); j++) {
            cnt[fruits[j]] ++;
            while (size(cnt) > 2) {
                cnt[fruits[i]] --;
                if (cnt[fruits[i]] == 0)
                    cnt.erase(fruits[i]);
                i ++;
            }
            res = max(res, j-i+1);
        }
        return res;
    }
};
```

</details>

## 3sum closest
Problem Link: https://leetcode.com/problems/3sum-closest

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        res = 2e4
        nums.sort()
        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            l, r = i+1, len(nums)-1
            while l < r:
                s = nums[i] + nums[l] + nums[r]
                if abs(s-target) < abs(res-target):
                    res = s
                if s > target:
                    r -= 1
                elif s <= target:
                    l += 1
                else:
                    return res
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int threeSumClosest(vector<int> &nums, int target) {
        int res = 2e4;
        sort(nums.begin(), nums.end());
        for (int i=0; i<size(nums); i++) {
            if (i > 0 and nums[i] == nums[i-1])
                continue;
            int l = i+1, r = size(nums)-1;
            while (l < r) {
                int s = nums[i] + nums[l] + nums[r];
                if (abs(s-target) < abs(res-target))
                    res = s;
                if (s > target)
                    r --;
                else if (s <= target)
                    l ++;
                else
                    return res;
            }
        }
        return res;
    }
};
```

</details>

## subarray product less than k
Problem Link: https://leetcode.com/problems/subarray-product-less-than-k

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        p, c, i = 1, 0, 0
        for j in range(len(nums)):
            p *= nums[j]
            while i <= j and p >= k:
                p //= nums[i]
                i += 1
            c += j-i+1
        return c
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int numSubarrayProductLessThanK(vector<int> &nums, int k) {
        int p=1, c=0, i=0;
        for (int j=0; j<size(nums); j++) {
            p *= nums[j];
            while (i <= j and p >= k) {
                p /= nums[i];
                i ++;
            }
            c += j-i+1;
        }
        return c;
    }
};
```

</details>

## count unique characters of all substrings of a given string
Problem Link: https://leetcode.com/problems/count-unique-characters-of-all-substrings-of-a-given-string

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def uniqueLetterString(self, s: str) -> int:
        idx = {chr(i): [-1, -1] for i in range(ord('A'), ord('Z')+1)}
        res = 0
        for i in range(len(s)):
            k, j = idx[s[i]]
            res += (i-j) * (j-k)
            idx[s[i]] = [j, i]
        for i in idx:
            k, j = idx[i]
            res += (len(s)-j) * (j-k)
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int uniqueLetterString(string s) {
        map<char, pair<int, int>> idx;
        for (char i='A'; i<='Z'; i++)
            idx[i] = {-1, -1};
        int res = 0;
        for (int i=0; i<size(s); i++) {
            auto [k, j] = idx[s[i]];
            res += (i-j) * (j-k);
            idx[s[i]] = {j, i};
        }
        for (auto &[i, v] : idx) {
            auto [k, j] = v;
            res += (size(s)-j) * (j-k);
        }
        return res;
    }
};
```

</details>

## course schedule iii
Problem Link: https://leetcode.com/problems/course-schedule-iii

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
import queue

class Solution:
    def scheduleCourse(self, courses: List[List[int]]) -> int:
        courses.sort(key = lambda x: x[1])
        max_heap = queue.PriorityQueue()
        now = 0
        for t, end in courses:
            now += t
            max_heap.put(-t)
            if now > end:
                now += max_heap.get()
        return max_heap.qsize()
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int scheduleCourse(vector<vector<int>> &courses) {
        auto comp = [](const vector<int> &x, const vector<int> &y) { return x[1] < y[1]; };
        sort(courses.begin(), courses.end(), comp);
        priority_queue<int> max_heap;
        int now = 0;
        for (auto &it : courses) {
            now += it[0];
            max_heap.push(it[0]);
            if (now > it[1]) {
                now += -max_heap.top();
                max_heap.pop();
            }
        }
        return size(max_heap);
    }
};
```

</details>

## meeting rooms
Problem Link: https://leetcode.com/problems/meeting-rooms

<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python

```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/array-string.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp

```

</details>
