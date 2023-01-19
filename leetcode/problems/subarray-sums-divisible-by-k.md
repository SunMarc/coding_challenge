---
date: 2023=01-19
title: 974. Subarray Sums Divisible by K
difficulty:
    - medium
runtime: 93.99 # faster than (in %)
memory usage: 87.93    # less than (in %)
---
## Description
Given an integer array `nums` and an integer `k`, return *the number of non-empty **subarrays** that have a sum divisible by* `k`.

A **subarray** is a **contiguous** part of an array.

**Example 1:**

```
Input: nums = [4,5,0,-2,-3,1], k = 5
Output: 7
Explanation: There are 7 subarrays with a sum divisible by k = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]

```

**Example 2:**

```
Input: nums = [5], k = 9
Output: 0

```

**Constraints:**

- `1 <= nums.length <= 3 * 104`
- `104 <= nums[i] <= 104`
- `2 <= k <= 104`

## Approach 1: Prefix Sum with Hashmap
Time complexity: `O(n)`    |    Space complexity: `O(k)`
where `n` is the length of the input array and `k` is the given divisor.

``` python
class Solution:
    def subarraysDivByK(self, nums: List[int], k: int) -> int:
        mod = defaultdict(int)
        mod[0]=1
        res = 0
        val = 0
        for num in nums:
            val  = (val + num) % k
            res += mod[val]
            mod[val]+=1
        return res
```
