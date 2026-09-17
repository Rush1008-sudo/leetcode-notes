# 20. Valid Parentheses


## Approach

1. Traverse the string character by character.
2. If it is an opening bracket ((, [, {), push it onto the stack.
3. If it is a closing bracket (), ], }):
4. Check if the stack is empty → if yes, return False.
5. Otherwise, pop from the stack and ensure the popped element matches the type of closing bracket.
6. If not matching, return False.
7. At the end, if the stack is empty, return True; otherwise, False.

<img width="800" height="983" alt="image" src="https://github.com/user-attachments/assets/35204829-7100-4b47-a306-bbb2e3058d52" />

## Complexity

- Time Complexity: O(N),we traverse the string once.
- Space Complexity: O(N), in the worst case, all characters are opening brackets stored in the stack.

## Solution

```cpp
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

