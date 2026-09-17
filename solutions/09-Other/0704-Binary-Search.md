# 704. Binary Search

## Approach 

<img width="800" height="663" alt="image" src="" />


## Complexity Analysis

- Time complexity: O(log n). 
- Space complexity: O(log n). 
  
## Solution

```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left = 0;
        int right = nums.size() - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (target == nums[mid]) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }
};
```
