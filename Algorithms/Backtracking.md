# 📝 Backtracking - Step 1: Basics & Algorithm Template

## **📌 What is Backtracking?**
Backtracking is a **recursive algorithm** used to solve problems by trying all possible solutions and eliminating invalid ones (**backtracking** when necessary). It is commonly used in:
- **Combinatorial problems** (subsets, permutations, combinations)
- **Constraint problems** (N-Queens, Sudoku, Word Search)
- **Graph problems** (Hamiltonian cycle, Knight's tour)

---

## **🔍 How Backtracking Works?**
Backtracking follows a **decision-making tree** approach:
1. **Make a choice.**
2. **Explore recursively with that choice.**
3. **If an invalid state is reached, backtrack and undo the choice.**

This process continues until all solutions are found or the best solution is reached.

---

## **⚡ Backtracking vs Brute Force**
| Feature | Brute Force | Backtracking |
|---------|------------|--------------|
| Approach | Tries all possibilities blindly | Tries possibilities but eliminates invalid cases early (pruning) |
| Efficiency | High time complexity | Optimized with pruning |
| Use Case | Small inputs, simple problems | Large inputs, combinatorial problems |

---

## **📝 Backtracking Algorithm Template**
```java
void backtrack(parameters) {
    if (base case met) {
        process solution;
        return;
    }
    
    for (each possible choice) {
        make choice;
        backtrack(updated parameters);
        undo choice (backtrack);
    }
}
```
🔹 **Base Case:** When we reach a valid solution, we stop and process it.
🔹 **Recursive Call:** Explore all possibilities.
🔹 **Undo Step:** Remove the last choice and try a new path (backtrack).

---

## **📌 Example: Generating Binary Strings of Length `N`**
```java
class BinaryStrings {
    static void generateBinary(int n, String output) {
        if (n == 0) {
            System.out.println(output);
            return;
        }
        
        generateBinary(n - 1, output + "0");
        generateBinary(n - 1, output + "1");
    }
    
    public static void main(String[] args) {
        int n = 3;
        generateBinary(n, "");
    }
}
```
### **🔹 Output for `n = 3`:**
```
000
001
010
011
100
101
110
111
```
This follows the **Backtracking template:**
- Base case: `n == 0`, print the output.
- Choices: Append `0` or `1`.
- Backtrack: No undo step needed here since we generate a new string.

---
