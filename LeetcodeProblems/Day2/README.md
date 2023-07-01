# Day 2 

## 347. Top K Frequent Elements
###### Medium  | <a href="[https://leetcode.com/problems/group-anagrams/description/](https://leetcode.com/problems/top-k-frequent-elements/description/)">leetcode link </a> | Array Hash Table String Bucket Sort Counting



#### 1. Introduction:

Given an integer array ```nums``` and an integer ```k```, return the ```k``` most frequent elements. You may return the answer in **any order.**

##### Example 1:
````
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
````

#### 2. Approach:
The problem is to find the **k** most frequent elements in an array. To solve this problem, we can use the bucket list approach. The idea is to count the frequencies of numbers in the given array using a HashMap. Then, we create a bucket list, which is an array of lists, to group numbers based on their requences. Finally, we extract the top K frequent elements from the bucket list. We start by counting the frequency of each number using a HashMap. The map will store each number as the **key** and its frequency as the **value**. 

![IMG_515EA76FC87C-1](https://github.com/Kumushai9919/Daily-Leetcode-Challenge-/assets/83897840/c7c56a02-60e7-4a01-94bf-cf94fbb98fe6)


#### 3. Explanation:

1. Counting frequencies:
- create a **countMap** to count the frequency of each number in the **nums** array.
   
2. Creating the Bucket List:
- create a **buckets** array with a length of **nums.length+1**.
- iterate over the map, for each number, retrieve its frequency from the map and add the number to the appropriate bucket in the buckets array
 
   
3. Extracting the Top K Frequent Elements:
- After populating the buckets array, we iterate over it in reverse order, starting from the highest frequency. This ensures that we process the most frequent numbers first.
- Within each non-empty bucket, iterate over the numbers and add them to the result array. Keep track of the number of elements added to the result array using the index variable.
- If we have added K elements to the result array, we break out of the loop and return the result array.

The overall time complexity of the solution is **O(n+m)**, where **n** is the length of the inout array and **m** is the number of unique elements.
The space complexity is O(n) since we use Hashmap to store the frequency counts for each element and also we need space for bucket list resulting in O(n) space, so space complexity is also **O(n)**.

 
#### Solution in Java:
````
class Solution {
    public int[] topKFrequent(int[] nums, int k) { 

        // Count the frequency of each number
        Map<Integer, Integer> map = new HashMap<>(); 
        for(int num: nums){
            map.put(num, map.getOrDefault(num, 0)+ 1);
        }

         // Create a bucket list to group numbers based on their frequency
        List<Integer>[] buckets = new List[nums.length+1];
        for(int num: map.keySet()){
            int freq = map.get(num);

            if(buckets[freq] == null){
                buckets[freq] = new ArrayList<>(); 
            }

            buckets[freq].add(num);
        }

        // Extract the top K frequent elements from the bucket list
        int[] res = new int[k];
        int index = 0;

        for(int i=buckets.length-1; i>0 && index < k; i--){
            if(buckets[i] != null){
                for(int num: buckets[i]){
                    res[index++] = num;
                   
                    if(index == k){
                        break;
                    }
                }
            }
        }

        return res;
        
    }
}
````
