# Day 9
## 3. Longest Substring Without Repeating Characters





###### Medium  | <a href="https://leetcode.com/problems/longest-substring-without-repeating-characters/description/">leetcode link </a> | Sliding window String



#### 1. Introduction:

The problem is to find the length of the longest substring without repeating characters in a given string. 
In other words, we need to find the maximum length of a substring in which all characters are unique.

##### Example 1:
````
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

````

#### 2. Approach:
1. Initialize an empty list substringL to represent the current substring without repeating characters.
2. Initialize a variable largestlength to keep track of the length of the longest substring encountered so far.
3. Iterate through each character in the input string s using a for loop:
    Check if the current character is already present in substringL by using the contains method.
    If the current character is found to be repeating, perform the following steps:
    Get the index of the repeating character in substringL using the indexOf method.
    Remove the repeating character from substringL using the remove method.
    If the index of the repeating character is greater than 0, remove all characters before that index in substringL using the subList method to ensure that only the substring starting from the next character is considered.
    Add the current character to substringL using the add method.
    Update largestlength with the maximum length between largestlength and the size of substringL using the Math.max method.
4. Return largestlength as the result.

#### 3. Explanation:

This solution maintains a sliding window represented by the substringL list to keep track of the current substring without repeating characters. It iterates through each character in the input string s and checks if the current character is repeating by using the contains method. If a repeating character is found, the solution removes it from substringL and updates the starting point of the substring to the next character. The solution updates largestlength with the maximum length between largestlength and the size of substringL to track the longest length encountered so far. Finally, the solution returns largestlength as the result.

The time complexity of this solution is O(n), where n is the length of the input string s, as each character in s is visited once. The space complexity is also O(n) in the worst case, as substringL can contain all unique characters of s

### Java Solution:
````
class Solution {
    public int lengthOfLongestSubstring(String s) {

        List<Character> substringL = new ArrayList<>();
            int largestlength = 0;
            for(int right = 0; right < s.length(); right++) {
                if(substringL.contains(s.charAt(right))) { 
                    // get the index of the char
                    int index = substringL.indexOf(s.charAt(right));
                    substringL.remove(index);
                    if(index > 0)
                        substringL.subList(0, index).clear();
                }
                substringL.add(s.charAt(right));
                largestlength = Math.max(largestlength, substringL.size());
            }
            return largestlength;
 
    }
}
````
