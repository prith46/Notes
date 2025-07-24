# Array Rotation Notes (Reversal Algorithm)

## 🔄 Left Rotation by `d` (Reversal Algorithm)

1. Reverse the first `d` elements.  
2. Reverse the remaining `d to n` elements.  
3. Reverse the entire array.

➡️ **Time Complexity:** `O(n)`  
➡️ **Space Complexity:** `O(1)`  

---

## 🔁 Right Rotation by `d` (Reversal Algorithm)

1. Reverse the entire array.  
2. Reverse the first `d` elements.  
3. Reverse the remaining `d to n` elements.

➡️ **Time Complexity:** `O(n)`  
➡️ **Space Complexity:** `O(1)`

# Time and Space Complexity for Recursion

**Time Complexity - O(Number of function calls × Time complexity per function call)**

**Space Complexity - O(Maximum depth of recursion tree/stack × Space complexity per function call)**

## Sum of all subarrays 
  → ( index + 1) \* ( array\_length - index ) \* A\[index\]

