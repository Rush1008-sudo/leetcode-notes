# 121. Best Time to Buy and Sell Stock


## Approach  

#image is needed 

## Complexity Analysis

- Time complexity: O(n)
- Space complexity: O(1)
  
## Solution

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int profit = 0;
        int buyPrice = prices[0];
        for(int i = 0; i < prices.size(); i++){
            if(buyPrice > prices[i]){
                buyPrice = prices[i];
            }
            profit = max(profit ,prices[i] - buyPrice);
        }
    return profit;
    }
};
```
