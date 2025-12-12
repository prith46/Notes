### 1. Search Insert Position

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
Link - https://leetcode.com/problems/search-insert-position/description/?envType=study-plan-v2&envId=binary-search

#### Algorithm:
- Do binary search, if the index is found, then return the index
- If not, then return the value of left (which will be the place where the number can be inserted).
