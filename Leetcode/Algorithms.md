## **2260\. Minimum Consecutive Cards to Pick Up**

You are given an integer array cards where cards\[i\] represents the **value** of the ith card. A pair of cards are **matching** if the cards have the **same** value.

Return _the_ _**minimum**_ _number of_ _**consecutive**_ _cards you have to pick up to have a pair of_ _**matching**_ _cards among the picked cards._ If it is impossible to have matching cards, return -1.

**Example 1:**
Input: cards = [3,4,2,3,4,7]  
Output: 4  
Explanation: We can pick up the cards [3,4,2,3] which contain a matching pair of cards with value 3. 
Note that picking up the cards [4,2,3,4] is also optimal.   

**Example 2:**

Input: cards = [1,0,5,3]  
Output: -1  
Explanation: There is no way to pick up a set of consecutive cards that contain a pair of matching cards   

https://leetcode.com/problems/minimum-consecutive-cards-to-pick-up/

![image](https://github.com/user-attachments/assets/6ef3e88d-bdcb-4fd1-a95d-2eb48e39a40c)

## To find the cycle
![Untitled-2025-05-16-1833](https://github.com/user-attachments/assets/49fc4d8e-ce7e-4ed3-aa56-35984c3e755b)

---
## **73\. Set Matrix Zeroes**

Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.
You must do it in place

Link - https://leetcode.com/problems/set-matrix-zeroes/

**Constraints:**

*   m == matrix.length
*   n == matrix\[0\].length 
*   1 <= m, n <= 200    
*   \-231 <= matrix\[i\]\[j\] <= 231 - 1    
*   Could you devise a constant space solution?

![Untitled-2025-05-16-1833](https://github.com/user-attachments/assets/e3b55603-0d1b-4e62-aedf-76200ff72cd5)

---
## **Letter Combinations of a Phone Number**

Link - https://leetcode.com/problems/letter-combinations-of-a-phone-number/

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.
A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Input: digits = "23"  Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"] 
Input: digits = ""  Output: []   
Input: digits = "2"  Output: ["a","b","c"]  

![image](https://github.com/user-attachments/assets/e2e03722-4342-4bf9-a00a-d0c345361119)

---

## **Subsets**

Link - https://leetcode.com/problems/subsets/

Given an integer array nums of **unique** elements, return _all possible subsets(the power set)_.
The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

Input: nums = [1,2,3]  Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]  
Input: nums = [0]  Output: [[],[0]]   

![image](https://github.com/user-attachments/assets/29a3b80e-cc05-4011-8dcf-2430a39b0a08)
---

## **90\. Subsets II**

Link - https://leetcode.com/problems/subsets-ii/

Given an integer array nums that may contain duplicates, return _all possible_ _subsets (the power set)_.
The solution set **must not** contain duplicate subsets. Return the solution in **any order**.
Input: nums = [1,2,2]  Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]  
Input: nums = [0]  Output: [[],[0]]  

![image](https://github.com/user-attachments/assets/1209dce4-49cc-48bd-bc7e-7b668eea980d)

---

## **2131\. Longest Palindrome by Concatenating Two Letter Words**
Link - https://leetcode.com/problems/longest-palindrome-by-concatenating-two-letter-words/

You are given an array of strings words. Each element of words consists of **two** lowercase English letters.
Create the **longest possible palindrome** by selecting some elements from words and concatenating them in **any order**. Each element can be selected **at most once**.
Return _the_ _**length**_ _of the longest palindrome that you can create_. If it is impossible to create any palindrome, return 0.

Input: words = ["lc","cl","gg"]  Output: 6  

![image](https://github.com/user-attachments/assets/ee674c6e-eefe-464e-9d44-bb47400362bc)

---

## 80\. Remove Duplicates from Sorted Array II
Link - https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/

Given an integer array nums sorted in **non-decreasing order**, remove some duplicates in-place such that each unique element appears **at most twice**. The **relative order** of the elements should be kept the **same**.
-- Input: nums = \[1,1,1,2,2,3\]
-- Output: 5, nums = \[1,1,2,2,3,\_\]

![image](https://github.com/user-attachments/assets/7629c204-c2b5-464c-a37d-196ea27814f9)

---

## 75\. Sort Colors
Link - https://leetcode.com/problems/sort-colors/

Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

Input: nums = [2,0,2,1,1,0]  Output: [0,0,1,1,2,2]   
Input: nums = [2,0,1]  Output: [0,1,2]   

![image](https://github.com/user-attachments/assets/60910880-589c-485f-a54d-d8a2736545d0)

 ---

 ## 40\. Combination Sum II
Link - https://leetcode.com/problems/combination-sum-ii/

Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.
Each number in candidates may only be used **once** in the combination.
**Note:** The solution set must not contain duplicate combinations.

Input: candidates = [10,1,2,7,6,1,5], target = 8  
Output:   [  [1,1,6],  [1,2,5],  [1,7],  [2,6]  ]  

![image](https://github.com/user-attachments/assets/e5a36d72-2b66-4138-a920-eb236be6ae0f)

---

## 160\. Intersection of Two Linked Lists
Link - https://leetcode.com/problems/intersection-of-two-linked-lists/

Given the heads of two singly linked-lists headA and headB, return _the node at which the two lists intersect_. If the two linked lists have no intersection at all, return null.

![image](https://github.com/user-attachments/assets/26e1eb87-20d3-46c3-8ff3-e6adc089cc6f)
![image](https://github.com/user-attachments/assets/6e1ce7b3-f4b8-48d0-af84-5099695311a9)

---
