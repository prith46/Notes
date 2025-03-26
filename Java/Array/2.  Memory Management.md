# Memory Management and Performance in Java Arrays

## Memory Allocation for Arrays
Java manages memory using the **heap** and **stack**:
- **Heap Memory**: Arrays are stored in heap memory, which is managed by Java's Garbage Collector.
- **Stack Memory**: References to arrays are stored in the stack.

### Example of Memory Allocation:
```java
int[] numbers = new int[5];
```
- The reference `numbers` is stored in stack memory.
- The actual array `{0, 0, 0, 0, 0}` is allocated in heap memory.

## Memory Layout of 1D and 2D Arrays in Java
### 1D Array Memory Layout
A 1D array is stored as a **contiguous block** in heap memory. Each element is placed in adjacent memory locations.
```java
int[] arr = {10, 20, 30, 40};
```
Memory representation:
| Address | Value |
|---------|-------|
| 1000    | 10    |
| 1004    | 20    |
| 1008    | 30    |
| 1012    | 40    |

### 2D Array Memory Layout
In Java, a **2D array is an array of arrays**, meaning each row is stored as a separate object.
```java
int[][] matrix = {{1, 2}, {3, 4}, {5, 6}};
```
Memory representation:
| Row Reference | Address |
|--------------|---------|
| matrix[0]    | 2000    |
| matrix[1]    | 3000    |
| matrix[2]    | 4000    |

Each row points to a separate contiguous memory block.

## Static vs. Dynamic Memory Allocation
### Static Memory Allocation
- Memory is allocated at **compile time**.
- Array size **must be known in advance**.
- Less flexible but **faster** due to fixed size.
```java
int[] staticArray = new int[10];
```

### Dynamic Memory Allocation
- Memory is allocated **at runtime**.
- Useful when **size is unknown initially**.
- More flexible but may have **performance overhead**.
```java
int size = new Scanner(System.in).nextInt();
int[] dynamicArray = new int[size];
```

## Performance Analysis of Array Operations
| Operation  | Time Complexity | Space Complexity |
|------------|----------------|------------------|
| Access     | O(1)           | O(1)             |
| Insertion (at end) | O(1) (if space available) | O(1) |
| Insertion (at start/middle) | O(n) | O(1) |
| Deletion (from end) | O(1) | O(1) |
| Deletion (from start/middle) | O(n) | O(1) |
| Search (Linear) | O(n) | O(1) |
| Search (Binary - Sorted Array) | O(log n) | O(1) |

## Time and Space Complexity of Common Array Operations
### Accessing Elements
- **Best case**: O(1) (Direct access via index)
- **Worst case**: O(1)

### Searching
- **Linear Search**: O(n) (Unsorted array)
- **Binary Search**: O(log n) (Sorted array)

### Insertion
- **At end**: O(1) (If space is available)
- **At beginning/middle**: O(n) (Shifting elements required)

### Deletion
- **From end**: O(1)
- **From beginning/middle**: O(n) (Shifting required)

### Sorting
- **Best sorting algorithms (Merge Sort, Quick Sort)**: O(n log n)

## Impact of Resizing an Array
### Using `System.arraycopy()`
When resizing an array manually, `System.arraycopy()` is used to copy elements efficiently.
```java
int[] oldArray = {1, 2, 3, 4};
int[] newArray = new int[8];
System.arraycopy(oldArray, 0, newArray, 0, oldArray.length);
```

### Growth Mechanism of `ArrayList`
`ArrayList` dynamically resizes itself when it reaches full capacity:
- Initial capacity = 10
- When full, new capacity = `oldCapacity * 1.5`
- Uses `System.arraycopy()` internally for efficient copying.
```java
ArrayList<Integer> list = new ArrayList<>();
for (int i = 0; i < 20; i++) {
    list.add(i);
}
```
This avoids frequent reallocations and improves performance.

## Garbage Collection and Arrays
- If an array is no longer referenced, it becomes eligible for **Garbage Collection (GC)**.
- Setting an array to `null` helps in memory deallocation:
```java
numbers = null;
```

## Conclusion
Understanding Java’s memory management, array performance, and resizing mechanisms is crucial for writing efficient code. Use built-in methods like `System.arraycopy()`, and prefer `ArrayList` for dynamic resizing to optimize performance.

