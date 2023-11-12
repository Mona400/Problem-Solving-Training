<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Heap and Bit Manipulation `10 problems`

## find k pairs with smallest sums
Problem Link: https://leetcode.com/problems/find-k-pairs-with-smallest-sums

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
import queue

class Solution:
    def kSmallestPairs(self, nums1: List[int], nums2: List[int], k: int) -> List[List[int]]:
        min_heap = queue.PriorityQueue()
        n, m = len(nums1), len(nums2)
        for i in range(min(n, k)):
            t = nums1[i] + nums2[0]
            n1, n2 = nums1[i], nums2[0]
            min_heap.put((t, n1, n2, 0))
        res = []
        while k and not min_heap.empty():
            t, n1, n2, idx = min_heap.get()
            res.append((n1 ,n2))
            k -= 1
            if idx < m-1:
                t = n1 + nums2[idx+1]
                n1, n2 = n1, nums2[idx+1]
                min_heap.put((t, n1 , n2, idx+1))
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    struct Item {
        int t, n1, n2, idx;
        Item(int t, int n1, int n2, int idx) :
            t(t), n1(n1), n2(n2), idx(idx) {
        }
    };
public:
    vector<vector<int>> kSmallestPairs(vector<int> &nums1, vector<int> &nums2, int k) {
        auto comp = [](const Item &x, const Item &y) { return x.t > y.t; };
        priority_queue<Item, vector<Item>, decltype(comp)> min_heap(comp);
        int n = size(nums1), m = size(nums2);
        for (int i=0; i<min(n, k); i++) {
            int n1 = nums1[i], n2 = nums2[0];
            min_heap.push(Item(n1+n2, n1, n2, 0));
        }
        vector<vector<int>> res;
        while (k and not min_heap.empty()) {
            Item x = min_heap.top();
            res.push_back({x.n1, x.n2});
            min_heap.pop();
            k --;
            if (x.idx < m-1) {
                int n1 = x.n1, n2 = nums2[x.idx+1];
                min_heap.push(Item(n1+n2, n1, n2, x.idx+1));
            }
        }
        return res;
    }
};
```

</details>
<br>

## kth largest element in an array
Problem Link: https://leetcode.com/problems/kth-largest-element-in-an-array

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        def partition(nums, l, r):
            p, f = nums[r], l
            for i in range(l, r):
                if nums[i] <= p:
                    nums[f], nums[i] = nums[i], nums[f]
                    f += 1
            nums[f], nums[r] = nums[r], nums[f]
            return f

        k = len(nums) - k
        l, r = 0, len(nums) - 1
        while l < r:
            p = partition(nums, l, r)
            if p < k:
                l = p+1
            elif p > k:
                r = p-1
            else:
                break
        return nums[k]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    int partition(const vector<int> &nums, int l, int r) {
        int p = nums[r], f = l;
        for (int i=l; i<r; i++) {
            if (nums[i] <= p) {
                swap(nums[f], nums[i]);
                f ++;
            }
        }
        swap(nums[f], nums[r]);
        return f;
    }
public:
    int findKthLargest(vector<int> &nums, int k) {
        k = size(nums) - k;
        int l = 0, r = size(nums)-1;
        while (l < r) {
            int p = partition(nums, l, r);
            if (p < k)
                l = p+1;
            else if (p > k)
                r = p-1;
            else
                break;
        }
        return nums[k];
    }
};
```

</details>
<br>

## find median from data stream
Problem Link: https://leetcode.com/problems/find-median-from-data-stream

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
import queue

class MedianFinder:
    def __init__(self):
        self.max_heap = queue.PriorityQueue()
        self.min_heap = queue.PriorityQueue()
        self.cnt = 0

    def addNum(self, num: int) -> None:
        if self.cnt % 2:
            self.min_heap.put(num)
        else:
            self.max_heap.put(-num)
        self.cnt += 1
        l = -1e9 if not self.max_heap.qsize() else -self.max_heap.queue[0]
        r =  1e9 if not self.min_heap.qsize() else  self.min_heap.queue[0]
        if l > r:
            self.max_heap.get()
            self.max_heap.put(-r)
            self.min_heap.get()
            self.min_heap.put(l)

    def findMedian(self) -> float:
        l = 0 if not self.max_heap.qsize() else -self.max_heap.queue[0]
        r = 0 if not self.min_heap.qsize() else  self.min_heap.queue[0]
        if self.cnt % 2:
            return l
        else:
            return (l+r)/2
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class MedianFinder {
    priority_queue<int> max_heap;
    priority_queue<int, vector<int>, greater<int>> min_heap;
    int cnt;
public:
    MedianFinder() {
        max_heap = priority_queue<int>();
        min_heap = priority_queue<int, vector<int>, greater<int>>();
        cnt = 0;
    }
    void addNum(int num) {
        if (cnt % 2)
            min_heap.push(num);
        else
            max_heap.push(num);
        cnt ++;
        int l = not size(max_heap) ? -1e9 : max_heap.top();
        int r = not size(min_heap) ?  1e9 : min_heap.top();
        if (l > r) {
            max_heap.pop();
            max_heap.push(r);
            min_heap.pop();
            min_heap.push(l);
        }
    }
    double findMedian() {
        int l = not size(max_heap) ? 0 : max_heap.top();
        int r = not size(min_heap) ? 0 : min_heap.top();
        if (cnt % 2)
            return l;
        else
            return 1.0*(l+r)/2;
    }
};
```

</details>
<br>

## single number
Problem Link: https://leetcode.com/problems/single-number

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        cnt_nums = [0] * int(6e4)
        for i in nums:
            cnt_nums[i+int(3e4)] += 1
        for i in nums:
            if cnt_nums[i+int(3e4)] == 1:
                return i
        return 0
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int singleNumber(vector<int> &nums) {
        vector<int> cnt_nums(6e4, 0);
        for (int i:nums)
            cnt_nums[i+int(3e4)] ++;
        for (int i:nums) {
            if (cnt_nums[i+int(3e4)] == 1)
                return i;
        }
        return 0;
    }
};
```

</details>
<br>

## top k frequent elements
Problem Link: https://leetcode.com/problems/top-k-frequent-elements

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
import queue

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        cnt = {}
        for i in nums:
            cnt[i] = cnt.get(i, 0) + 1
        max_heap = queue.PriorityQueue()
        for i, j in cnt.items():
            max_heap.put((-j, i))
        res = [0] * k
        for i in range(k):
            v, j = max_heap.get()
            res[i] = j
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    vector<int> topKFrequent(vector<int> &nums, int k) {
        map<int, int> cnt;
        for (int i : nums)
            cnt[i] ++;
        priority_queue<pair<int, int>> max_heap;
        for (auto &[i, j] : cnt)
            max_heap.push({j, i});
        vector<int> res(k);
        for (int i=0; i<k; i++) {
            auto [v, j] = max_heap.top();
            max_heap.pop();
            res[i] = j;
        }
        return res;
    }
};
```

</details>
<br>

## kth smallest element in a sorted matrix
Problem Link: https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
        def binary_search_upper(arr, x):
            l, r = 0, len(arr)-1
            while l <= r:
                m = (l+r) // 2
                if arr[m] <= x:
                    l = m+1
                else:
                    r = m-1
            return l

        def count_less_k(m):
            res = 0
            for i in range(n):
                res += binary_search_upper(matrix[i], m)
            return res

        l, r, n = matrix[0][0], matrix[-1][-1], len(matrix)
        while l <= r:
            m = (l+r) // 2
            if count_less_k(m) < k:
                l = m+1
            else:
                r = m-1
        return l
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    int n;

    int binary_search_upper(const vector<int> &arr, int x) {
        int l = 0, r = size(arr)-1;
        while (l <= r) {
            int m = (l+r) / 2;
            if (arr[m] <= x)
                l = m+1;
            else
                r = m-1;
        }
        return l;
    }
    int count_less_k(int m, const vector<vector<int>> &matrix) {
        int res = 0;
        for (int i=0; i<n; i++)
            res += binary_search_upper(matrix[i], m);
        return res;
    }
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        n = size(matrix);
        int l = matrix[0][0], r = matrix[n-1][n-1];
        while (l <= r) {
            int m = (l+r) / 2;
            if (count_less_k(m, matrix) < k)
                l = m+1;
            else
                r = m-1;
        }
        return l;
    }
};
```

</details>
<br>

## Interval List Intersections
Problem Link: https://leetcode.com/problems/interval-list-intersections

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def intervalIntersection(self, firstList: List[List[int]], secondList: List[List[int]]) -> List[List[int]]:
        i, j = 0, 0
        n, m = len(firstList), len(secondList)
        res = []
        while i < n and j < m:
            lo = max(firstList[i][0], secondList[j][0])
            hi = min(firstList[i][1], secondList[j][1])
            if lo <= hi:
                res.append((lo, hi))
            if firstList[i][1] > secondList[j][1]:
                j += 1
            else:
                i += 1
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    vector<vector<int>> intervalIntersection(vector<vector<int>> &firstList, vector<vector<int>> &secondList) {
        int i = 0, j = 0;
        int n = size(firstList), m = size(secondList);
        vector<vector<int>> res;
        while (i < n and j < m) {
            int lo = max(firstList[i][0], secondList[j][0]);
            int hi = min(firstList[i][1], secondList[j][1]);
            if (lo <= hi)
                res.push_back({lo, hi});
            if (firstList[i][1] > secondList[j][1])
                j ++;
            else
                i ++;
        }
        return res;
    }
};
```

</details>
<br>

## non overlapping intervals
Problem Link: https://leetcode.com/problems/non-overlapping-intervals

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort()
        res = 0
        prev_end = -int(5e4)
        for s, e in intervals:
            if s >= prev_end:
                prev_end = e
            else:
                res += 1
                prev_end = min(e, prev_end)
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    int eraseOverlapIntervals(vector<vector<int>> &intervals) {
        sort(intervals.begin(), intervals.end());
        int res = 0;
        int prev_end = -int(5e4);
        for (auto &it : intervals) {
            int s = it[0], e = it[1];
            if (s >= prev_end)
                prev_end = e;
            else {
                res ++;
                prev_end = min(e, prev_end);
            }
        }
        return res;
    }
};
```

</details>
<br>

## meeting rooms ii
Problem Link: https://leetcode.com/problems/meeting-rooms-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python

```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp

```

</details>
<br>

## k closest points to origin
Problem Link: https://leetcode.com/problems/k-closest-points-to-origin

<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
import queue

class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        min_heap = queue.PriorityQueue()
        for i in range(len(points)):
            dist = points[i][0] ** 2 + points[i][1] ** 2
            min_heap.put((dist, i))
        res = [0] * k
        for i in range(k):
            dist, j = min_heap.get()
            res[i] = points[j]
        return res
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/heap-bit-manipulation.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    vector<vector<int>> kClosest(vector<vector<int>> &points, int k) {
        auto comp = [](const pair<int, int> &x, const pair<int, int> &y) { return x.first > y.first; };
        priority_queue<pair<int, int>, vector<pair<int, int>>, decltype(comp)> min_heap(comp);
        for (int i=0; i<size(points); i++) {
            int dist = points[i][0] * points[i][0] + points[i][1] * points[i][1];
            min_heap.push({dist, i});
        }
        vector<vector<int>> res(k);
        for (int i=0; i<k; i++) {
            auto [dist, j] = min_heap.top();
            min_heap.pop();
            res[i] = points[j];
        }
        return res;
    }
};
```

</details>
<br>

