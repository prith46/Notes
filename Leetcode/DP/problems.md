## Min Cost Climbing Stairs

You are given an integer array `cost` where `cost[i]` is the cost of the `i`-th step on a staircase.  
Once you pay the cost, you can either climb **one** or **two** steps.

You may start from the step with **index 0** or **index 1**.

Return **the minimum cost to reach the top of the floor**.

---

### Example

Input: cost = [10,15,20]
Output: 15
Explanation: You will start at index 1.
Pay 15 and climb two steps to reach the top.
The total cost is 15.

Link - https://leetcode.com/problems/min-cost-climbing-stairs/description/?envType=study-plan-v2&envId=dynamic-programming

---

Recursive approach:
1. Just like steps problem we need to find the end value (n-1) and (n-2) steps.
2. use DP to save the values.
3. Just like steps problem remove the dp and use 2 variables for O(1) space.

<img width="945" height="540" alt="image" src="https://github.com/user-attachments/assets/6f1fa4bb-4bc2-4f0b-8c32-c7dd168af64b" />
<img width="943" height="841" alt="image" src="https://github.com/user-attachments/assets/0a1fdc5c-787d-420e-9b19-6d750b71d1d8" />
<img width="946" height="404" alt="image" src="https://github.com/user-attachments/assets/fc11bde8-b4d5-4438-989e-ed275ff8234f" />

---

### 740. Delete and Earn
You are given an integer array nums. You want to maximize the number of points you get by performing the following operation any number of times:

Pick any nums[i] and delete it to earn nums[i] points. Afterwards, you must delete every element equal to nums[i] - 1 and every element equal to nums[i] + 1.
Return the maximum number of points you can earn by applying the above operation some number of times.

Input: nums = [3,4,2]
Output: 6
Explanation: You can perform the following operations:
- Delete 4 to earn 4 points. Consequently, 3 is also deleted. nums = [2].
- Delete 2 to earn 2 points. nums = [].
You earn a total of 6 points.

## Algorithm:

1. Sort the array in non-decreasing order.
2. Define a function `f(index)` that returns the maximum points obtainable starting from `index`.
3. If `index` is outside the array bounds, return `0`.
4. Compute the **take** option:
   - Let `value = nums[index]`.
   - Sum all duplicates of `value` and move the pointer past them.
   - Skip all numbers equal to `value + 1` and move the pointer past them.
   - Add the sum to the result of calling `f(next_safe_index)`.
5. Compute the **skip** option:
   - Move to `index + 1` and call `f(index + 1)`.
6. Return `max(take, skip)`.
7. Store and reuse results for each `index` to avoid recalculation (memoization).

Code:

```
class Solution {
    public int deleteAndEarn(int[] nums) {
        int[] dp = new int[nums.length];
        Arrays.fill(dp, -1);
        Arrays.sort(nums);
        return knapsack(nums, 0, dp);
    }

    public int knapsack(int[] A, int index, int[] dp) {
        if (index >= A.length)
            return 0;

        if (dp[index] != -1)
            return dp[index];

        int select = A[index];
        int skip = index+1;

        // skip till the values are same
        while (skip < A.length && A[skip] == A[index]) {
            skip++;
            select += A[index];
        }
        
        // skip all the values greater than the selected value, ignoring the value less than the selected value
        while (skip < A.length && A[skip] == A[index]+1)
            skip++;

        select += knapsack(A, skip, dp);
        int reject = knapsack(A, index+1, dp);

        dp[index] = Math.max(select, reject);
        return dp[index];        
    }
}
```
