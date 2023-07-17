# Day 15
## 21. Merge Two Sorted Lists


 

###### Easy  | <a href="https://leetcode.com/problems/merge-two-sorted-lists/description/">leetcode link </a> | Linked List Recursion



#### 1. Introduction:

The problem is to merge two sorted linked lists into a single sorted linked list. We are given the heads of both linked lists, and we need to merge them in a way that the resulting list is also sorted.
##### Example 1:
 <img width="659" alt="Screenshot 2023-07-17 at 6 57 46 PM" src="https://github.com/Kumushai9919/Daily-Leetcode-Challenge-/assets/83897840/4804a42e-7d43-4753-b3db-801fa918b676">

````
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]

````

#### 2. Approach:
To merge two sorted linked lists, we will use the iterative approach. We will create a new dummy node as the root of the merged list. Then, we will iterate through both lists and compare the values of the nodes. We will attach the node with the smaller value to the merged list and move the corresponding pointer forward. We will repeat this process until we have processed all the nodes from both lists.
#### 3. Explanation:

1. Create a new dummy node root as the root of the merged list.
2. Initialize a pointer prev to keep track of the previous node in the merged list.
3. While both list1 and list2 are not null:
  Compare the values of the current nodes of list1 and list2.
  If the value of the current node in list1 is smaller, attach it to the prev.next and move the list1 pointer forward.
  Otherwise, attach the current node in list2 to the prev.next and move the list2 pointer forward.
  Move the prev pointer to the newly attached node.
4. After the loop, if there are remaining nodes in either list1 or list2, attach them to the prev.next.
5. Return root.next as it will be pointing to the head of the merged sorted linked list.
#### 4. Complexity Analysis:
The time complexity of this solution is O(n), where n is the total number of nodes in both lists. We traverse both lists once.
The space complexity is O(1) as we are using a constant amount of extra space to store the root, prev, and other temporary variables.
### Java Solution:
````
 /**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        final ListNode root = new ListNode();
        ListNode prev = root;
        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                prev.next = list1;
                list1 = list1.next;
            } else {
                prev.next = list2;
                list2 = list2.next;
            }
            prev = prev.next;
        }
        prev.next = list1 != null ? list1 : list2;
        return root.next;
        
    }
}
````
