# 📝 Backtracking - Fundamentals & Algorithm Template

## **📌 Introduction to Backtracking**
Backtracking is a **recursive problem-solving approach** used to explore all possible solutions to a problem. It incrementally builds a solution, abandons (backtracks) upon reaching an invalid state, and continues searching for valid solutions.

### **🔹 When to Use Backtracking?**
- **Combinatorial problems** (subsets, permutations, combinations)
- **Constraint satisfaction problems** (N-Queens, Sudoku, Word Search)
- **Graph traversal problems** (Hamiltonian cycle, Knight's tour)

---

## **🔍 How Backtracking Works?**
Backtracking follows a systematic approach:
1. **Make a choice** → Select a possible solution component.
2. **Recursively explore** → Continue building upon the current selection.
3. **Backtrack if needed** → Undo the last choice if it leads to an invalid solution.

By eliminating infeasible solutions early (**pruning**), backtracking significantly improves efficiency compared to brute-force approaches.

---

## **⚡ Backtracking vs Brute Force**
| Feature | Brute Force | Backtracking |
|---------|------------|--------------|
| Approach | Explores all possibilities exhaustively | Explores possibilities selectively, eliminating invalid ones early |
| Efficiency | High time complexity | Optimized with pruning |
| Use Case | Small input sizes | Large, combinatorial problems |

---

## **📝 General Backtracking Algorithm Template**
```java
void backtrack(parameters) {
    if (base case is met) {
        process the solution;
        return;
    }
    
    for (each possible choice) {
        make a choice;
        backtrack(updated parameters);
        undo the choice (backtrack);
    }
}
```
### **Key Components:**
- **Base Case** → Determines when to stop recursion and process a valid solution.
- **Recursive Exploration** → Tries all possible valid choices.
- **Undo Step (Backtrack)** → Removes the last choice and explores an alternative path.

---

## **📌 Example: Generating All Subsets (Power Set)**
This example generates all subsets of a given set `{1, 2, 3}`.

```java
import java.util.*;

class SubsetGenerator {
    static void generateSubsets(int[] nums, int index, List<Integer> current, List<List<Integer>> result) {
        if (index == nums.length) {
            result.add(new ArrayList<>(current));
            return;
        }
        
        // Include current element
        current.add(nums[index]);
        generateSubsets(nums, index + 1, current, result);
        
        // Exclude current element (backtrack)
        current.remove(current.size() - 1);
        generateSubsets(nums, index + 1, current, result);
    }
    
    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        List<List<Integer>> result = new ArrayList<>();
        generateSubsets(nums, 0, new ArrayList<>(), result);
        
        System.out.println(result);
    }
}
```
### **🔹 Output:**
```
[[], [3], [2], [2, 3], [1], [1, 3], [1, 2], [1, 2, 3]]
```
### **Breakdown of Approach:**
- **Base case:** If all elements have been considered, store the subset.
- **Recursive calls:**
  - Include the current element in the subset.
  - Exclude the current element and move to the next.
- **Backtracking:** The last element is removed after exploring all possibilities for a given path.

---
