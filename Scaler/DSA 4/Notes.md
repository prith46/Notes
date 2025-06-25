### 📌 Why start at `i = n/2 - 1` in heap building?

In a 0-indexed array, all nodes from index `n/2` to `n-1` are leaf nodes — they don’t need heapify.  
The last non-leaf node is at index `n/2 - 1`, so we start heapifying from there.

#### 🧮 Example:
For `n = 10`:  
`n/2 = 5` → start at `i = 4` (`n/2 - 1`)
