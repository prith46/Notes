# Letter Combinations of a Phone Number

## 🔹 Problem Statement  
Given a string containing digits (`2-9`), return all possible letter combinations that the number could represent, following the traditional **T9 phone keyboard mapping**.

https://leetcode.com/problems/letter-combinations-of-a-phone-number/?envType=problem-list-v2&envId=string

## 🛠 Algorithm Explanation  
1. **Define a mapping** (`L[][]`) of digits to letters, similar to a phone keypad.  
2. Create a helper function `combine(int digit, List<String> s)`:  
   - If `s` is empty, initialize it with letters of `digit`.  
   - Otherwise, append each letter of `digit` to all existing combinations in `s`.  
3. Process digits **from right to left**:  
   - Convert the input `digits` into an integer (`num`).  
   - Extract the **last digit** and call `combine(digit, output)`.  
   - Remove the last digit by performing `num /= 10`.  
4. **Return the final list** of combinations.

![null](https://github.com/user-attachments/assets/c568fc7f-5da3-494f-9352-a1586d44ef62)
