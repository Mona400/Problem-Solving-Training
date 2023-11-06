<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Hashmap and Math `10 problems`

## longest consecutive sequence
Problem Link: https://leetcode.com/problems/longest-consecutive-sequence

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        longest_len = 0
        set_nums = set(nums)
        for i in set_nums:
            if i - 1 in set_nums:
                continue
            curr_len = 0
            while i + curr_len in set_nums:
                curr_len += 1
            longest_len = max(longest_len, curr_len)
        return longest_len
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int longestConsecutive(vector<int> &nums) {
        int longest_len = 0;
        set<int> set_nums(nums.begin(), nums.end());
        for (int i : set_nums) {
            if (set_nums.find(i - 1) != set_nums.end())
                continue;
            int curr_len = 0;
            while (set_nums.find(i + curr_len) != set_nums.end())
                curr_len ++;
            longest_len = max(longest_len, curr_len);
        }
        return longest_len;
    }
};
```

</details>

## merge intervals
Problem Link: https://leetcode.com/problems/merge-intervals

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort()
        res = [intervals[0]]
        for s, e in intervals:
            if s <= res[-1][1]:
                res[-1][1] = max(res[-1][1], e)
            else:
                res.append([s, e])
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>> &intervals) {
        sort(intervals.begin(), intervals.end());
        vector<vector<int>> res;
        res.push_back(intervals[0]);
        for (auto &it : intervals) {
            int s = it[0], e = it[1];
            if (s <= res[size(res)-1][1])
                res[size(res)-1][1] = max(res[size(res)-1][1], e);
            else
                res.push_back({s, e});
        }
        return res;
    }
};
```

</details>

## insert interval
Problem Link: https://leetcode.com/problems/insert-interval

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        i = 0
        res = []
        while i < len(intervals) and newInterval[0] > intervals[i][1]:
            res.append(intervals[i])
            i += 1
        while i < len(intervals) and newInterval[1] >= intervals[i][0]:
            newInterval = (min(newInterval[0], intervals[i][0]),
                           max(newInterval[1], intervals[i][1]))
            i += 1
        res.append(newInterval)
        while i < len(intervals):
            res.append(intervals[i])
            i += 1
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>> &intervals, vector<int> &newInterval) {
        int i = 0;
        vector<vector<int>> res;
        while (i < size(intervals) and newInterval[0] > intervals[i][1]) {
            res.push_back(intervals[i]);
            i ++;
        }
        while (i < size(intervals) and newInterval[1] >= intervals[i][0]) {
            newInterval = {min(newInterval[0], intervals[i][0]),
                           max(newInterval[1], intervals[i][1])};
            i ++;
        }
        res.push_back(newInterval);
        while (i < size(intervals)) {
            res.push_back(intervals[i]);
            i ++;
        }
        return res;
    }
};
```

</details>

## minimum number of arrows to burst balloons
Problem Link: https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        points.sort()
        res = 0
        prev_end = -int(1<<31)-1
        for s, e in points:
            if s > prev_end:
                prev_end = e
            else:
                res += 1
                prev_end = min(e, prev_end)
        return len(points) - res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    int findMinArrowShots(vector<vector<int>> &points) {
        sort(points.begin(), points.end());
        int res = 0;
        long prev_end = -long(1LL<<31)-1;
        for (auto &it : points) {
            int s = it[0], e = it[1];
            if (s > prev_end)
                prev_end = e;
            else {
                res ++;
                prev_end = min(long(e), prev_end);
            }
        }
        return size(points) - res;
    }
};
```

</details>

## word search ii
Problem Link: https://leetcode.com/problems/word-search-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Trie:
    class TrieNode:
        def __init__(self):
            self.child = [None] * 26
            self.end = False
            self.cnt = 0

    def __init__(self):
        self.root = self.TrieNode()

    def insert(self, word):
        curr = self.root
        curr.cnt += 1
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] == None:
                curr.child[i] = self.TrieNode()
            curr = curr.child[i]
            curr.cnt += 1
        curr.end = True

    def remove(self, word):
        curr = self.root
        curr.cnt -= 1
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] != None:
                curr = curr.child[i]
                curr.cnt -= 1

class Solution:
    def findWords(self, board: List[List[str]], words: List[str]) -> List[str]:
        def dfs(r, c, curr, word):
            if r < 0 or c < 0 or r == n or c == m or \
               not curr.child[ord(board[r][c]) - ord('a')] or \
               curr.child[ord(board[r][c]) - ord('a')].cnt < 1 or \
               (r, c) in visited:
                return
            visited.add((r, c))
            curr = curr.child[ord(board[r][c]) - ord('a')]
            word += board[r][c]
            if curr.end:
                curr.end = False
                res.add(word)
                t.remove(word)
            dfs(r+1, c, curr, word)
            dfs(r-1, c, curr, word)
            dfs(r, c+1, curr, word)
            dfs(r, c-1, curr, word)
            visited.remove((r, c))

        t = Trie()
        for w in words:
            t.insert(w)
        n, m = len(board), len(board[0])
        res, visited = set(), set()
        for r in range(n):
            for c in range(m):
                dfs(r, c, t.root, "")
        return list(res)
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class TrieNode {
public:
    vector<TrieNode*> child;
    bool end;
    int cnt;
    TrieNode() {
        this->child.assign(26, NULL);
        this->end = false;
        this->cnt = 0;
    }
};

class Trie {
public:
    TrieNode *root;
    Trie() {
        this->root = new TrieNode();
    }
    void insert(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                curr->child[i] = new TrieNode();
            curr = curr->child[i];
            curr->cnt ++;
        }
        curr->end = true;
    }
    void remove(string word) {
        TrieNode *curr = this->root;
        curr->cnt --;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] != NULL) {
                curr = curr->child[i];
                curr->cnt --;
            }
        }
    }
};

class Solution {
    int n, m;
    set<string> res;
    set<pair<int, int>> visited;
    Trie t;

    void dfs(int r, int c, TrieNode *curr, string word, const vector<vector<char>> &board) {
        if (r < 0 or c < 0 or r == n or c == m or
            not curr->child[board[r][c] - 'a'] or
            curr->child[board[r][c] - 'a']->cnt < 1 or
            visited.find({r, c}) != visited.end())
            return;
        visited.insert({r, c});
        curr = curr->child[board[r][c] - 'a'];
        word += board[r][c];
        if (curr->end) {
            curr->end = false;
            res.insert(word);
            t.remove(word);
        }
        dfs(r+1, c, curr, word, board);
        dfs(r-1, c, curr, word, board);
        dfs(r, c+1, curr, word, board);
        dfs(r, c-1, curr, word, board);
        visited.erase(visited.find({r, c}));
    }
public:
    vector<string> findWords(vector<vector<char>> &board, vector<string> &words) {
        t = Trie();
        for (string w : words)
            t.insert(w);
        n = size(board), m = size(board[0]);
        for (int r=0; r<n; r++)
            for (int c=0; c<m; c++)
                dfs(r, c, t.root, "", board);
        vector<string> ans(res.begin(), res.end());
        return ans;
    }
};
```

</details>

## implement trie prefix tree
Problem Link: https://leetcode.com/problems/implement-trie-prefix-tree

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Trie:
    class TrieNode:
        def __init__(self):
            self.child = [None] * 26
            self.end = False

    def __init__(self):
        self.root = self.TrieNode()

    def insert(self, word: str) -> None:
        curr = self.root
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] == None:
                curr.child[i] = self.TrieNode()
            curr = curr.child[i]
        curr.end = True

    def search(self, word: str) -> bool:
        curr = self.root
        for c in word:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
        return curr.end

    def startsWith(self, prefix: str) -> bool:
        curr = self.root
        for c in prefix:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
        return True
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Trie {
    class TrieNode {
    public:
        vector<TrieNode*> child;
        bool end;
        TrieNode() {
            this->child.assign(26, NULL);
            this->end = false;
        }
    };
    TrieNode *root;
public:
    Trie() {
        this->root = new TrieNode();
    }
    void insert(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                curr->child[i] = new TrieNode();
            curr = curr->child[i];
        }
        curr->end = true;
    }
    bool search(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
        }
        return curr->end;
    }
    bool startsWith(string prefix) {
        TrieNode *curr = this->root;
        for (char c : prefix) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
        }
        return true;
    }
};
```

</details>

## two sum
Problem Link: https://leetcode.com/problems/two-sum

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        idx = {}
        for i in range(len(nums)):
            idx[nums[i]] = idx.get(nums[i], [])
            idx[nums[i]].append(i)
        res = []
        for i in nums:
            if i in idx and target - i in idx:
                if i == target - i and len(idx[i]) == 1:
                    continue
                res = [idx[i][0], idx[target - i][-1]]
                break
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int> &nums, int target) {
        map<int, vector<int>> idx;
        for (int i=0; i<size(nums); i++)
            idx[nums[i]].push_back(i);
        vector<int> res;
        for (int i : nums) {
            if (idx.find(i) != idx.end() and idx.find(target - i) != idx.end()) {
                if (i == target - i and size(idx[i]) == 1)
                    continue;
                res = {idx[i][0], idx[target - i][size(idx[i])-1]};
                break;
            }
        }
        return res;
    }
};
```

</details>

## contains duplicate
Problem Link: https://leetcode.com/problems/contains-duplicate

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums) != len(set(nums))
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
public:
    bool containsDuplicate(vector<int> &nums) {
        set<int> set_nums(nums.begin(), nums.end());
        return size(nums) != size(set_nums);
    }
};
```

</details>

## longest word in dictionary
Problem Link: https://leetcode.com/problems/longest-word-in-dictionary

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Trie:
    class TrieNode:
        def __init__(self):
            self.child = [None] * 26
            self.end = False

    def __init__(self):
        self.root = self.TrieNode()

    def insert(self, word: str) -> None:
        curr = self.root
        for c in word:
            i = ord(c) - ord('a')
            if curr.child[i] == None:
                curr.child[i] = self.TrieNode()
            curr = curr.child[i]
        curr.end = True

    def search(self, word: str) -> bool:
        curr = self.root
        for c in word:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
        return curr.end

    def startsWith(self, prefix: str) -> bool:
        curr = self.root
        for c in prefix:
            i = ord(c) - ord("a")
            if curr.child[i] == None:
                return False
            curr = curr.child[i]
            if not curr.end:
                return False
        return True

class Solution:
    def longestWord(self, words: List[str]) -> str:
        t = Trie()
        words.sort()
        for w in words:
            t.insert(w)
        res = ''
        for w in words:
            if len(w) < len(res) or len(w) == len(res) and w >= res:
                continue
            if t.startsWith(w):
                res = w
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Trie {
    class TrieNode {
    public:
        vector<TrieNode*> child;
        bool end;
        TrieNode() {
            this->child.assign(26, NULL);
            this->end = false;
        }
    };
    TrieNode *root;
public:
    Trie() {
        this->root = new TrieNode();
    }
    void insert(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                curr->child[i] = new TrieNode();
            curr = curr->child[i];
        }
        curr->end = true;
    }
    bool search(string word) {
        TrieNode *curr = this->root;
        for (char c : word) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
        }
        return curr->end;
    }
    bool startsWith(string prefix) {
        TrieNode *curr = this->root;
        for (char c : prefix) {
            int i = c - 'a';
            if (curr->child[i] == NULL)
                return false;
            curr = curr->child[i];
            if (not curr->end)
                return false;
        }
        return true;
    }
};

class Solution {
public:
    string longestWord(vector<string>& words) {
        Trie t = Trie();
        sort(words.begin(), words.end());
        for (string w : words)
            t.insert(w);
        string res = "";
        for (string w : words) {
            if (size(w) < size(res) or size(w) == size(res) and w >= res)
                continue;
            if (t.startsWith(w))
                res = w;
        }
        return res;
    }
};
```

</details>

## smallest range covering elements from k lists
Problem Link: https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
import queue

class Solution:
    def smallestRange(self, nums: List[List[int]]) -> List[int]:
        min_heap = queue.PriorityQueue()
        max_end = -2e5
        for i in range(len(nums)):
            min_heap.put((nums[i][0], i, 0))
            max_end = max(max_end, nums[i][0])
        t, i, j = min_heap.get()
        res = [t, max_end]
        while j < len(nums[i])-1:
            max_end = max(max_end, nums[i][j+1])
            min_heap.put((nums[i][j+1], i, j+1))
            t, i, j = min_heap.get()
            if max_end - t < res[1] - res[0]:
                res[0], res[1] = t, max_end
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    struct Item {
        int t, i, j;
        Item(int t, int i, int j) :
            t(t), i(i), j(j) {
        }
    };
public:
    vector<int> smallestRange(vector<vector<int>> &nums) {
        auto comp = [](const Item &x, const Item &y) { return x.t > y.t; };
        priority_queue<Item, vector<Item>, decltype(comp)> min_heap(comp);
        int max_end = -2e5;
        for (int i=0; i<size(nums); i++) {
            min_heap.push(Item(nums[i][0], i, 0));
            max_end = max(max_end, nums[i][0]);
        }
        Item x = min_heap.top();
        min_heap.pop();
        vector<int> res = {x.t, max_end};
        while (x.j < size(nums[x.i])-1) {
            max_end = max(max_end, nums[x.i][x.j+1]);
            min_heap.push(Item(nums[x.i][x.j+1], x.i, x.j+1));
            x = min_heap.top();
            min_heap.pop();
            if (max_end - x.t < res[1] - res[0])
                res[0] = x.t, res[1] = max_end;
        }
        return res;
    }
};
```

</details>

## palindrome pairs
Problem Link: https://leetcode.com/problems/palindrome-pairs

<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/python.png"></img></a>
<details>
    <summary><h5>Python Solution</h5></summary>

```python
class Solution:
    def palindromePairs(self, words: List[str]) -> List[List[int]]:
        def is_palindrome(s, i, j):
            while i < j and s[i] == s[j]:
                i += 1
                j -= 1
            return i >= j

        idx = {}
        words_len = set()
        res = []
        for i in range(len(words)):
            idx[words[i]] = i
            words_len.add(len(words[i]))
        for i in range(len(words)):
            rev_word = words[i][::-1]
            if rev_word in idx and idx[rev_word] != i:
                res.append((idx[rev_word] , i))
            word_len = len(rev_word)
            for j in words_len:
                if j >= word_len:
                    continue
                suff = rev_word[word_len-j:]
                pref = rev_word[:j]
                if is_palindrome(rev_word, 0, word_len-j-1) and suff in idx:
                    res.append((i , idx[suff]))
                if is_palindrome(rev_word, j, word_len-1) and pref in idx:
                    res.append((idx[pref], i))
        return res
```

</details>
<a href="/level-2/leetcode/interviews-questions-1/solutions/hashmap-math.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/main/repos-logos/cpp.png"></img></a>
<details>
    <summary><h5>CPP Solution</h5></summary>

```cpp
class Solution {
    bool is_palindrome(string &s, int i, int j) {
        while (i < j and s[i] == s[j]) {
            i ++;
            j --;
        }
        return i >= j;
    }
public:
    vector<vector<int>> palindromePairs(vector<string> &words) {
        vector<vector<int>> res;
        map<string, int> idx;
        set<int> words_len;
        for (int i = 0; i < size(words); i++) {
            idx[words[i]] = i;
            words_len.insert(size(words[i]));
        }
        for (int i = 0; i < size(words); i++) {
            string rev_word = words[i];
            reverse(rev_word.begin(),rev_word.end());
            if (idx.find(rev_word) != idx.end() and idx[rev_word] != i) {
                res.push_back({idx[rev_word] , i});
            }
            int word_len = size(rev_word);
            auto end_len = words_len.find(word_len);
            for (auto it = words_len.begin(); it != end_len; it++) {
                int j = *it;
                string suff = rev_word.substr(word_len-j);
                string pref = rev_word.substr(0, j);
                if (is_palindrome(rev_word, 0, word_len-j-1) and idx.find(suff) != idx.end()) {
                    res.push_back({i , idx[suff]});
                }
                if (is_palindrome(rev_word, j, word_len-1) and idx.find(pref) != idx.end()) {
                    res.push_back({idx[pref], i});
                }
            }
        }
        return res;
    }
};
```

</details>

