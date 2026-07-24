# 20. Valid Parentheses

- Difficulty: Easy
- Language: C++
- Link: https://leetcode.com/problems/valid-parentheses/

## Problem Statement

Given a string `s` containing characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

## Approach

Use a stack to track open brackets:
1. Iterate through the string character by character.
2. If the character is an opening bracket `(`, `{`, `[`, push it onto the stack.
3. If it is a closing bracket, check whether the stack is empty. If empty, return false. Otherwise, pop the top character and check if it matches the current closing bracket.
4. After traversing the string, return true if the stack is empty; otherwise, return false.

## Complexity

- Time Complexity: O(N), where N is the length of the string. Each character is pushed and popped at most once.
- Space Complexity: O(N), for storing characters in the stack in the worst case.

## Solution

```cpp
#include <string>
#include <stack>
using namespace std;

class Solution {
public:
    bool isValid(string s) {
        stack<char> stack;
        for(char ch: s){
            if(ch == '(' || ch == '[' || ch == '{'){
                stack.push(ch);
            }else {
                if (stack.empty()){
                    return false;
                }
                char top = stack.top();
                stack.pop();
                if(ch == ')' && top != '('){
                    return false;
                }
                 if(ch == ']' && top != '['){
                    return false;
                }
                 if(ch == '}' && top != '{'){
                    return false;
                }
            }
        }
        return stack.empty();
    }
};
```

