<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="80" src="/logos/leetcode.png"></img></a>

# LeetCode OJ - Interviews Questions 1 <br> Linked List `15 problems`

## reverse linked list
Problem Link: https://leetcode.com/problems/reverse-linked-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if head == None:
            return head
        prv = None
        cur = head
        nxt = cur.next
        while nxt:
            cur.next = prv
            prv = cur
            cur = nxt
            nxt = nxt.next
        cur.next = prv
        return cur
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* reverseList(ListNode *head) {
        if (head == NULL)
            return head;
        ListNode *prv = NULL;
        ListNode *cur = head;
        ListNode *nxt = cur->next;
        while (nxt) {
            cur->next = prv;
            prv = cur;
            cur = nxt;
            nxt = nxt->next;
        }
        cur->next = prv;
        return cur;
    }
};
```

</details>
<br>

## swap nodes in pairs
Problem Link: https://leetcode.com/problems/swap-nodes-in-pairs

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        res = ListNode(0, head)
        prev, curr = res, head
        while curr and curr.next:
            temp1 = curr.next.next
            temp2 = curr.next
            temp2.next = curr
            curr.next = temp1
            prev.next = temp2
            prev = curr
            curr = temp1
        return res.next
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* swapPairs(ListNode *head) {
        ListNode *res = new ListNode(0, head);
        ListNode *prev = res, *curr = head;
        while (curr and curr->next) {
            ListNode *temp1 = curr->next->next;
            ListNode *temp2 = curr->next;
            temp2->next = curr;
            curr->next = temp1;
            prev->next = temp2;
            prev = curr;
            curr = temp1;
        }
        return res->next;
    }
};
```

</details>
<br>

## linked list cycle ii
Problem Link: https://leetcode.com/problems/linked-list-cycle-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head:
            return
        curr1 = head
        curr2 = head
        while curr2 and curr2.next:
            curr2 = curr2.next.next
            curr1 = curr1.next
            if curr1 == curr2:
                break
        if not curr2 or not curr2.next:
            return
        curr2 = head
        while curr1 and curr2:
            if curr1 == curr2:
                return curr1
            curr1 = curr1.next
            curr2 = curr2.next
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* detectCycle(ListNode *head) {
        if (not head)
            return NULL;
        ListNode *curr1 = head;
        ListNode *curr2 = head;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
            if (curr1 == curr2)
                break;
        }
        if (not curr2 or not curr2->next)
            return NULL;
        curr2 = head;
        while (curr1 and curr2) {
            if (curr1 == curr2)
                return curr1;
            curr1 = curr1->next;
            curr2 = curr2->next;
        }
        return NULL;
    }
};
```

</details>
<br>

## sort list
Problem Link: https://leetcode.com/problems/sort-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        def beforeMiddleNode(head):
            curr1 = head
            curr2 = head.next
            while curr2 and curr2.next:
                curr2 = curr2.next.next
                curr1 = curr1.next
            return curr1

        def mergeTwoLists(list1, list2):
            head = ListNode()
            curr = head
            while list1 and list2:
                if list1.val <= list2.val:
                    curr.next = list1
                    list1 = list1.next
                else:
                    curr.next = list2
                    list2 = list2.next
                curr = curr.next
            if list1:
                curr.next = list1
            if list2:
                curr.next = list2
            return head.next

        def merge_sort(head):
            if not head or not head.next:
                return head
            left = head
            right = beforeMiddleNode(head)
            temp = right.next
            right.next = None
            right = temp
            left  = merge_sort(left)
            right = merge_sort(right)
            return mergeTwoLists(left, right)

        return merge_sort(head)
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    ListNode* beforeMiddleNode(ListNode *head) {
        ListNode *curr1 = head;
        ListNode *curr2 = head->next;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
        }
        return curr1;
    }
    ListNode* mergeTwoLists(ListNode *list1, ListNode *list2) {
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (list1 and list2) {
            if (list1->val <= list2->val)
                curr->next = list1,
                list1 = list1->next;
            else
                curr->next = list2,
                list2 = list2->next;
            curr = curr->next;
        }
        if (list1)
            curr->next = list1;
        if (list2)
            curr->next = list2;
        return head->next;
    }
    ListNode* merge_sort(ListNode *head) {
            if (not head or not head->next)
                return head;
            ListNode *left  = head;
            ListNode *right = beforeMiddleNode(head);
            ListNode *temp  = right->next;
            right->next = NULL;
            right = temp;
            left  = merge_sort(left);
            right = merge_sort(right);
            return mergeTwoLists(left, right);
    }
public:
    ListNode* sortList(ListNode *head) {
        return merge_sort(head);
    }
};
```

</details>
<br>

## merge k sorted lists
Problem Link: https://leetcode.com/problems/merge-k-sorted-lists

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        def mergeTwoLists(list1, list2):
            head = ListNode()
            curr = head
            while list1 and list2:
                if list1.val <= list2.val:
                    curr.next = list1
                    list1 = list1.next
                else:
                    curr.next = list2
                    list2 = list2.next
                curr = curr.next
            if list1:
                curr.next = list1
            if list2:
                curr.next = list2
            return head.next

        if len(lists) == 0:
            return None
        for i in range(1, len(lists)):
            lists[0] = mergeTwoLists(lists[0], lists[i])
        return lists[0]
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    ListNode* mergeTwoLists(ListNode *list1, ListNode *list2) {
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (list1 and list2) {
            if (list1->val <= list2->val)
                curr->next = list1,
                list1 = list1->next;
            else
                curr->next = list2,
                list2 = list2->next;
            curr = curr->next;
        }
        if (list1)
            curr->next = list1;
        if (list2)
            curr->next = list2;
        return head->next;
    }
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if (size(lists) == 0)
            return NULL;
        for (int i=1; i<size(lists); i++)
            lists[0] = mergeTwoLists(lists[0], lists[i]);
        return lists[0];
    }
};
```

</details>
<br>

## linked list cycle
Problem Link: https://leetcode.com/problems/linked-list-cycle

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        curr1 = head
        curr2 = head
        while curr2 and curr2.next:
            curr2 = curr2.next.next
            curr1 = curr1.next
            if curr1 == curr2:
                return True
        return False
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode *curr1 = head;
        ListNode *curr2 = head;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
            if (curr1 == curr2)
                return true;
        }
        return false;
    }
};
```

</details>
<br>

## merge two sorted lists
Problem Link: https://leetcode.com/problems/merge-two-sorted-lists

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        head = ListNode()
        curr = head
        while list1 and list2:
            if list1.val <= list2.val:
                curr.next = list1
                list1 = list1.next
            else:
                curr.next = list2
                list2 = list2.next
            curr = curr.next
        if list1:
            curr.next = list1
        if list2:
            curr.next = list2
        return head.next
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode *list1, ListNode *list2) {
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (list1 and list2) {
            if (list1->val <= list2->val)
                curr->next = list1,
                list1 = list1->next;
            else
                curr->next = list2,
                list2 = list2->next;
            curr = curr->next;
        }
        if (list1)
            curr->next = list1;
        if (list2)
            curr->next = list2;
        return head->next;
    }
};
```

</details>
<br>

## reverse linked list ii
Problem Link: https://leetcode.com/problems/reverse-linked-list-ii

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        res = ListNode(0, head)
        prev_left, cur = res, head
        for i in range(left-1):
            prev_left = cur
            cur = cur.next
        prv = None
        for i in range(right-left+1):
            temp = cur.next
            cur.next = prv
            prv = cur
            cur = temp
        prev_left.next.next = cur
        prev_left.next = prv
        return res.next
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* reverseBetween(ListNode *head, int left, int right) {
        ListNode *res = new ListNode(0, head);
        ListNode *prev_left = res, *cur = head;
        for (int i=0; i<left-1; i++) {
            prev_left = cur;
            cur = cur->next;
        }
        ListNode *prv = NULL;
        for (int i=0; i<right-left+1; i++) {
            ListNode *temp = cur->next;
            cur->next = prv;
            prv = cur;
            cur = temp;
        }
        prev_left->next->next = cur;
        prev_left->next = prv;
        return res->next;
    }
};
```

</details>
<br>

## remove nth node from end of list
Problem Link: https://leetcode.com/problems/remove-nth-node-from-end-of-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        res = ListNode(0, head)
        curr1 = res
        curr2 = head
        while n:
            curr2 = curr2.next
            n -= 1
        while curr2:
            curr1 = curr1.next
            curr2 = curr2.next
        curr1.next = curr1.next.next
        return res.next
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode *head, int n) {
        ListNode *res = new ListNode(0, head);
        ListNode *curr1 = res;
        ListNode *curr2 = head;
        while (n) {
            curr2 = curr2->next;
            n --;
        }
        while (curr2) {
            curr1 = curr1->next;
            curr2 = curr2->next;
        }
        curr1->next = curr1->next->next;
        return res->next;
    }
};
```

</details>
<br>

## rotate list
Problem Link: https://leetcode.com/problems/rotate-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        def get_length(curr):
            res = 0
            while curr:
                curr = curr.next
                res += 1
            return res

        if not head or not head.next:
            return head
        k %= get_length(head)
        if k == 0:
            return head
        res = ListNode(0, head)
        curr1 = res
        curr2 = head
        while k:
            curr2 = curr2.next
            k -= 1
        while curr2.next:
            curr1 = curr1.next
            curr2 = curr2.next
        curr1 = curr1.next
        new_head = curr1.next
        curr1.next = None
        curr2.next = head
        res.next = new_head
        return res.next
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    int get_length(ListNode *curr) {
        int res = 0;
        while (curr) {
            curr = curr->next;
            res ++;
        }
        return res;
    }
public:
    ListNode* rotateRight(ListNode *head, int k) {
        if (not head or not head->next)
            return head;
        k %= get_length(head);
        if (k == 0)
            return head;
        ListNode *res = new ListNode(0, head);
        ListNode *curr1 = res;
        ListNode *curr2 = head;
        while (k) {
            curr2 = curr2->next;
            k --;
        }
        while (curr2->next) {
            curr1 = curr1->next;
            curr2 = curr2->next;
        }
        curr1 = curr1->next;
        ListNode *new_head = curr1->next;
        curr1->next = NULL;
        curr2->next = head;
        res->next = new_head;
        return res->next;
    }
};
```

</details>
<br>

## middle of the linked list
Problem Link: https://leetcode.com/problems/middle-of-the-linked-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        curr1 = head
        curr2 = head
        while curr2 and curr2.next:
            curr2 = curr2.next.next
            curr1 = curr1.next
        return curr1
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* middleNode(ListNode *head) {
        ListNode *curr1 = head;
        ListNode *curr2 = head;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
        }
        return curr1;
    }
};
```

</details>
<br>

## remove linked list elements
Problem Link: https://leetcode.com/problems/remove-linked-list-elements

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        curr = head
        while curr and curr.next:
            if curr.next.val == val:
                temp = curr.next
                curr.next = curr.next.next
                del temp
            else:
                curr = curr.next
        if head and head.val == val:
            temp = head
            head = head.next
            del temp
        return head
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* removeElements(ListNode *head, int val) {
        ListNode *curr = head;
        while (curr and curr->next) {
            if (curr->next->val == val) {
                ListNode *temp = curr->next;
                curr->next = curr->next->next;
                delete temp;
            }
            else
                curr = curr->next;
        }
        if (head and head->val == val) {
            ListNode *temp = head;
            head = head->next;
            delete temp;
        }
        return head;
    }
};
```

</details>
<br>

## remove duplicates from sorted list
Problem Link: https://leetcode.com/problems/remove-duplicates-from-sorted-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        curr = head
        while curr and curr.next:
            if curr.val == curr.next.val:
                temp = curr.next
                curr.next = curr.next.next
                del temp
            else:
                curr = curr.next
        return head
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* deleteDuplicates(ListNode *head) {
        ListNode *curr = head;
        while (curr and curr->next) {
            if (curr->val == curr->next->val) {
                ListNode *temp = curr->next;
                curr->next = curr->next->next;
                delete temp;
            }
            else
                curr = curr->next;
        }
        return head;
    }
};
```

</details>
<br>

## reorder list
Problem Link: https://leetcode.com/problems/reorder-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def reorderList(self, head: Optional[ListNode]) -> None:
        def beforeMiddleNode(head):
            curr1 = head
            curr2 = None
            if head.next:
                curr2 = head.next.next
            while curr2 and curr2.next:
                curr2 = curr2.next.next
                curr1 = curr1.next
            return curr1

        def reverseList(head):
            if head == None:
                return head
            prv = None
            cur = head
            nxt = cur.next
            while nxt:
                cur.next = prv
                prv = cur
                cur = nxt
                nxt = nxt.next
            cur.next = prv
            return cur

        def mergeTwoLists(list1, list2):
            head = ListNode()
            curr = head
            while list1 and list2:
                curr.next = list1
                list1 = list1.next
                curr = curr.next
                curr.next = list2
                list2 = list2.next
                curr = curr.next
            return head.next

        mid = beforeMiddleNode(head)
        temp = mid.next
        mid.next = None
        mid = temp
        mid = reverseList(mid)
        head = mergeTwoLists(head, mid)
        return head
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
    ListNode* beforeMiddleNode(ListNode *head) {
        ListNode *curr1 = head;
        ListNode *curr2 = NULL;
        if (head->next)
            curr2 = head->next->next;
        while (curr2 and curr2->next) {
            curr2 = curr2->next->next;
            curr1 = curr1->next;
        }
        return curr1;
    }
    ListNode* reverseList(ListNode *head) {
        if (head == NULL)
            return head;
        ListNode *prv = NULL;
        ListNode *cur = head;
        ListNode *nxt = cur->next;
        while (nxt) {
            cur->next = prv;
            prv = cur;
            cur = nxt;
            nxt = nxt->next;
        }
        cur->next = prv;
        return cur;
    }
    ListNode* mergeTwoLists(ListNode *list1, ListNode *list2) {
        ListNode *head = new ListNode();
        ListNode *curr = head;
        while (list1 and list2) {
            curr->next = list1,
            list1 = list1->next;
            curr = curr->next;
            curr->next = list2,
            list2 = list2->next;
            curr = curr->next;
        }
        return head->next;
    }
public:
    void reorderList(ListNode *head) {
        ListNode *mid = beforeMiddleNode(head);
        ListNode *temp = mid->next;
        mid->next = NULL;
        mid = temp;
        mid = reverseList(mid);
        head = mergeTwoLists(head, mid);
    }
};
```

</details>
<br>

## odd even linked list
Problem Link: https://leetcode.com/problems/odd-even-linked-list

<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
class Solution:
    def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head:
            return head
        odd  = head
        even = head.next
        original_even = even
        while even and even.next:
            odd.next = even.next
            odd = odd.next
            even.next = odd.next
            even = even.next
        odd.next = original_even
        return head
```

</details>
<br>
<a href="/level-2/leetcode/interviews-questions-1/solutions/linked-list.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
class Solution {
public:
    ListNode* oddEvenList(ListNode *head) {
        if (not head)
            return head;
        ListNode *odd  = head;
        ListNode *even = head->next;
        ListNode *original_even = even;
        while (even and even->next) {
            odd->next = even->next;
            odd = odd->next;
            even->next = odd->next;
            even = even->next;
        }
        odd->next = original_even;
        return head;
    }
};
```

</details>
<br>
