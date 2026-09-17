# 21. Merge Two Sorted Lists

- Difficulty: Easy
- Language: C++
- **Topics**: `Linked List`, `Recursion`
- Link: https://leetcode.com/problems/merge-two-sorted-lists/

## Problem Statement

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

**Example 1:**
> **Input:** `ist1 = [1,2,4]`, `list2 = [1,3,4]`  
> **Output:** `[1,1,2,3,4,4]`  

## Approach 

Maintain a head and a tail pointer on the merged linked list.

Then choose the head of the merged linked list by comparing the first node of both linked lists.

For all subsequent nodes in both lists, you choose the smaller current node and link it to the tail of the merged list, and moving the current pointer of that list one step forward.

You keep doing this while there are some remaining elements in both the lists.

If there are still some elements in only one of the lists, you link this remaining list to the tail of the merged list.

Initially, the merged linked list is NULL.

Compare the value of the first two nodes and make the node with the smaller value the head node of the merged linked list.

Since it’s the first and only node in the merged list, it will also be the tail.

Then move head1 one step forward.

# (image need add)

## Complexity Analysis

- Time complexity: O(n+m)
- Space complexity: O(n+m) this is auxiliary stack space due to recursion.
  
## Solution

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if(l1 == NULL){
            return l2;
        }
        if(l2 == NULL){
            return l1;
        }
        if(l1 -> val <= l2 -> val){
            l1 -> next = mergeTwoLists(l1 -> next, l2);
            return l1;
        }
        else{
            l2 -> next = mergeTwoLists(l1 , l2 -> next);
            return l2;
        }
    }
};
```
