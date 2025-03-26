# Array Internals and Java-Specific Implementations

## How Java Implements Arrays Internally

- In Java, arrays are **objects** stored in heap memory.
- The **JVM (Java Virtual Machine)** manages arrays dynamically.
- Each array object has a **header** that stores:
  - Length of the array
  - Type of elements
  - A reference to the actual data
- Arrays are **zero-indexed** and contiguous in memory.

### Example Memory Representation of an Array:
```java
int[] arr = new int[5];
```
Memory layout:
| Address  | Value |
|----------|-------|
| 1000     | 0     |
| 1004     | 0     |
| 1008     | 0     |
| 1012     | 0     |
| 1016     | 0     |

## Differences Between Primitive Type Arrays and Object Type Arrays

| Feature | Primitive Type Array | Object Type Array |
|---------|----------------------|-------------------|
| Storage | Stores actual values | Stores references to objects |
| Memory Usage | Less (direct storage) | More (extra reference storage) |
| Example | `int[] arr = new int[5];` | `String[] arr = new String[5];` |
| Access Speed | Faster | Slightly slower due to reference lookup |

### Example of Primitive vs. Object Type Arrays:
```java
int[] intArray = {1, 2, 3}; // Stores values directly
String[] strArray = {"A", "B", "C"}; // Stores references
```

## Cloning an Array (Shallow Copy vs. Deep Copy)

### Shallow Copy
- Creates a **new array reference**, but **does not copy** the actual objects.
- If the original array is modified, the cloned array reflects those changes.

```java
int[] original = {1, 2, 3};
int[] shallowCopy = original; // Only copies reference
shallowCopy[0] = 10;
System.out.println(original[0]); // Prints 10
```

### Deep Copy
- Creates a **new array and copies** elements individually.
- Modifications in the copied array do not affect the original array.

```java
int[] deepCopy = Arrays.copyOf(original, original.length);
deepCopy[0] = 20;
System.out.println(original[0]); // Still prints 10
```

For object arrays, use **`clone()`** carefully:
```java
Person[] clonedArray = originalArray.clone(); // Still a shallow copy for objects!
```
To perform **deep copying** for objects, manually copy each element:
```java
Person[] deepCopiedArray = new Person[originalArray.length];
for (int i = 0; i < originalArray.length; i++) {
    deepCopiedArray[i] = new Person(originalArray[i]);
}
```

## Immutable Arrays and How to Make an Array Unmodifiable

Arrays in Java are **mutable** by default. To make an array immutable:

### Using `Collections.unmodifiableList()`
```java
List<Integer> immutableList = Collections.unmodifiableList(Arrays.asList(1, 2, 3));
immutableList.add(4); // Throws UnsupportedOperationException
```

### Using `Arrays.copyOf()`
```java
int[] immutableArray = Arrays.copyOf(originalArray, originalArray.length);
```

## How `Arrays.asList()` Works and Its Limitations

### How It Works:
- `Arrays.asList(array)` converts an **array to a fixed-size list**.
- The list is backed by the original array.
- Any change to the list **modifies the array**.

```java
String[] arr = {"A", "B", "C"};
List<String> list = Arrays.asList(arr);
list.set(1, "Z");
System.out.println(arr[1]); // Prints "Z"
```

### Limitations:
1. **Size is fixed** – Cannot add/remove elements.
2. **Direct modification of list affects the array**.
3. **Cannot use `list.add()` or `list.remove()`**.

To create a truly **modifiable list**, use:
```java
List<String> modifiableList = new ArrayList<>(Arrays.asList(arr));
```

## How `ArrayDeque` Works Internally Compared to Normal Arrays

### `ArrayDeque` (Double-Ended Queue)
- Unlike normal arrays, `ArrayDeque` allows **fast insertions and deletions** at both ends.
- Uses a **circular buffer** to improve performance.
- **Does not support null elements**.

### Internal Implementation
- Uses a **resizable array**.
- **Maintains head and tail pointers** to track the queue.
- Resizes when full by **doubling capacity** and using `System.arraycopy()`.

```java
Deque<Integer> deque = new ArrayDeque<>();
deque.addFirst(1); // O(1)
deque.addLast(2); // O(1)
deque.removeFirst(); // O(1)
deque.removeLast(); // O(1)
```

### Performance Comparison: `ArrayDeque` vs. `ArrayList`

| Operation | `ArrayDeque` | `ArrayList` |
|-----------|-------------|-------------|
| Insert at End | O(1) | O(1) (amortized) |
| Insert at Beginning | O(1) | O(n) (shifting required) |
| Delete at End | O(1) | O(1) |
| Delete at Beginning | O(1) | O(n) |

### Why Use `ArrayDeque` Over `LinkedList`?
1. **Faster than `LinkedList`** (better cache locality).
2. **Less memory overhead** (no extra node objects).
3. **Efficient for queue operations**.

## Conclusion
Understanding Java's **array internals, object vs. primitive storage, cloning techniques, immutability, `Arrays.asList()` behavior, and `ArrayDeque` efficiency** is crucial for FAANG-level interviews. Knowing these topics deeply will help answer low-level system design and performance-related questions.

