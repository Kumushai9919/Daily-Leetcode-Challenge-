# Day 9
## 424. Longest Repeating Character Replacement

 

###### Medium  | <a href="https://leetcode.com/problems/longest-repeating-character-replacement/description/">leetcode link </a> | Sliding window String HashTable



#### 1. Introduction:

The problem is to find the length of the longest substring in a given string s where you can change at most k characters to any other uppercase English character. The goal is to maximize the length of the substring with the same repeating letters.


##### Example 1:
````
Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.

````

#### 2. Approach:
To solve this problem, we can use a sliding window approach. We maintain a window that expands and contracts as we iterate through the string. The window represents the substring we are considering, and we adjust it based on the number of characters we can change (k).

#### 3. Explanation:

1. Initialize an array arr of size 26 to keep track of the count of each letter in the current window.
2. Initialize variables ans, max, and i to keep track of the maximum length of the substring, the maximum count of any letter in the current window, and the starting index of the window, respectively.
3. Iterate through the string using a pointer j:
  Increment the count of the letter s.charAt(j) in the arr array.
  Update max to the maximum value between max and the count of the current letter.
  If the length of the window (j - i + 1) minus max is greater than k, it means we need to shrink the window from the left side:
    Decrement the count of the letter s.charAt(i) in the arr array.
    Increment i to move the window's starting index.
  Update ans to the maximum value between ans and the current window's length (j - i + 1).
4. Return ans, which represents the length of the longest substring with the same repeating letters that can be achieved by changing at most k characters.

The time complexity of this solution is O(n), where n is the length of the input string s.
The space complexity is O(1) since we use a fixed-size array arr of size 26 to keep track of the counts.

### Java Solution:
````
   class Solution {
    public int characterReplacement(String s, int k) {
        int[] arr = new int[26];
        int ans = 0;
        int max = 0;
        int i = 0;
        for (int j = 0; j < s.length(); j++) {
            arr[s.charAt(j) - 'A']++;
            max = Math.max(max, arr[s.charAt(j) - 'A']);
            if (j - i + 1 - max > k) {
                arr[s.charAt(i) - 'A']--;
                i++;
            }
            ans = Math.max(ans, j - i + 1);
        }
        return ans;
        
    }
}
````
