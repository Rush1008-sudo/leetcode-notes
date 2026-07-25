# 125. Valid Palindrome

- Difficulty: Easy
- Language: C++
- **Topics**: `Two Pointers`, `String`
- Link: https://leetcode.com/problems/valid-palindrome/

## Problem Statement

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

**Example 1:**
> **Input:** `s = "A man, a plan, a canal: Panama"`  
> **Output:** `true`  
> **Explanation:** `"amanaplanacanalpanama" is a palindrome.`.

**Example 2:**
> **Input:** `s = " "`  
> **Output:** `true`  
> **Explanation:** `"s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.`.

## Approach 

# image need add

## Complexity Analysis

- Time complexity: O(n)
- Space complexity: O(n)
  
## Solution

```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        string filtered;
        for(char ch : s){
            if(isalnum(ch)){
                filtered += tolower(ch);
            }
        }
        int start = 0;
        int last = filtered.size() - 1;

        while (start < last){
            if(filtered[start] != filtered[last]){
                return false;
            }
            start ++;
            last --;
        }
        return true;
    }
};
```
