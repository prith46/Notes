## Code for Binary Search

```
private static int binarySearch(int[] a, int fromIndex, int toIndex, int key) {
        int low = fromIndex;
        int high = toIndex - 1;

        while (low <= high) {
            int mid = (low + high) >>> 1;
            int midVal = a[mid];

            if (midVal < key)
                low = mid + 1;
            else if (midVal > key)
                high = mid - 1;
            else
                return mid; // key found
        }
        return -(low + 1);  // key not found.
    }
```

# Why Return a Negative Value?

When the key is not found, we need to tell the caller two things:

- The key is missing.
- Where it should be inserted (so the array remains sorted).

By returning a negative value, we signal that the key does not exist in the array. This prevents confusion between a missing key and an index.

# Why -(low + 1)?

When the loop exits, `low` represents the insertion point—the index where the key should be inserted to maintain sorted order.

But if we simply return `low`, the caller won’t know if:

- The key was actually found.
- The key needs to be inserted.

So, we return `-(low + 1)`, and here's why:

- Adding `+1` prevents conflicts with index 0.
- If we return `-low`, then for `low = 0`, we'd return 0, which looks like a valid index.
- `-(low + 1)` ensures all return values for missing keys are negative.

The caller can retrieve the insertion point easily:

If the return value is negative, the insertion index can be found with:

```java
int insertIndex = -(returnValue) - 1;
```
- This makes it easy to insert the element at the correct position.

### 🔹 **Example to Understand it Clearly**

#### **Given Array:**

```java
int[] arr = {10, 20, 30, 40, 50};
```

#### **Searching for a Key That Exists:**

```java
int index = binarySearch0(arr, 0, arr.length, 30); 
System.out.println(index); // Output: 2 (Found at index 2)
```

#### **Searching for a Key That Doesn't Exist (e.g., 25):**

```java
int index = binarySearch0(arr, 0, arr.length, 25); 
System.out.println(index); // Output: -3
```

- `25` is missing, but it **should be inserted at index `2`** (between `20` and `30`).
- Return value: `-(2 + 1) = -3`.
- The caller can compute the insertion index using:

```java
int insertIndex = -(-3) - 1 = 2;
```

### 🔹 **Key Takeaways**

1. **Negative return values indicate that the key is missing.**
2. **`-(low + 1)` encodes the insertion index.**
3. **The caller can compute the insertion index using `-(returnValue) - 1`.**

---

# 🔥 How `>>>` Handles Integer Overflow When Calculating `mid`

### 🔹 What Happens in `(low + high) / 2`?

Given:

```java
int low = 1_000_000_000;  // 1 billion
int high = 2_000_000_000; // 2 billion
```

If we calculate `mid` using:

```java
int mid = (low + high) / 2;
```

Then:

```java
low + high = 1_000_000_000 + 2_000_000_000 = 3_000_000_000
```

😱 But Java `int` can only store values up to `2,147,483,647` (`Integer.MAX_VALUE`)!  
So, `3,000,000,000` overflows into a negative number!

---

### 🔥 How `>>> 1` Prevents Overflow

Using:

```java
int mid = (low + high) >>> 1;
```

Java first adds `low + high`, and even if it overflows into a negative number, `>>> 1` shifts it right without keeping the sign bit (it treats the overflowed number as unsigned).

#### Example: Simulating Overflow

Let’s break it down step by step.

---

#### ✅ Using Normal Addition (`/ 2`)

```java
int low = 1_000_000_000; 
int high = 2_000_000_000; 
int sum = low + high; 
System.out.println(sum); 
```

**Expected Output (but causes overflow):**

```cpp
-1_294_967_296  // (Overflowed value)
```

Now, if we do:

```java
int mid = sum / 2;
```

The division happens on an already-overflowed value, so it’s incorrect!

---

#### ✅ Using `>>> 1` to Fix Overflow

```java
int mid = (low + high) >>> 1;
System.out.println(mid);
```

---

### 🔹 How `>>>` Works Internally:

- `low + high` overflows into a negative number.
- `>>> 1` treats it as an unsigned number and shifts all bits right by 1.
- The result is still a valid positive number.

---

#### ✅ No Integer Overflow!

The result will be correct, even with large numbers.
