### 📌 Why start at `i = n/2 - 1` in heap building?

In a 0-indexed array, all nodes from index `n/2` to `n-1` are leaf nodes — they don’t need heapify.  
The last non-leaf node is at index `n/2 - 1`, so we start heapifying from there.

#### 🧮 Example:
For `n = 10`:  
`n/2 = 5` → start at `i = 4` (`n/2 - 1`)


Minimum largest element
Given an array A of N numbers, you have to perform B operations. In each operation, you have to pick any one of the N elements and add the original value(value stored at the index before we did any operations) to its current value. You can choose any of the N elements in each operation.
Perform B operations in such a way that the largest element of the modified array(after B operations) is minimized.
Find the minimum possible largest element after B operations.

From <https://www.scaler.com/academy/mentee-dashboard/class/351647/homework/problems/602/?navref=cl_pb_nv_tb> 
<img width="1705" height="1026" alt="image" src="https://github.com/user-attachments/assets/76674c8a-9eb1-47bb-8694-71e7eb47dc1e" />
