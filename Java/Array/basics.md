# Basics of Arrays in Java

## What is an Array?
An array is a data structure that stores a fixed-size sequential collection of elements of the same type. It is used to store multiple values in a single variable, instead of declaring separate variables for each value.

### Characteristics of Arrays:
- **Fixed Size:** The size of an array is defined at the time of creation and cannot be changed later.
- **Indexed Storage:** Elements in an array are stored at contiguous memory locations and can be accessed using an index.
- **Homogeneous Elements:** All elements in an array must be of the same data type.
- **Efficient Access:** Elements can be accessed in constant time `O(1)` using the index.

## Array Declaration, Initialization, and Memory Allocation

### Declaring an Array
```java
// Syntax
dataType[] arrayName; // Recommended
dataType arrayName[]; // Allowed but not recommended
```
Examples:
```java
int[] numbers;    // Preferred style
char characters[];
```

### Allocating Memory for an Array
```java
// Allocating memory for an array
arrayName = new dataType[size];
```
Example:
```java
int[] numbers = new int[5]; // Array of 5 integers
```

### Initializing an Array
```java
// Inline initialization
int[] numbers = {10, 20, 30, 40, 50};
```

### Default Values of Array Elements
In Java, arrays are initialized with default values:
| Data Type  | Default Value |
|------------|--------------|
| byte, short, int, long | 0 |
| float, double | 0.0 |
| char | '\u0000' (null character) |
| boolean | false |
| Object references | null |

The default values are assigned automatically when the array is created, which helps avoid garbage values.

## Types of Arrays

### Single-Dimensional Arrays
A single-dimensional array is a list of elements stored in a linear sequence.
```java
int[] numbers = new int[5];
numbers[0] = 10;
numbers[1] = 20;
```

### Multi-Dimensional Arrays
Multi-dimensional arrays store data in tabular form (rows and columns).
```java
int[][] matrix = new int[3][3]; // 3x3 matrix
```

#### Jagged Arrays
A jagged array is an array of arrays where inner arrays may have different sizes.
```java
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[2];
jaggedArray[1] = new int[3];
jaggedArray[2] = new int[1];
```

## Anonymous Arrays
An anonymous array is an array that is created without assigning it to a reference variable. It is mainly used when we need to pass an array directly as an argument or for one-time use.

Example:
```java
printArray(new int[]{10, 20, 30, 40});

public static void printArray(int[] arr) {
    for (int num : arr) {
        System.out.print(num + " ");
    }
}
```
### Use Cases of Anonymous Arrays:
- **Passing arrays directly to methods**
- **Reducing memory usage for temporary arrays**
- **Creating quick test cases without defining named variables**

## Accessing Array Elements
Elements in an array are accessed using their index (starting from 0).
```java
int[] arr = {10, 20, 30, 40};
System.out.println(arr[2]); // Output: 30
```

## Common Mistakes with Arrays

### ArrayIndexOutOfBoundsException
Accessing an index that is out of range causes an exception.
```java
int[] arr = new int[5];
System.out.println(arr[5]); // Throws ArrayIndexOutOfBoundsException
```

### NullPointerException in Arrays
An array declared but not initialized will throw `NullPointerException` when accessed.
```java
int[] arr;
System.out.println(arr.length); // Throws NullPointerException
```

## Best Practices for Using Arrays in Java
- Always check the length before accessing elements.
- Use `Arrays.copyOf()` or `System.arraycopy()` instead of manual copying.
- Prefer `ArrayList` over arrays when dynamic resizing is required.
- Avoid memory wastage by allocating only the required size.

### Using `Arrays.copyOf()` and `System.arraycopy()`
When copying an array, manual element-wise copying can be inefficient. Java provides built-in methods to optimize this:

#### `Arrays.copyOf()`
Used to create a new array by copying elements from an existing array.
```java
int[] original = {1, 2, 3, 4, 5};
int[] copy = Arrays.copyOf(original, original.length);
```
- Creates a new array of specified length.
- Useful when you need an independent copy.

#### `System.arraycopy()`
Provides efficient copying of a portion of an array.
```java
int[] source = {10, 20, 30, 40, 50};
int[] destination = new int[5];
System.arraycopy(source, 1, destination, 0, 3);
```
- Copies 3 elements from `source[1]` to `destination[0]`.
- Faster than manual copying using loops.
- Suitable for performance-critical applications.

---

