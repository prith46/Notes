# Finding the Duplicate Number Using Bit Manipulation

## **Problem Description**
Given an array `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, find the duplicate number.

https://leetcode.com/problems/find-the-duplicate-number/description/?envType=problem-list-v2&envId=two-pointers

### **Constraints**
- You must solve the problem **without modifying** the array `nums`.
- You must use **only constant extra space**.

## **Step-by-Step Algorithm**

1. **Find the maximum bit position required** to represent `n`:
   - Since `n` can be large, find the **highest bit set** in `n` (i.e., the leftmost `1` in its binary form).
   - This ensures that we only process necessary bits.

2. **Iterate over each bit position** from `0` to `maxBit`:
   - **Count the number of `1`s** in `nums` at this bit position (`numsCount`).
   - **Count the number of `1`s** in the numbers from `1` to `n` at this bit position (`rangeCount`).
   - If `numsCount > rangeCount`, that bit belongs to the duplicate.

3. **Reconstruct the duplicate number** using the bits identified.
   - Start with `duplicate = 0`.
   - For each bit where `numsCount > rangeCount`, set that bit in `duplicate`.
   - The final value of `duplicate` is the repeated number.


## Dry Run

## Example: `[1, 2, 3, 2, 4]`

- `n = 4`, so valid numbers are `[1, 2, 3, 4]`.
- **Binary Representation**:

```
1 -> 001  
2 -> 010  
3 -> 011  
4 -> 100  
```

Given `nums = [1, 2, 3, 2, 4]`, we will compare the bit counts.

### **Bit Position 0 (LSB)**

| Number in `nums` | Binary | Bit 0 |
| --- | --- | --- |
| **1** | 001 | 1 |
| **2** | 010 | 0 |
| **3** | 011 | 1 |
| **2** | 010 | 0 |
| **4** | 100 | 0 |
| **Total in `numsCount`** | **2** |  |

| Number in `[1, n]` | Binary | Bit 0 |
| --- | --- | --- |
| **1** | 001 | 1 |
| **2** | 010 | 0 |
| **3** | 011 | 1 |
| **4** | 100 | 0 |
| **Total in `rangeCount`** | **2** |  |

Since `numsCount == rangeCount`, **this bit does not belong to the duplicate number**.

---

### **Bit Position 1**

| Number in `nums` | Binary | Bit 1 |
| --- | --- | --- |
| **1** | 001 | 0 |
| **2** | 010 | 1 |
| **3** | 011 | 1 |
| **2** | 010 | 1 |
| **4** | 100 | 0 |
| **Total in `numsCount`** | **3** |  |

| Number in `[1, n]` | Binary | Bit 1 |
| --- | --- | --- |
| **1** | 001 | 0 |
| **2** | 010 | 1 |
| **3** | 011 | 1 |
| **4** | 100 | 0 |
| **Total in `rangeCount`** | **2** |  |

Since `numsCount > rangeCount`, **this bit is set in the duplicate number**.

---

### **Bit Position 2**

| Number in `nums` | Binary | Bit 2 |
| --- | --- | --- |
| **1** | 001 | 0 |
| **2** | 010 | 0 |
| **3** | 011 | 0 |
| **2** | 010 | 0 |
| **4** | 100 | 1 |
| **Total in `numsCount`** | **1** |  |

| Number in `[1, n]` | Binary | Bit 2 |
| --- | --- | --- |
| **1** | 001 | 0 |
| **2** | 010 | 0 |
| **3** | 011 | 0 |
| **4** | 100 | 1 |
| **Total in `rangeCount`** | **1** |  |

Since `numsCount == rangeCount`, **this bit does not belong to the duplicate number**.

---

## **Final Duplicate Number**

- **Bits collected:** `010` (binary)
- **Decimal value:** `2`
- ✅ **Duplicate = `2`**

