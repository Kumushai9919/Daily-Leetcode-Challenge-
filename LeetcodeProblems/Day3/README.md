# Day 3 

## 128. Longest Consecutive Sequence

###### Medium  | <a href="https://leetcode.com/problems/longest-consecutive-sequence/description/">leetcode link </a> | Array Hash Table String Union Find Sorting



#### 1. Introduction:

Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.

##### Example 1:
````
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
````

#### 2. Approach:
The problem is to find the longest consecutive elements sequence in an array. To solve this problem, we can use a HashSet to efficiently check for the presence of elements and find consecutive sequences.This approach allows us to find the longest consecutive sequence in linear time complexity O(n), where n is the number of elements in the input array. The approach can be summarized as follows:
1. Create a HashSet to store unique elements from the input array.
2. Iterate through the array and add each element to the HashSet.
3. Iterate through the array again and for each element, check if it is the starting element of a potential consecutive sequence.
4. If it is, find the length of the consecutive sequence by incrementing the element and counting the consecutive elements present in the HashSet.
5. Update the length of the longest consecutive sequence found so far.
6. Return the length of the longest consecutive sequence.

   ![IMG_9644FA102D8C-1](https://github.com/Kumushai9919/Daily-Leetcode-Challenge-/assets/83897840/a2714bab-a04c-411f-b46e-ef915bd607e0)


#### 3. Explanation:

Explanation:

1. Initialize a HashSet to store unique elements from the input array.
2. Initialize a variable to keep track of the longest consecutive sequence length, initially set to 1.
3. Iterate through the array and add each element to the HashSet.
4. Iterate through the array again and for each element:
  a. Check if the element minus one (num - 1) is not present in the HashSet.
  b. If not present, it means the current element is the starting element of a potential consecutive sequence.
  c. Initialize a count variable to 1 to track the length of the current consecutive sequence.
  d. Use a while loop to increment the element and count as long as the element plus one (num + 1) is present in the HashSet.
  e. Update the longest consecutive sequence length if the current count is greater.
5. Return the length of the longest consecutive sequence.
   
The solution utilizes the HashSet data structure to efficiently check for the presence of elements in O(1) time complexity. By traversing the array twice,
we can find the longest consecutive sequence of numbers in linear time complexity O(n), where n is the number of elements in the input array.
 
#### Solution in Java:
````
class Solution {
    public int longestConsecutive(int[] nums) {
        if(nums.length == 0) return 0;
        
       HashSet<Integer> set = new HashSet<>();
        int ans = 1;

       for(int num: nums) set.add(num);
       for(int num: nums){
           if(!set.contains(num - 1)){
               int count = 1;
               while(set.contains(num+1)){
                   num++;
                   count++;
               }
                ans = Math.max(count, ans);
           }
          
       }
        return ans;
    }
}
 
````
