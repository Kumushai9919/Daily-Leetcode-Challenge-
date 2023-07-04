# Day 5
## 125. Valid Palindrome




###### Easy  | <a href="https://leetcode.com/problems/valid-palindrome/description/">leetcode link </a> |Two pointer String



#### 1. Introduction:

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

##### Example 1:
````
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

````

#### 2. Approach:
The given solution uses a two-pointer approach to determine whether a string is a palindrome. The approach involves comparing characters at the start and end of the string and moving the pointers inward until they meet or cross each other.

1. Initialize two pointers, i and j, pointing to the start and end of the string, respectively.
2. While i is less than j, perform the following steps:
    Get the characters at indices i and j in the string.
    Check if start is not a letter or digit. If true, increment i and continue to the next iteration.
    Check if end is not a letter or digit. If true, decrement j and continue to the next iteration.
    Convert both start and end to lowercase and compare them. If they are not equal, return false.
    Increment i and decrement j.
3. If the loop completes without finding any unequal characters, return true as the string is a palindrome.

#### 3. Explanation:

The solution checks whether a given string is a palindrome or not. It uses a two-pointer approach, starting from the two ends of the string and moving inward. This approach ensures that non-alphanumeric characters are ignored and only alphanumeric characters are compared.

The solution iterates through the string until the two pointers meet or cross each other. At each step, it compares the characters at the current positions, ignoring non-alphanumeric characters. If the characters are not equal, it immediately returns false. Otherwise, it continues to the next pair of characters by incrementing i and decrementing j.

By using this approach, the solution can efficiently determine whether the string is a palindrome without using extra space or manipulating the input string. The time complexity of this approach is O(n), where n is the length of the input string, as it only requires a single pass through the string.

In summary, the solution provides an effective and concise approach to determine whether a string is a palindrome, satisfying the requirements of the problem statement.




### Java Solution:
````
public boolean isPalindrome(String s) {
        
    int i = 0;
    int j = s.length() - 1;
    while (i < j) {
        
        Character start = s.charAt(i);
        Character end = s.charAt(j);
        
        if (!Character.isLetterOrDigit(start)) {
            i++;
            continue;
        }
        
        if (!Character.isLetterOrDigit(end)) {
            j--;
            continue;
        }
        
        if (Character.toLowerCase(start) != Character.toLowerCase(end)) {
            return false;
        }
        
        i++;
        j--;    
    }
    
    return true;
}
````
