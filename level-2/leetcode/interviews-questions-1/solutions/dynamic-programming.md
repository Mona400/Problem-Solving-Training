<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Dynamic Programming `15 problems`

## climbing stairs
Problem Link: https://leetcode.com/problems/climbing-stairs

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        memo = [0] * 46
        memo[0] = memo[1] = 1
        for i in range(2, n+1):
            memo[i] = memo[i-1] + memo[i-2]
        return memo[n]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int climbStairs(int n) {
        vector<int> memo(46, 0);
        memo[0] = memo[1] = 1;
        for (int i=2; i<n+1; i++)
            memo[i] = memo[i-1] + memo[i-2];
        return memo[n];
    }
};
```

</details>
<br>

## house robber
Problem Link: https://leetcode.com/problems/house-robber

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        res1, res2 = 0, 0
        for i in nums:
            temp = max(res1+i, res2)
            res1 = res2
            res2 = temp
        return res2
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int rob(vector<int> &nums) {
        int res1 = 0, res2 = 0;
        for (int i : nums) {
            int temp = max(res1+i, res2);
            res1 = res2;
            res2 = temp;
        }
        return res2;
    }
};
```

</details>
<br>

## word break
Problem Link: https://leetcode.com/problems/word-break

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> bool:
        dp = [0] * (len(s)+1)
        dp[len(s)] = 1
        for i in range(len(s)-1, -1, -1):
            for w in wordDict:
                if i+len(w) <= len(s) and s[i:i+len(w)] == w and dp[i+len(w)]:
                    dp[i] = dp[i+len(w)]
        return dp[0]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    bool wordBreak(string s, vector<string> &wordDict) {
        vector<int> dp(size(s)+1, 0);
        dp[size(s)] = 1;
        for (int i=size(s)-1; i>-1; i--) {
            for (string w : wordDict) {
                if (i+size(w) <= size(s) and s.substr(i, size(w)) == w and dp[i+size(w)])
                    dp[i] = dp[i+size(w)];
            }
        }
        return dp[0];
    }
};
```

</details>
<br>

## coin change
Problem Link: https://leetcode.com/problems/coin-change

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [int(1e4+3)] * (amount+1)
        dp[0] = 0
        for i in range(1, amount+1):
            for c in coins:
                if i - c >= 0:
                    dp[i] = min(dp[i], dp[i-c]+1)
        if dp[amount] == int(1e4+3):
            dp[amount] = -1
        return dp[amount]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int coinChange(vector<int> &coins, int amount) {
        vector<int> dp(amount+1, int(1e4+3));
        dp[0] = 0;
        for (int i=1; i<amount+1; i++) {
            for (int c : coins) {
                if (i - c >= 0)
                    dp[i] = min(dp[i], dp[i-c]+1);
            }
        }
        if (dp[amount] == int(1e4+3))
            dp[amount] = -1;
        return dp[amount];
    }
};
```

</details>
<br>

## longest increasing subsequence
Problem Link: https://leetcode.com/problems/longest-increasing-subsequence

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        res = [1] * len(nums)
        for i in range(len(nums)-1, -1, -1):
            for j in range(i+1, len(nums)):
                if nums[j] > nums[i]:
                    res[i] = max(res[i], res[j]+1)
        return max(res)
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int lengthOfLIS(vector<int> &nums) {
        vector<int> res(size(nums), 1);
        for (int i=size(nums)-1; i>-1; i--) {
            for (int j=i+1; j<size(nums); j++) {
                if (nums[j] > nums[i])
                    res[i] = max(res[i], res[j]+1);
            }
        }
        return *max_element(res.begin(), res.end());
    }
};
```

</details>
<br>

## longest palindromic substring
Problem Link: https://leetcode.com/problems/longest-palindromic-substring

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def get_longest(size_type):
            res = ''
            res_len = 0
            for i in range(len(s)):
                l, r = i, i+size_type
                while l >= 0 and r < len(s) and s[l] == s[r]:
                    if res_len < r-l+1:
                        res = s[l:r+1]
                        res_len = r-l+1
                    l -= 1
                    r += 1
            return res

        res1 = get_longest(0)
        res2 = get_longest(1)
        return res1 if len(res1) > len(res2) else res2
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    string get_longest(bool size_type, string &s) {
        string res = "";
        int res_len = 0;
        int l, r;
        for (int i=0; i<size(s); i++) {
            l = i, r = i+size_type;
            while (l >= 0 and r < size(s) and s[l] == s[r]) {
                if (res_len < r-l+1) {
                    res = s.substr(l, r-l+1);
                    res_len = r-l+1;
                }
                l --;
                r ++;
            }
        }
        return res;
    }
public:
    string longestPalindrome(string s) {
        string res1 = get_longest(0, s);
        string res2 = get_longest(1, s);
        return (size(res1) > size(res2))? res1 : res2;
    }
};
```

</details>
<br>

## maximum product subarray
Problem Link: https://leetcode.com/problems/maximum-product-subarray

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        res = max(nums)
        curr_min, curr_max = 1, 1
        for i in nums:
            prev_min, prev_max = curr_min, curr_max
            curr_min = min(prev_min, prev_max, 1) * i
            curr_max = max(prev_min, prev_max, 1) * i
            res = max(res, curr_min, curr_max)
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int maxProduct(vector<int> &nums) {
        int res = *max_element(nums.begin(), nums.end());
        int curr_min = 1, curr_max = 1;
        int prev_min = 1, prev_max = 1;
        for (int i : nums) {
            prev_min = curr_min, prev_max = curr_max;
            curr_min = min(min(prev_min, prev_max), 1) * i;
            curr_max = max(max(prev_min, prev_max), 1) * i;
            res = max(res, max(curr_min, curr_max));
        }
        return res;
    }
};
```

</details>
<br>

## unique paths
Problem Link: https://leetcode.com/problems/unique-paths

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        memo = [[0 for i in range(n)] for j in range(m)]
        memo[m-1] = [1] * n
        for i in range(m-2, -1, -1):
            memo[i][n-1] = 1
            for j in range(n-2, -1, -1):
                memo[i][j] = memo[i][j+1] + memo[i+1][j]
        return memo[0][0]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int uniquePaths(int m, int n) {
        vector<vector<int>> memo(m, vector<int>(n, 0));
        fill(memo[m-1].begin(), memo[m-1].end(), 1);
        for (int i=m-2; i>-1; i--) {
            memo[i][n-1] = 1;
            for (int j=n-2; j>-1; j--) {
                memo[i][j] = memo[i][j+1] + memo[i+1][j];
            }
        }
        return memo[0][0];
    }
};
```

</details>
<br>

## partition equal subset sum
Problem Link: https://leetcode.com/problems/partition-equal-subset-sum

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        nums_sum = sum(nums)
        if nums_sum % 2:
            return False
        all_sums = set([0])
        half = nums_sum // 2
        for i in nums:
            prev_all_sums = all_sums.copy()
            for j in prev_all_sums:
                all_sums.add(j+i)
            if half in all_sums:
                return True
        return False
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    bool canPartition(vector<int> &nums) {
        int nums_sum = accumulate(nums.begin(), nums.end(), 0);
        if (nums_sum % 2)
            return false;
        set<int> all_sums = {0};
        int half = nums_sum / 2;
        for (int i : nums) {
            set<int> prev_all_sums(all_sums.begin(), all_sums.end());
            for (int j : prev_all_sums)
                all_sums.insert(j+i);
            if (all_sums.find(half) != all_sums.end())
                return true;
        }
        return false;
    }
};
```

</details>
<br>

## range sum query immutable
Problem Link: https://leetcode.com/problems/range-sum-query-immutable

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class NumArray:
    def __init__(self, nums: List[int]):
        self.cumulative_sum = nums.copy()
        self.cumulative_sum.insert(0, 0)
        for i in range(1, len(nums)+1):
            self.cumulative_sum[i] += self.cumulative_sum[i-1]

    def sumRange(self, left: int, right: int) -> int:
        return self.cumulative_sum[right+1] - self.cumulative_sum[left]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class NumArray {
    vector<int> cumulative_sum;
public:
    NumArray(vector<int> &nums) {
        cumulative_sum.assign(nums.begin(), nums.end());
        cumulative_sum.insert(cumulative_sum.begin(), 0);
        for (int i=1; i<size(nums)+1; i++)
            cumulative_sum[i] += cumulative_sum[i-1];
    }
    int sumRange(int left, int right) {
        return cumulative_sum[right+1] - cumulative_sum[left];
    }
};
```

</details>
<br>

## counting bits
Problem Link: https://leetcode.com/problems/counting-bits

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def countBits(self, n: int) -> List[int]:
        cnt_ones = [0] * (n+1)
        for i in range(n+1):
            x = i
            cnt = 0
            while x > 0:
                cnt += x%2
                x //= 2
            cnt_ones[i] = cnt
        return cnt_ones
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    vector<int> countBits(int n) {
        vector<int> cnt_ones (n+1, 0);
        for (int i=0; i<n+1; i++) {
            int x = i;
            int cnt = 0;
            while (x > 0) {
                cnt += x%2;
                x /= 2;
            }
            cnt_ones[i] = cnt;
        }
        return cnt_ones;
    }
};
```

</details>
<br>

## house robber ii
Problem Link: https://leetcode.com/problems/house-robber-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        def rob_subarray(nums):
            res1, res2 = 0, 0
            for i in nums:
                temp = max(res1+i, res2)
                res1 = res2
                res2 = temp
            return res2

        if len(nums) == 1:
            return nums[0]
        return max(rob_subarray(nums[1:]), rob_subarray(nums[:-1]))
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    int rob_subarray(vector<int> &nums) {
        int res1 = 0, res2 = 0;
        for (int i : nums) {
            int temp = max(res1+i, res2);
            res1 = res2;
            res2 = temp;
        }
        return res2;
    }
public:
    int rob(vector<int> &nums) {
        if (size(nums) == 1)
            return nums[0];
        return max(rob_subarray({nums.begin()+1, nums.end()}),
                   rob_subarray({nums.begin(), nums.end()-1}));
    }
};
```

</details>
<br>

## combination sum iv
Problem Link: https://leetcode.com/problems/combination-sum-iv

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def combinationSum4(self, nums: List[int], target: int) -> int:
        N = int(1e3+1)
        dp = [0] * (2*N)
        dp[N] = 1
        for i in range(1, target+1):
            for j in nums:
                dp[i+N] += dp[i-j+N]
        return dp[target+N]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    static const int N = int(1e3+1);
    int dp[2*N] = {0};
public:
    int combinationSum4(vector<int> &nums, int target) {
        dp[N] = 1;
        for (int i=1; i<target+1; i++) {
            for (int j : nums) {
                dp[i+N] += dp[i-j+N];
            }
        }
        return dp[target+N];
    }
};
```
`TODO` RUN-TIME ERROR

</details>
<br>

## decode ways
Problem Link: https://leetcode.com/problems/decode-ways

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def numDecodings(self, s: str) -> int:
        def dp(i):
            if memo[i] != -1:
                return memo[i]
            if s[i] == '0':
                return 0
            res = dp(i+1)
            if i+1 < len(s) and 10 <= int(s[i]+s[i+1]) <= 26:
                res += dp(i+2)
            memo[i] = res
            return memo[i]

        memo = [-1] * (len(s)+1)
        memo[len(s)] = 1
        return dp(0)
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    int memo[101];

    int dp(int i, string &s) {
        if (memo[i] != -1)
            return memo[i];
        if (s[i] == '0')
            return 0;
        int res = dp(i+1, s);
        if (i+1 < size(s) and 10 <= stoi(s.substr(i, 2)) and stoi(s.substr(i, 2)) <= 26)
            res += dp(i+2, s);
        memo[i] = res;
        return memo[i];
    }
public:
    int numDecodings(string s) {
        memset(memo, -1, sizeof memo);
        memo[size(s)] = 1;
        return dp(0, s);
    }
};
```

</details>
<br>

## palindromic substrings
Problem Link: https://leetcode.com/problems/palindromic-substrings

<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        def count_pali(s, l, r):
            res = 0
            while l >=0 and r < len(s) and s[l] == s[r]:
                l -= 1
                r += 1
                res += 1
            return res

        res = 0
        for i in range(len(s)):
            res += count_pali(s, i, i)
            res += count_pali(s, i, i+1)
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/dynamic-programming.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    int count_pali(string s, int l, int r) {
        int res = 0;
        while (l >=0 and r < size(s) and s[l] == s[r]) {
            l --;
            r ++;
            res ++;
        }
        return res;
    }
public:
    int countSubstrings(string s) {
        int res = 0;
        for (int i=0; i<size(s); i++) {
            res += count_pali(s, i, i);
            res += count_pali(s, i, i+1);
        }
        return res;
    }
};
```

</details>
<br>
