<a href="/level-2/leetcode/interviews-questions-2/solutions/dynam-programming.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 2 <br> Dynamic Programming `15 problems`




## number of longest increasing subsequence
Problem Link: https://leetcode.com/problems/number-of-longest-increasing-subsequence

<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def findNumberOfLIS(self, nums: List[int]) -> int:
        dp = {}
        len_lis, res = 0, 0
        for i in range(len(nums) - 1, -1, -1):
            max_len, max_cnt = 1, 1
            for j in range(i + 1, len(nums)):
                if nums[j] <= nums[i]:
                    continue
                length, cnt = dp[j]
                if length + 1 > max_len:
                    max_len, max_cnt = length + 1, cnt
                elif length + 1 == max_len:
                    max_cnt += cnt
            if max_len > len_lis:
                len_lis, res = max_len, max_cnt
            elif max_len == len_lis:
                res += max_cnt
            dp[i] = [max_len, max_cnt]
        return res
```

</details>
<br>
<a href="/level-3/leetcode/interviews-questions-1/solutions/medium-problems-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int findNumberOfLIS(vector<int> &nums) {
        map<int, pair<int, int>> dp;
        int len_lis = 0, res = 0;
        for (int i=size(nums)-1; i>-1; i--) {
            int max_len = 1, max_cnt = 1;
            for (int j=i+1; j<size(nums); j++) {
                if (nums[j] <= nums[i])
                    continue;
                auto [length, count] = dp[j];
                if (length + 1 > max_len)
                    max_len = length + 1, max_cnt = count;
                else if (length + 1 == max_len)
                    max_cnt += count;
            }
            if (max_len > len_lis)
                len_lis = max_len, res = max_cnt;
            else if (max_len == len_lis)
                res += max_cnt;
            dp[i] = {max_len, max_cnt};
        }
        return res;
    }
};
```

</details>
<br>

## maximum subarray
Problem Link: https://leetcode.com/problems/maximum-subarray

<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        curr_subarray_sum = 0
        max_subarray_sum = nums[0]
        for i in nums:
            curr_subarray_sum = max(curr_subarray_sum, 0)
            curr_subarray_sum += i
            max_subarray_sum = max(max_subarray_sum, curr_subarray_sum)
        return max_subarray_sum
```

</details>
<br>
<a href="/level-3/leetcode/interviews-questions-1/solutions/easy-problems.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int maxSubArray(vector<int> &nums) {
        int curr_subarray_sum = 0;
        int max_subarray_sum = nums[0];
        for (int i : nums) {
            curr_subarray_sum = max(curr_subarray_sum, 0);
            curr_subarray_sum += i;
            max_subarray_sum = max(max_subarray_sum, curr_subarray_sum);
        }
        return max_subarray_sum;
    }
};
```

</details>
<br>

