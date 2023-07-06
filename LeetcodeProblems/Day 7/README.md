# Day 7
## 11. Container With Most Water





###### Medium  | <a href="https://leetcode.com/problems/container-with-most-water/description/">leetcode link </a> |Two pointer Array Sorting



#### 1. Introduction:

The problem is to find the maximum amount of water that can be contained in a container formed by vertical lines. The height array represents the height of the lines, and the distance between any two lines is equal to their index difference. The goal is to find two lines that, along with the x-axis, form a container that can hold the maximum amount of water.
##### Example 1:
<img width="594" alt="Screenshot 2023-07-06 at 9 49 29 PM" src="https://github.com/Kumushai9919/Daily-Leetcode-Challenge-/assets/83897840/0486f1a6-2e66-4353-b7f5-e4862a568c5f">

````
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
````

#### 2. Approach:
The approach to solve the Container With Most Water problem is to use the two-pointer technique. We initialize two pointers, left and right, representing the leftmost and rightmost lines of the container. We calculate the area of the container by multiplying the distance between the lines (container length) with the minimum height of the two lines. We update the maximum area found so far and then move the pointers inward.

#### 3. Explanation:

1. Initialize the pointers and the maximum area: We set the left pointer to 0, representing the leftmost line, and the right pointer to height.length - 1, representing the rightmost line. We initialize the maximum area, res, to 0.

2. Calculate the area and update the maximum area: In each iteration, we calculate the area of the container using the formula containerLength * Math.min(height[left], height[right]), where containerLength is the distance between the lines and Math.min(height[left], height[right]) represents the minimum height of the two lines. We update the maximum area, res, by taking the maximum of the current area and the previous maximum.

3. Move the pointers inward: We compare the heights of the two lines pointed by the left and right pointers. If the height of the left line is smaller, we move the left pointer one step to the right. Otherwise, if the height of the right line is smaller or equal, we move the right pointer one step to the left. This step ensures that we explore all possible container combinations.

4. Repeat until the pointers meet: We continue the above steps until the left and right pointers meet. At this point, we have explored all possible container combinations, and the maximum area is stored in res.

5. Return the maximum area: After the loop ends, we return the maximum area, res, as the result.

By following this approach, we can find the maximum amount of water that can be contained in the given array of heights. The two-pointer technique allows us to efficiently explore all possible container combinations in a single pass, resulting in a time complexity of O(n), where n is the length of the input array.

### Java Solution:
````
class Solution {
    public int maxArea(int[] height) {

        int left = 0;
        int right = height.length - 1;
        int res = 0;
        while (left < right) {
            int containerLength = right - left;
            int area = containerLength * Math.min(height[left], height[right]);
            res = Math.max(res, area);
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }
        return res;
        
    }
}
````
