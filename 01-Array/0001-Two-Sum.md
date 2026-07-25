# 1. Two Sum

- Difficulty: Easy
- Language: C++
- **Topics**: `Hash table`, `Array`
- Link: https://leetcode.com/problems/two-sum/

## Problem Statement

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

**Example 1:**
> **Input:** `nums = [2,7,11,15]`, `target = 9`  
> **Output:** `[0,1]`  
> **Explanation:** Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

## Approach 1: Brute Force

<img width="800" height="663" alt="image" src="https://github.com/user-attachments/assets/59e67f37-98a7-4dab-a25e-fad377d1adfc" />


## Complexity Analysis

- Time complexity: O(n²). For each element, we try to find its complement by looping through the rest of the array which takes O(n) time. Therefore, the time complexity is o(n²)
- Space complexity: O(1). The space required does not depend on the size of the input array, so only constant space is used.
  
## Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target){
        for(int i = 0; i < nums.size(); i++){
            for(int j = i+1; j < nums.size(); j++){
                if(nums[j] == target - nums[i]){
                    return{i,j};
                }
            }
        }
        return {};
    }
};
```
## Approach 2: Two-pass Hash Table

<img width="800" height="576" alt="image" src="https://github.com/user-attachments/assets/393aa3e7-be5d-45bc-a2f7-6efacad1d964" />

## Complexity Analysis

- Time complexity: O(n).We traverse the list containing n elements exactly twice. Since the hash table reduces the lookup time to O(1), the overall time complexity is O(n).
- Space complexity: O(n).The extra space required depends on the number of items stored in the hash table, which stores exactly n elements.
  
## Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target){
        unordered_map<int,int>hashmp;
        for(int i = 0; i<nums.size();i++){
            hashmp[nums[i]] = i;
        }
        for(int i = 0; i < nums.size(); i++){
            int com = target - nums[i];
            if(hashmp.find(com) != hashmp.end() && hashmp[com] != i){
                return{i, hashmp[com]};
            }
        }
        return {};
    }
};
```
## Approach 3: One-pass Hash Table

<img width="800" height="1022" alt="image" src="https://github.com/user-attachments/assets/a2b7a223-3ba9-4e27-83d2-3711f89a4966" />

## Complexity Analysis

- Time complexity: O(n).We traverse the list containing n elements only once. Each lookup in the table costs only O(1) time.
The solution is faster than Approach 2:Two-pass Hash Table
- Space complexity: O(n).The extra space required depends on the number of items stored in the hash table, which stores at most n elements.
  
## Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int>hash;
        for(int i = 0 ;i < nums.size() ;i++){
            int complement = target - nums[i];
            if(hash.find(complement) != hash.end()){
                return {hash[complement] ,i};
            }
            hash[nums[i]] = i;
        }
        return {};
    }
};
```
