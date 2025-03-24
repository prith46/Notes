# Java Collections Methods

## 1. Sorting & Searching

### `Collections.sort(List<T> list)`
Sorts the list in ascending order.
```java
List<Integer> list = Arrays.asList(5, 2, 8, 1, 9);
Collections.sort(list);
System.out.println(list); // [1, 2, 5, 8, 9]
```

### `Collections.sort(List<T> list, Comparator<? super T> c)`
Sorts using a custom comparator.
```java
Collections.sort(list, Collections.reverseOrder());
System.out.println(list); // [9, 8, 5, 2, 1]
```

### `Collections.binarySearch(List<T> list, T key)`
Searches for `key` in a **sorted** list.
```java
int index = Collections.binarySearch(list, 5);
System.out.println(index); // 2 (assuming sorted list)
```

---

## 2. Finding Min & Max

### `Collections.min(Collection<T> coll)`
Finds the smallest element.
```java
System.out.println(Collections.min(list)); // 1
```

### `Collections.max(Collection<T> coll)`
Finds the largest element.
```java
System.out.println(Collections.max(list)); // 9
```

---

## 3. Reverse, Rotate, Swap

### `Collections.reverse(List<T> list)`
Reverses the order.
```java
Collections.reverse(list);
System.out.println(list); // [9, 8, 5, 2, 1]
```

### `Collections.rotate(List<T> list, int distance)`
Rotates elements.
```java
Collections.rotate(list, 2);
System.out.println(list); // [2, 1, 9, 8, 5]
```

### `Collections.swap(List<?> list, int i, int j)`
Swaps two elements.
```java
Collections.swap(list, 0, 4);
System.out.println(list); // [5, 1, 9, 8, 2]
```

---

## 4. Frequency & Disjoint

### `Collections.frequency(Collection<?> coll, Object o)`
Counts occurrences.
```java
System.out.println(Collections.frequency(list, 1)); // 1
```

### `Collections.disjoint(Collection<?> c1, Collection<?> c2)`
Checks if two collections have **no common elements**.
```java
List<Integer> list2 = Arrays.asList(10, 20, 30);
System.out.println(Collections.disjoint(list, list2)); // true
```

---

## 5. Fill, Copy, Replace

### `Collections.fill(List<? super T> list, T obj)`
Fills the list with a specific value.
```java
Collections.fill(list, 0);
System.out.println(list); // [0, 0, 0, 0, 0]
```

### `Collections.copy(List<? super T> dest, List<? extends T> src)`
Copies elements from `src` to `dest`.
```java
List<Integer> dest = new ArrayList<>(Arrays.asList(0, 0, 0, 0, 0));
Collections.copy(dest, list);
System.out.println(dest);
```

### `Collections.replaceAll(List<T> list, T oldVal, T newVal)`
Replaces all occurrences.
```java
Collections.replaceAll(list, 5, 99);
System.out.println(list); // [99, 1, 9, 8, 2]
```

---

## 6. Shuffle & Randomization

### `Collections.shuffle(List<?> list)`
Randomly shuffles the list.
```java
Collections.shuffle(list);
System.out.println(list); // Random order
```

### `Collections.shuffle(List<?> list, Random rnd)`
Shuffles with a given random generator.
```java
Collections.shuffle(list, new Random());
```

---

## 7. Thread-Safe Collections

### `Collections.synchronizedList(List<T> list)`
Creates a thread-safe list.
```java
List<Integer> syncList = Collections.synchronizedList(new ArrayList<>(list));
```

### `Collections.synchronizedSet(Set<T> set)`
Creates a thread-safe set.
```java
Set<Integer> syncSet = Collections.synchronizedSet(new HashSet<>());
```

---

## 8. Unmodifiable Collections (Read-Only)

### `Collections.unmodifiableList(List<? extends T> list)`
Creates a read-only list.
```java
List<Integer> unmodList = Collections.unmodifiableList(list);
// unmodList.add(10); // Throws UnsupportedOperationException
```

### `Collections.unmodifiableSet(Set<? extends T> set)`
Creates a read-only set.
```java
Set<Integer> unmodSet = Collections.unmodifiableSet(new HashSet<>(list));
```

---

## 9. Singleton & Empty Collections

### `Collections.singleton(T obj)`
Creates an immutable collection with one element.
```java
Collection<Integer> singleton = Collections.singleton(42);
```

### `Collections.emptyList()`, `Collections.emptySet()`, `Collections.emptyMap()`
Creates immutable empty collections.
```java
List<Integer> emptyList = Collections.emptyList();
Set<Integer> emptySet = Collections.emptySet();
Map<Integer, String> emptyMap = Collections.emptyMap();
```

---

## 10. Other Utilities

### `Collections.nCopies(int n, T obj)`
Creates an immutable list with `n` copies of an object.
```java
List<Integer> copies = Collections.nCopies(5, 100);
System.out.println(copies); // [100, 100, 100, 100, 100]
```

### `Collections.checkedList(List<T> list, Class<T> type)`
Ensures type safety at runtime.
```java
List<String> checkedList = Collections.checkedList(new ArrayList<>(), String.class);
```

