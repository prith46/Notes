### 1. Search Insert Position

Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
Link - https://leetcode.com/problems/search-insert-position/description/?envType=study-plan-v2&envId=binary-search

#### Algorithm:
- Do binary search, if the index is found, then return the index
- If not, then return the value of left (which will be the place where the number can be inserted).
---

### Count Negative Numbers in a Sorted Matrix

Given a m x n matrix grid which is sorted in non-increasing order both row-wise and column-wise, return the number of negative numbers in grid.
Link - https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/description/?envType=study-plan-v2&envId=binary-search

Input: grid = [[4,3,2,-1],[3,2,1,-1],[1,1,-1,-2],[-1,-1,-2,-3]]
Output: 8
Explanation: There are 8 negatives number in the matrix.

#### Algorithm:
- keep i at 0 and j at the end of the first array.
- Since it is column wise sorted, the negative numbers will also be sorted in the order.
- so keeo reducing j for every loop and count the number of negative numbers in the array.

```
public int countNegatives(int[][] A) {
        int i=0, j=A[0].length-1, count = 0;

        for (; i<A.length; i++) {
            while (j>=0 && A[i][j] < 0)
                j--;

            count += A[i].length - j - 1;
        }

        return count;
    }
```
---

