# Day 14
## 206. Reverse Linked List


 

###### Easy  | <a href="https://leetcode.com/problems/reverse-linked-list/description/">leetcode link </a> | Linked List Recursion



#### 1. Introduction:

The problem is to reverse a singly linked list. We are given the head of the linked list, and we need to reverse the order of the nodes and return the new head of the reversed list.

##### Example 1:
<img width="556" alt="Screenshot 2023-07-16 at 11 21 18 PM" src="https://github.com/Kumushai9919/Daily-Leetcode-Challenge-/assets/83897840/a31370d1-1bb8-4e7b-8007-fa32ee37f5af">

````
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]

````

#### 2. Approach:
To reverse the linked list, we will use the iterative approach. We will traverse the linked list using three pointers: current, previous, and nextCurrent. At each step, we will reverse the next pointer of the current node to point to the previous node, and then update the previous and current pointers accordingly to move forward in the list.

#### 3. Explanation:

1. Initialize three pointers current, previous, and nextCurrent to keep track of the current node, the previous node, and the next node of the current node, respectively.
2. Start iterating through the linked list from the head.
3. At each step, store the next node of the current node in the nextCurrent pointer to avoid losing the reference to the remaining linked list.
4. Reverse the next pointer of the current node to point to the previous node.
5. Move the previous pointer to the current node, and the current pointer to the nextCurrent node.
6. Repeat steps 3 to 5 until the end of the linked list is reached (current becomes null).
7. Return the previous pointer as it will be pointing to the new head of the reversed list.

#### 4. Complexity Analysis:
The time complexity of this solution is O(n), where n is the number of nodes in the linked list, as we need to traverse the entire linked list once.
The space complexity is O(1) as we are using a constant amount of extra space to store the three pointers.

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
    public ListNode reverseList(ListNode head) {
        ListNode current = head;
        ListNode previous = null;
        ListNode nextCurrent = null;
    
        while (current != null) {
            nextCurrent = current.next;
            current.next = previous;
            previous = current;
            current = nextCurrent;
        }

        return previous;
        
        
    }
}
````
