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
