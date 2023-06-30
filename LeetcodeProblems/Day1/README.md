# Day1  
## 49. Group Anagrams 
###### Medium  | <a href="https://leetcode.com/problems/group-anagrams/description/">leetcode link </a> | Array Hash Table String Sorting


Given an array of strings ```strs```, group the anagrams together. You can return the answer in any order.
An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

#### Example 1:
````
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
````



### Java solution 
#### 1. Logic:
The logic is to group words that are anagrams together in the **strs** array and return it. We can use HashMap to efficient our solution, but first we need to sort each string in the array and to find the angarams, so with that anagrams key we can map HashMap. 

#### 2. Explanation:






