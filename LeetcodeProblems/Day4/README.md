# Day 4
## 238. Product of Array Except Self

###### Medium  | <a href="https://leetcode.com/problems/product-of-array-except-self/description/">leetcode link </a> | Array Prefix



#### 1. Introduction:

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

##### Example 1:
````
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
````

#### 2. Approach:
To solve this problem, we can use the concept of prefix and suffix products. 
The idea is to calculate the product of all elements to the left of each element and the product of all elements to the right of each element. 
Then, we can multiply these two products to get the desired result.

    
#### 3. Explanation:

Explanation:

1. Initialize two arrays: leftProduct and answer of size n, where n is the length of the input array nums.
2. Calculate the product of all elements to the left of each element and store them in the leftProduct array.
    - Initialize leftProduct[0] as 1 since there are no elements to the left of the first element.
    - For each element at index i (starting from 1), calculate leftProduct[i] by multiplying leftProduct[i - 1] with nums[i - 1].
3. Initialize a variable rightProduct as 1 to keep track of the product of all elements to the right of the current element.
4. Traverse the input array nums in reverse order from the last element to the first element.
    - Calculate the value of answer[i] by multiplying leftProduct[i] with rightProduct.
    - Update rightProduct by multiplying it with nums[i].
5. After the traversal, the answer array will contain the product of all elements except the current element.
6. Return the answer array.

By using the prefix product (leftProduct) and the suffix product (rightProduct), we avoid using division and achieve the required O(n) time complexity.

#### Solution in Java:
````
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] leftProduct = new int[n];
        int[] answer = new int[n];
        
        // Calculate the product of all elements to the left of each element
        leftProduct[0] = 1;
        for (int i = 1; i < n; i++) {
            leftProduct[i] = leftProduct[i - 1] * nums[i - 1];
        }
        
        // Calculate the product of all elements to the right of each element and multiply with leftProduct
        int rightProduct = 1;
        for (int i = n - 1; i >= 0; i--) {
            answer[i] = leftProduct[i] * rightProduct;
            rightProduct *= nums[i];
        }
        
        return answer;
    }
}

 
````

