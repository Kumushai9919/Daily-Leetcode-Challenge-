# Day 13
## 20. Valid Parentheses

 

###### Easy  | <a href="https://leetcode.com/problems/valid-parentheses/description/">leetcode link </a> | Stack String  



#### 1. Introduction:

The problem is to determine if a given string containing different types of brackets is valid. A valid string should satisfy the following conditions:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

##### Example 1:
````
Input: s = "()"
Output: true

````

#### 2. Approach:
The given problem can be solved using a stack data structure. We iterate through the characters of the string and perform the following steps:
- if the current character is an opening bracket ```'(', '{', or '['```, we push it onto the stack
- if the current character is a closing ```')', '}', or ']'```, we we check if the stack is empty or if the top of the stack does not correspond to the same type of opening bracket. If either condition is true, the string is not valid and we return false.
- if the current character is a closing bracket and the top of the stack corresponds to the same type of opening bracket, we pop the top of the stack as the brackets are matched
- After iterating through all characters, we check if the stack is empty. If it is empty, all brackets are properly matched, and the string is valid. Otherwise, the string is not valid.
- 
#### 3. Explanation:

1. Check if the length of the string is odd. If it is, return false as a valid string must have an even number of characters.
2. Initialize an empty stack to store the opening brackets.
3. Iterate through each character in the string:
    If the current character is an opening bracket ('(', '{', or '['), push it onto the stack.
    If the current character is a closing bracket (')', '}', or ']'), check if the stack is empty or if the top of the stack does not match the current closing bracket. If either condition is true, return false as the string is not valid.
    If the current character is a closing bracket and the top of the stack matches the current closing bracket, pop the top of the stack as the brackets are matched.
4. After iterating through all characters, check if the stack is empty. If it is, return true as the string is valid. Otherwise, return false.

The time complexity of this solution is O(n), where n is the length of the input string.
The space complexity is O(n) as the worst-case scenario occurs when all characters are opening brackets and are stored in the stack.


### Java Solution:
````
   class Solution {
    public boolean isValid(String s) {
        if (s.length() % 2 != 0) return false;
        Stack<Character> stack = new Stack<>();
        for (int i = 0; i < s.length(); i++) {
            if (
                stack.isEmpty() &&
                (s.charAt(i) == ')' || s.charAt(i) == '}' || s.charAt(i) == ']')
            ) return false; else {
                if (!stack.isEmpty()) {
                    if (
                        stack.peek() == '(' && s.charAt(i) == ')'
                    ) stack.pop(); else if (
                        stack.peek() == '{' && s.charAt(i) == '}'
                    ) stack.pop(); else if (
                        stack.peek() == '[' && s.charAt(i) == ']'
                    ) stack.pop(); else stack.add(s.charAt(i));
                } else stack.add(s.charAt(i));
            }
        }
        return stack.isEmpty();
        
    }
}
````
