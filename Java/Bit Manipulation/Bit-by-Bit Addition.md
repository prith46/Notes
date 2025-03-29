## 1. Normal Addition.

```java
public class Solution {
    public int getSum(int a, int b) {
        int result = 0, carry = 0, position = 0;

        while((position < 32) && (a != 0 || b != 0 || carry != 0)){
            int bitA = a & 1;
            int bitB = b & 1;
            int sum = bitA ^ bitB ^ carry;

            result |= sum << position;
            carry = ((bitA & bitB) | (carry & (bitA ^ bitB)));

            a >>= 1;
            b >>= 1;
            position++;
        }

        return result;
    }
}
```
### Explanation of Each Line

1. **`int result = 0, carry = 0, position = 0;`**  
   - **result**: This will store the final result of the addition.  
   - **carry**: This stores the carry bit that results from a bitwise addition.  
   - **position**: This keeps track of the bit position that we are processing (starting from the least significant bit).

2. **`while((position < 32) && (a != 0 || b != 0 || carry != 0)) {`**  
   This `while` loop will run until either all 32 bits have been processed (for 32-bit integers), or there are no more bits to add in `a`, `b`, and no carry left.  
   This loop ensures that we process all bits from the least significant to the most significant (up to 32 bits for a standard integer).

3. **`int bitA = a & 1;`**  
   `bitA` extracts the least significant bit of `a`. This is done by performing a bitwise AND operation between `a` and `1`.  
   This gives either `0` or `1`, depending on whether the least significant bit of `a` is `0` or `1`.

4. **`int bitB = b & 1;`**  
   `bitB` extracts the least significant bit of `b`, similarly to how `bitA` was calculated.  
   This gives either `0` or `1`, depending on whether the least significant bit of `b` is `0` or `1`.

5. **`int sum = bitA ^ bitB ^ carry;`**  
   This calculates the sum of the bits at the current position, including any carry from the previous position.  
   The XOR (`^`) operator is used because it simulates addition without carry:
   - `0 ^ 0 = 0`
   - `0 ^ 1 = 1`
   - `1 ^ 0 = 1`
   - `1 ^ 1 = 0` (no carry here, just like binary addition)  
   We also XOR the carry because the carry bit from the previous iteration could affect the sum.

6. **`result |= sum << position;`**  
   This line sets the correct bit in the result.  
   `sum` is left-shifted by `position` to place it at the correct bit position.  
   The `|=` operator is a bitwise OR assignment, which sets the bit at the `position` in `result` to the value of `sum`. This accumulates the sum bit by bit.

7. **`carry = ((bitA & bitB) | (carry & (bitA ^ bitB)));`**  
   This calculates the carry for the next position.  
   First, we calculate the carry for this bit position by performing the bitwise AND of `bitA` and `bitB`: `bitA & bitB`. This tells us where both bits are `1`, and we need a carry.  
   Then, we need to check if there's a carry left from the previous position (`carry & (bitA ^ bitB)`), which happens when one bit is `1` and the other is `0`.  
   The `|` operator is used to combine these two conditions. This will generate the proper carry for the next bit.

8. **`a >>= 1;`**  
   Right-shift `a` by 1 bit. This effectively removes the least significant bit (which we've already processed) and prepares `a` for the next iteration.

9. **`b >>= 1;`**  
   Right-shift `b` by 1 bit, similar to `a`. This removes the least significant bit of `b` and prepares it for the next iteration.

10. **`position++;`**  
   Increment the position to move to the next bit in the next iteration.  
   This is crucial because we need to process each bit in turn, starting from the least significant bit and moving to the most significant.

![image](https://github.com/user-attachments/assets/577a9646-4843-490c-ba48-2c06fd5380d9)
![image](https://github.com/user-attachments/assets/100772f7-835e-420a-8f53-71f7c6f61ddc)

## Why `(position < 32)`

![image](https://github.com/user-attachments/assets/52c54136-35d7-450e-a531-109b24fdaeb0)
![image](https://github.com/user-attachments/assets/c9dedf9e-cd8a-45de-9958-b45382a5a905)

>Use >>> for Zero-Fill:
If you want to force 0s into the MSB, use >>> (but note this converts negatives to positives)

>So, to prevent the loop running infinitely we need to use position < 32.
---

## 2. Optimised.

```
public class Solution {
    public int getSum(int a, int b) {
        while (b != 0) {
            int carry = (a & b) << 1;
            a ^= b;
            b = carry;
        }
        return a;
    }
}
```

### Step-by-Step Explanation:

1. **`while (b != 0):`**  
   This `while` loop runs as long as there is a carry to propagate. In binary addition, if the carry is zero, the addition is complete. So, the loop continues until there's no carry left.

2. **`int carry = (a & b) << 1;`**  
   - **`(a & b)`**: This performs a bitwise AND between `a` and `b` to find the positions where both bits are `1`. These are the positions where a carry will occur in the next iteration.  
   - **`<< 1`**: The result of `(a & b)` is then shifted left by one position. This is because the carry should be added to the next higher bit position in the next iteration.  
   
   For example: if `a = 3` (0011) and `b = 5` (0101), then `a & b` gives `0001`, and after the left shift, carry will be `0010`.

3. **`a ^= b;`**  
   **`^ (XOR)`**: This operation is used to sum `a` and `b` without considering the carry. It works as follows:
   - `0 ^ 0 = 0`
   - `0 ^ 1 = 1`
   - `1 ^ 0 = 1`
   - `1 ^ 1 = 0` (this is like binary addition without carry).
   
   So, `a ^= b` effectively adds `a` and `b` without including the carry. This is the partial sum of `a` and `b`.

4. **`b = carry;`**  
   The carry calculated earlier (from `a & b`) is stored in `b`, and this will be used in the next iteration to propagate the carry to the next higher bit.

5. **`return a;`**  
   Once `b` becomes zero, there is no carry left, and `a` contains the final result of the addition. This value is returned.
