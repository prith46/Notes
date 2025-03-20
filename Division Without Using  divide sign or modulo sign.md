# Division Without Using `/` or `%`

## **Approach**
This algorithm divides two integers **without using** the division (`/`) or modulus (`%`) operators. Instead, it uses **bitwise left shifts (`<<`)** to optimize the process.

### **Step 1: Handle Edge Case**
- If `dividend` is **Integer.MIN_VALUE** (`-2³¹`) and `divisor` is `-1`, return `Integer.MAX_VALUE` to prevent overflow.

### **Step 2: Initialize Variables**
- `result = 0` → **Stores the final quotient.**
- Determine the **sign** of the result:
  - If both numbers have the **same sign**, the result is **positive**.
  - If they have **different signs**, the result is **negative**.
- Convert `dividend` and `divisor` to their **absolute values**.

### **Step 3: Perform Division Using Bitwise Shifting**
1. **Loop while `dividend` is greater than or equal to `divisor`:**
   - Find the **largest multiple** of `divisor` that fits in `dividend`:
     - Start with `count = 0`.
     - Keep **doubling `divisor` (using bit shifts) until it no longer fits** inside `dividend`.
     - Each time `divisor` is doubled, increase `count`.
   - **Update the `result`** by adding `2^count` (`1 << count`).
   - **Reduce `dividend`** by subtracting the largest found multiple (`divisor << count`).

### **Step 4: Apply the Correct Sign**
- If the original numbers had **different signs**, return `-result`.
- Otherwise, return `result`.

## **Complexity Analysis**
- **Time Complexity:** `O(log N)`, since we reduce the `dividend` exponentially.
- **Space Complexity:** `O(1)`, as we use only a few integer variables.

![null (1)](https://github.com/user-attachments/assets/dbefaf72-fc47-41ef-94c8-3b20417f9162)
