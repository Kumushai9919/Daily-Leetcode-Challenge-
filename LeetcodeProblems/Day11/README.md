# Day 11
## 153. Find Minimum in Rotated Sorted Array

 
###### Medium  | <a href="https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/">leetcode link </a> | Binary search Array


#### 1. Introduction:

The problem is to find the minimum element in a sorted rotated array. The array is initially sorted in ascending order and then rotated between 1 and n times.
##### Example 1:
````
Input: nums = [3,4,5,1,2]
Output: 1
Explanation: The original array was [1,2,3,4,5] rotated 3 times.

````

#### 2. Approach:
To solve this problem in O(log n) time, we can use a modified binary search algorithm. We initialize two pointers, l and r, pointing to the start and end of the array, respectively. We compare the element at the middle index (mid) with the elements at the start (l) and end (r) indices to determine the rotation point.

#### 3. Explanation:

1. Initialize two pointers, l and r, pointing to the start and end of the array, respectively.
2. Perform a binary search until l is less than or equal to r:
  Check if the element at index l is less than or equal to the element at index r. If true, it means the array is not rotated, so the minimum element is at l. Return nums[l].
  Calculate the middle index mid as the average of l and r.
  Compare the element at index mid with the element at index l:
    If nums[mid] is greater than or equal to nums[l], it means the minimum element is to the right of mid. Set l to mid + 1.
    Otherwise, if nums[mid] is less than nums[l], it means the minimum element is to the left of mid or at mid itself. Set r to mid.
3. Return 0 (default) if no minimum element is found (this should not occur in the given problem constraints).

The time complexity of this solution is O(log n) because we perform binary search to find the minimum element.
The space complexity is O(1) as we only use a constant amount of extra space for variables.




### Java Solution:
````
   class Solution {
    public int findMin(int[] nums) {

        int l = 0;
        int r = nums.length - 1;

        while (l <= r) {
            if (nums[l] <= nums[r]) {
                return nums[l];
            }

            int mid = (l + r) / 2;
            if (nums[mid] >= nums[l]) {
                l = mid + 1;
            } else {
                r = mid;
            }
        }
        return 0;
        
    }
}
````
