# 125. Valid Palindrome

## Approach 

# image id needed 

## Complexity Analysis

- Time complexity: O(n)
- Space complexity: O(n)
  
## Solution

```cpp
class Solution {
public:
    bool isPalindrome(string s) {
       string filtered;
       for(char ch : s) {
            if(isalnum(ch)) {
                filtered += tolower(ch);
            }
       }
       int start = 0;
       int last = filtered.size() - 1;

       while(start < last) {
            if(filtered[start] != filtered[last]) {
                return false;
        }
            start ++;
            last --;
       }
       return true;
    }
};
```
