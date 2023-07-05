# Day 5
## 15. 3Sum




###### Medium  | <a href="https://leetcode.com/problems/3sum/description/">leetcode link </a> |Two pointer Array Sorting



#### 1. Introduction:

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.

##### Example 1:
````
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.

````

#### 2. Approach:
The approach to solve the 3Sum problem involves sorting the array and then using a two-pointer technique to find unique triplets whose sum is zero. By skipping duplicates and adjusting the pointers based on the sum, we can efficiently find all possible combinations.

#### 3. Explanation:

1. Sort the input array: Sorting the array allows us to identify duplicate elements easily and helps in applying the two-pointer technique.
2. Initialize an empty result list: This list will store all the unique triplets whose sum is zero.
3. Iterate through the array: Consider each element as a potential candidate for the first element of the triplet.
4. Skip duplicates: To avoid duplicate triplets, skip elements that are the same as the previous one. This ensures that only unique triplets are considered.
5. Use two pointers: Initialize two pointers, left and right, to find the remaining two elements of the triplet. The left pointer starts from i + 1, and the right pointer starts from the end of the array.
6. Find triplets using the two-pointer technique: Use a while loop to adjust the pointers based on the sum of the current triplet. If the sum is zero, add the triplet to the result list.
    If the sum is less than zero, increment the left pointer to increase the sum.
    If the sum is greater than zero, decrement the right pointer to decrease the sum.
7. Skip duplicates within the while loop: To avoid duplicate triplets, skip elements that are the same as the previous ones. This ensures that only unique triplets are considered.

8. Move the pointers: After processing a triplet, increment the left pointer and decrement the right pointer to continue finding more triplets.

9. Return the result list: After iterating through the entire array, return the result list containing all the unique triplets.

By following this approach, we can find all the triplets whose sum is zero efficiently. The time complexity of this solution is O(n^2), where n is the length of the input array. Sorting the array takes O(nlogn) time, and finding triplets using the two-pointer technique takes O(n) time. Overall, the solution runs in O(n^2) time, satisfying the problem's constraints.



### Java Solution:
````
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
         List<List<Integer>> result = new ArrayList<>();
        
        if (nums.length < 3) {
            return result;
        }
        
        Arrays.sort(nums);
        
        for (int i = 0; i < nums.length - 2; i++) {
            // Skip duplicates
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            }
            
            int left = i + 1;
            int right = nums.length - 1;
            
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                
                if (sum == 0) {
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    
                    // Skip duplicates
                    while (left < right && nums[left] == nums[left + 1]) {
                        left++;
                    }
                    
                    while (left < right && nums[right] == nums[right - 1]) {
                        right--;
                    }
                    
                    left++;
                    right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }
        
        return result;
        
    }
}
````
