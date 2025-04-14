## Binary Search

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

### 🔹 Why Return a Negative Value?

- A negative return signals the key is missing and encodes where it should be inserted.  
- `-(low + 1)` avoids confusion with index `0` and helps the caller compute the insertion point.
  

### 🔹 Why Use `>>> 1` to Find Mid Safely

- `(low + high)` can overflow if the values are large.  
- `>>> 1` safely divides the sum by 2 using an **unsigned right shift**, preventing overflow.  
- It ensures `mid` is always a valid index even if `(low + high)` exceeds `Integer.MAX_VALUE`.
  

### Binary Search in a 2D Sorted Matrix

- Apply binary search on the matrix by treating it as a flattened array from index `0` to `m * n - 1`.  
- Use `row = mid // n` to find which row the element is in, and `col = mid % n` to get its position within that row.
  
