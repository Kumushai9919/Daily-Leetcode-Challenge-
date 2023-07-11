# Day 12
## 153. Find Minimum in Rotated Sorted Array

 
###### Medium  | <a href="https://leetcode.com/problems/search-in-rotated-sorted-array/description/">leetcode link </a> | Binary search Array


#### 1. Introduction:

There is an integer array nums sorted in ascending order (with distinct values).

Prior to being passed to your function, nums is possibly rotated at an unknown pivot index k (1 <= k < nums.length) such that the resulting array is [nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]] (0-indexed). For example, [0,1,2,4,5,6,7] might be rotated at pivot index 3 and become [4,5,6,7,0,1,2].

Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums.

##### Example 1:
````
Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4

````

#### 2. Approach:
The Binary search approach is based on the fact that a rotated sorted array can be divided into two sorted arrays.


#### 3. Explanation:

1. The approach starts with finding the mid element and compares it with the target element.
2. If they are equal, it returns the mid index. If the left half of the array is sorted, then it checks if the target lies between the start and the mid, and updates the end pointer accordingly.
3. Otherwise, it checks if the target lies between mid and end, and updates the start pointer accordingly.
4. If the right half of the array is sorted, then it checks if the target lies between mid and end, and updates the start pointer accordingly.
5. Otherwise, it checks if the target lies between start and mid, and updates the end pointer accordingly.
6. This process continues until the target element is found, or the start pointer becomes greater than the end pointer, in which case it returns -1.
7. This approach has a time complexity of O(log n).

Time Complexity:

The time complexity of the Brute force approach is O(n), where n is the size of the input array.
The time complexity of the Binary search approach is O(log n), where n is the size of the input array.

Space Complexity:
The space complexity of both approaches is O(1) as we are not using any extra space to store any intermediate results.

### Java Solution:
````
  class Solution {
    public int search(int[] nums, int target) {
            int left = 0;
            int right = nums.length-1;
            int mid;
            while(left<=right){
                mid = left+(right-left)/2;
                
                if(nums[mid] == target) return mid;
                // condition for left side is sort
                if(nums[left]<=nums[mid]){
                    if(target>=nums[left] && target <=nums[mid]){
                        right = mid-1;
                    }else {
                        left = mid+1;
                    }
                }
                else{
                    if(target>=nums[mid] && target <=nums[right]){
                        left = mid+1;
                    }else{
                        right = mid-1;
                    }
                }
        }
         return -1;   
        
    }
}
````
