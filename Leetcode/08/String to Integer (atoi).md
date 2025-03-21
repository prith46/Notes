# String to Integer (atoi) - Algorithm

## Overview  
This function converts a string (`s`) into a **32-bit signed integer** (`int`). It follows specific rules to handle whitespace, signs (`+/-`), digits, and overflow.

https://leetcode.com/problems/string-to-integer-atoi/description/

---

## Algorithm  

### 1. Skip Leading Whitespaces  
- Start from the first character and move forward while it is a space (`' '`).
- Stop when a non-space character is found.

### 2. Check for a Sign (`+` or `-`)  
- If the next character is `'-'`, set `isNegative = true`.  
- If it is `'+'`, keep `isNegative = false`.  
- Move to the next character.

### 3. Extract Digits and Build the Number  
- Read characters one by one **as long as they are digits (`0-9`)**.
- Convert the character to an integer (`'0'` → `0`, `'1'` → `1`, ..., `'9'` → `9`).
- Add the digit to the number:  
  ```java
  num = num * 10 + digit;

![null](https://github.com/user-attachments/assets/837e9631-6633-4d79-a85c-3a92c85967f6)


![null (1)](https://github.com/user-attachments/assets/d5d95c25-2833-4608-aef3-b692bd9b720b)
