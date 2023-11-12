<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Stack and Queue `10 problems`

## sliding window maximum
Problem Link: https://leetcode.com/problems/sliding-window-maximum

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        dq = deque()
        res = []
        for i in range(len(nums)):
            while dq and nums[i] > dq[-1][0]:
                dq.pop()
            dq.append((nums[i], i))
            if i < k-1:
                continue
            res.append(dq[0][0])
            if i - dq[0][1] + 1 == k:
                dq.popleft()
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int> &nums, int k) {
        deque<pair<int, int>> dq;
        vector<int> res;
        for (int i=0; i<size(nums); i++) {
            while (size(dq) and nums[i] > dq.back().first)
                dq.pop_back();
            dq.push_back({nums[i], i});
            if (i < k-1)
                continue;
            res.push_back(dq[0].first);
            if (i - dq.front().second + 1 == k)
                dq.pop_front();
        }
        return res;
    }
};
```

</details>
<br>

## minimum size subarray sum
Problem Link: https://leetcode.com/problems/minimum-size-subarray-sum

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        i, total, res = 0, 0, 2e9
        for j in range(len(nums)):
            total += nums[j]
            while total >= target:
                res = min(res, j-i+1)
                total -= nums[i]
                i += 1
        return 0 if res == 2e9 else res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int minSubArrayLen(int target, vector<int> &nums) {
        int i = 0, total = 0, res = 2e9;
        for (int j=0; j<size(nums); j++) {
            total += nums[j];
            while (total >= target) {
                res = min(res, j-i+1);
                total -= nums[i];
                i ++;
            }
        }
        return res == 2e9 ? 0 : res;
    }
};
```

</details>
<br>

## longest substring without repeating characters
Problem Link: https://leetcode.com/problems/longest-substring-without-repeating-characters

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        curr_chars = set()
        res, j = 0, 0
        for i in s:
            while i in curr_chars:
                curr_chars.remove(s[j])
                j += 1
            curr_chars.add(i)
            res = max(res, len(curr_chars))
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        set<char> curr_chars;
        int res = 0, j = 0;
        for (char i : s) {
            while (curr_chars.find(i) != curr_chars.end()) {
                curr_chars.erase(curr_chars.find(s[j]));
                j ++;
            }
            curr_chars.insert(i);
            res = max(res, int(size(curr_chars)));
        }
        return res;
    }
};
```

</details>
<br>

## substring with concatenation of all words
Problem Link: https://leetcode.com/problems/substring-with-concatenation-of-all-words

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def findSubstring(self, s: str, words: List[str]) -> List[int]:
        cnt, sub = {}, {}
        res = []
        is_substr = True
        n = len(words[0])
        if len(s) <= 0 or len(s) < len(words)*n:
            return res
        for i in range(len(words)):
            cnt[words[i]] = cnt.get(words[i], 0) + 1
        for i in range(len(s)-n*len(words)+1):
            is_substr = True
            sub.clear()
            if s[i:i+n] not in cnt:
                continue
            for j in range(len(words)):
                next_word = s[i+j*n:i+j*n+n]
                if next_word in cnt:
                    sub[next_word] = sub.get(next_word, 0) + 1
                if next_word not in cnt or \
                    sub[next_word] > cnt[next_word]:
                    is_substr = False
                    break
            if is_substr == True:
                res.append(i)
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    vector<int> findSubstring(string s, vector<string> &words) {
        map<string, int> cnt;
        map<string, int> sub;
        vector<int> res;
        bool is_substr = true;
        int n = size(words[0]);
        if (size(s) <= 0 or size(s) < size(words)*n)
            return res;
        for (int i=0; i<size(words); i++)
            cnt[words[i]] ++;
        for (int i=0; i<size(s)-n*size(words)+1; i++) {
            is_substr = true;
            sub.clear();
            if (cnt.find(s.substr(i, n)) == cnt.end())
                continue;
            for (int j=0 ; j<size(words); j++) {
                string next_word = s.substr(i+j*n, n);
                if (cnt.find(next_word) != cnt.end())
                    sub[next_word] ++;
                if (cnt.find(next_word) == cnt.end() or
                    sub[next_word] > cnt[next_word]) {
                    is_substr = false;
                    break;
                }
            }
            if (is_substr == true)
                res.push_back(i);
        }
        return res;
    }
};
```

</details>
<br>

## minimum window substring
Problem Link: https://leetcode.com/problems/minimum-window-substring

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        cnt, window = {}, {}
        for i in t:
            cnt[i] = cnt.get(i, 0) + 1
        curr, need = 0, len(cnt)
        res_i, res_j, res_len = -1, -1, 2e5
        j = 0
        for i in range(len(s)):
            window[s[i]] = window.get(s[i], 0) + 1
            if s[i] in cnt and window[s[i]] == cnt[s[i]]:
                curr += 1
            while curr == need:
                if i-j+1 < res_len:
                    res_i, res_j, res_len = j, i, i-j+1
                window[s[j]] -= 1
                if s[j] in cnt and window[s[j]] < cnt[s[j]]:
                    curr -= 1
                j += 1
        return s[res_i:res_j+1] if res_len != 2e5 else ""
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    string minWindow(string s, string t) {
        map<char, int> cnt, window;
        for (char i : t)
            cnt[i] ++;
        int curr = 0, need = size(cnt);
        int res_i = -1, res_j = -1, res_len = 2e5;
        int j = 0;
        for (int i=0; i<size(s); i++) {
            window[s[i]] ++;
            if (cnt.find(s[i]) != cnt.end() and window[s[i]] == cnt[s[i]])
                curr ++;
            while (curr == need) {
                if (i-j+1 < res_len)
                    res_i = j, res_j = i, res_len = i-j+1;
                window[s[j]] --;
                if (cnt.find(s[j]) != cnt.end() and window[s[j]] < cnt[s[j]])
                    curr --;
                j ++;
            }
        }
        return res_len != 2e5? s.substr(res_i, res_j-res_i+1) : "";
    }
};
```

</details>
<br>

## backspace string compare
Problem Link: https://leetcode.com/problems/backspace-string-compare

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:
        def move(w, idx, cnt):
            while idx != -1 and w[idx] == '#':
                cnt += 1
                idx -= 1
            while idx != -1 and cnt > 0 and w[idx] != '#':
                cnt -= 1
                idx -= 1
            return idx, cnt

        i, j = len(s)-1, len(t)-1
        cnt_s, cnt_t = 0, 0
        prev_i, prev_j = -1, -1
        while i != prev_i and j != prev_j:
            while i != prev_i:
                prev_i = i
                i, cnt_s = move(s, i, cnt_s)
            while j != prev_j:
                prev_j = j
                j, cnt_t = move(t, j, cnt_t)
            if i >= 0 and j >= 0:
                if s[i] != t[j]:
                    return False
                else:
                    i -= 1
                    j -= 1
        return i == -1 and j == -1
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    void move(string w, int &idx, int &cnt) {
        while (idx != -1 and w[idx] == '#') {
            cnt ++;
            idx --;
        }
        while (idx != -1 and cnt > 0 and w[idx] != '#') {
            cnt --;
            idx --;
        }
    }
public:
    bool backspaceCompare(string s, string t) {
        int i = size(s)-1, j = size(t)-1;
        int cnt_s = 0, cnt_t = 0;
        int prev_i = -1, prev_j = -1;
        while (i != prev_i and j != prev_j) {
            while (i != prev_i) {
                prev_i = i;
                move(s, i, cnt_s);
            }
            while (j != prev_j) {
                prev_j = j;
                move(t, j, cnt_t);
            }
            if (i >= 0 and j >= 0) {
                if (s[i] != t[j])
                    return false;
                else
                    i --,
                    j --;
            }
        }
        return i == -1 and j == -1;
    }
};
```

</details>
<br>

## task scheduler
Problem Link: https://leetcode.com/problems/task-scheduler

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:
        cnt = {}
        max_cnt = 0
        for i in tasks:
            cnt[i] = cnt.get(i, 0) + 1
            max_cnt = max(max_cnt, cnt[i])
        res = (max_cnt-1) * (n+1)
        for i, j in cnt.items():
            if j == max_cnt:
                res += 1
        return max(res, len(tasks))
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int leastInterval(vector<char> &tasks, int n) {
        map<char, int> cnt;
        int max_cnt = 0;
        for (char i : tasks) {
            cnt[i] ++;
            max_cnt = max(max_cnt, cnt[i]);
        }
        int res = (max_cnt-1) * (n+1);
        for (auto &[i, j] : cnt) {
            if (j == max_cnt)
                res ++;
        }
        return max(res, int(size(tasks)));
    }
};
```

</details>
<br>

## permutation in string
Problem Link: https://leetcode.com/problems/permutation-in-string

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        if len(s1) > len(s2):
            return False
        cnt1, cnt2 = [0] * 26, [0] * 26
        for i in range(len(s1)):
            cnt1[ord(s1[i]) - ord('a')] += 1
            cnt2[ord(s2[i]) - ord('a')] += 1
        cnt_same = 0
        for i in range(26):
            if cnt1[i] == cnt2[i]:
                cnt_same += 1
        for i in range(len(s1), len(s2)):
            if cnt_same == 26:
                return True
            idx = ord(s2[i]) - ord('a')
            cnt2[idx] += 1
            if cnt1[idx] == cnt2[idx]:
                cnt_same += 1
            elif cnt1[idx] + 1 == cnt2[idx]:
                cnt_same -= 1
            idx = ord(s2[i-len(s1)]) - ord('a')
            cnt2[idx] -= 1
            if cnt1[idx] == cnt2[idx]:
                cnt_same += 1
            elif cnt1[idx] - 1 == cnt2[idx]:
                cnt_same -= 1
        return cnt_same == 26
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        if (size(s1) > size(s2))
            return false;
        vector<int> cnt1(26, 0), cnt2(26, 0);
        for (int i=0; i<size(s1); i++) {
            cnt1[s1[i]-'a'] ++;
            cnt2[s2[i]-'a'] ++;
        }
        int cnt_same = 0;
        for (int i=0; i<26; i++) {
            if (cnt1[i] == cnt2[i])
                cnt_same ++;
        }
        for (int i=size(s1); i<size(s2); i++) {
            if (cnt_same == 26)
                return true;
            int idx = s2[i] - 'a';
            cnt2[idx] ++;
            if (cnt1[idx] == cnt2[idx])
                cnt_same ++;
            else if (cnt1[idx] + 1 == cnt2[idx])
                cnt_same --;
            idx = s2[i-size(s1)] - 'a';
            cnt2[idx] --;
            if (cnt1[idx] == cnt2[idx])
                cnt_same ++;
            else if (cnt1[idx] - 1 == cnt2[idx])
                cnt_same --;
        }
        return cnt_same == 26;
    }
};
```

</details>
<br>

## longest repeating character replacement
Problem Link: https://leetcode.com/problems/longest-repeating-character-replacement

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        cnt = {}
        res, j, curr_max = 0, 0, 0
        for i in range(len(s)):
            cnt[s[i]] = cnt.get(s[i], 0) + 1
            curr_max = max(curr_max, cnt[s[i]])
            if i-j+1 - curr_max > k:
                cnt[s[j]] -= 1
                j += 1
            res = max(res, i-j+1)
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int characterReplacement(string s, int k) {
        map<char, int> cnt;
        int res = 0, j = 0, curr_max = 0;
        for (int i=0; i<size(s); i++) {
            cnt[s[i]] ++;
            curr_max = max(curr_max, cnt[s[i]]);
            if (i-j+1 - curr_max > k) {
                cnt[s[j]] --;
                j ++;
            }
            res = max(res, i-j+1);
        }
        return res;
    }
};
```

</details>
<br>

## minimum number of k consecutive bit flips
Problem Link: https://leetcode.com/problems/minimum-number-of-k-consecutive-bit-flips

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def minKBitFlips(self, nums: List[int], k: int) -> int:
        res, flipped = 0, 0
        is_flipped = [0] * len(nums)
        for i in range(len(nums)):
            if i >= k:
                flipped ^= is_flipped[i-k]
            if flipped != nums[i]:
                continue
            if i+k > len(nums):
                return -1
            is_flipped[i] = 1
            flipped = 1 - flipped
            res += 1
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int minKBitFlips(vector<int> &nums, int k) {
        int res = 0, flipped = 0;
        vector<int> is_flipped(size(nums), 0);
        for (int i=0; i<size(nums); i++) {
            if (i >= k)
                flipped ^= is_flipped[i-k];
            if (flipped != nums[i])
                continue;
            if (i+k > size(nums))
                return -1;
            is_flipped[i] = 1;
            flipped = 1 - flipped;
            res ++;
        }
        return res;
    }
};
```

</details>
<br>

## maximum frequency stack
Problem Link: https://leetcode.com/problems/maximum-frequency-stack

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class FreqStack:
    def __init__(self):
        self.max_freq = 0
        self.cnt = {}
        self.freq = {}

    def push(self, val: int) -> None:
        self.cnt[val] = self.cnt.get(val, 0) + 1
        if self.max_freq < self.cnt[val]:
            self.max_freq = self.cnt[val]
        if self.cnt[val] not in self.freq:
            self.freq[self.cnt[val]] = [val]
        else:
            self.freq[self.cnt[val]].append(val)

    def pop(self) -> int:
        x = self.freq[self.max_freq].pop()
        self.cnt[x] -= 1
        if not len(self.freq[self.max_freq]):
            self.max_freq -= 1
        return x
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class FreqStack {
    map<int, int> cnt;
    map<int, stack<int>> freq;
    int max_freq;
public:
    FreqStack() {
        max_freq = 0;
    }
    void push(int val) {
        cnt[val] ++;
        max_freq = max(max_freq, cnt[val]);
        freq[cnt[val]].push(val);
    }
    int pop() {
        int x = freq[max_freq].top();
        freq[max_freq].pop();
        cnt[x] --;
        if (not size(freq[max_freq]))
            max_freq --;
        return x;
    }
};
```

</details>
<br>

## sliding window median
Problem Link: https://leetcode.com/problems/sliding-window-median

<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def medianSlidingWindow(self, nums: List[int], k: int) -> List[float]:
        def binary_search(arr, x):
            l, r = 0, len(arr)
            while l < r:
                m = (l+r) // 2
                if arr[m] < x:
                    l = m + 1
                else:
                    r = m
            return l

        window = sorted(nums[:k-1])
        res = []
        for i in range(k-1, len(nums)):
            j = binary_search(window, nums[i])
            window.insert(j, nums[i])
            res.append((window[k//2] + window[(k-1)//2]) / 2.0)
            window.remove(nums[i-k+1])
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/stack-queue.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    int binary_search(vector<int> &arr, int x) {
        int l = 0, r = size(arr);
        while (l < r) {
            int m = (l+r) / 2;
            if (arr[m] < x)
                l = m + 1;
            else
                r = m;
        }
        return l;
    }
public:
    vector<double> medianSlidingWindow(vector<int> &nums, int k) {
        vector<int> window(nums.begin(), nums.begin()+k-1);
        sort(window.begin(), window.end());
        vector<double> res;
        for (int i=k-1; i<size(nums); i++) {
            int j = binary_search(window, nums[i]);
            window.insert(window.begin()+j, nums[i]);
            res.push_back((1LL*window[k/2] + 1LL*window[(k-1)/2]) / 2.0);
            window.erase(find(window.begin(), window.end(), nums[i-k+1]));
        }
        return res;
    }
};
```

</details>
<br>
