# Difference Between `trim()` and `strip()` in Java

| Feature          | `trim()`  | `strip()`  |
|-----------------|----------|-----------|
| **Introduced In** | Java 1.0 | Java 11 |
| **Removes** | Only standard spaces (`' '` U+0020) | All Unicode whitespace (including `U+00A0`, `U+2002`, etc.) |
| **Unicode Support** | ❌ No | ✅ Yes |
| **Performance** | Faster (simple check) | Slightly slower (checks Unicode) |

## **How They Work?**
- **`trim()`**  
  - Removes only basic ASCII space (`U+0020`).  
  - Doesn't remove Unicode spaces (e.g., non-breaking space `U+00A0`).  

- **`strip()`** *(Java 11+)*  
  - Uses `Character.isWhitespace()`, which recognizes and removes **all** whitespace characters, including Unicode.
  - **Use `strip()`** when dealing with **Unicode text** (e.g., input from the web, files) for full whitespace removal.

## **Example Code**
```java
public class TrimVsStripExample {
    public static void main(String[] args) {
        String text = "\u2002Hello World\u00A0"; // Contains ASCII and Unicode spaces

        System.out.println("Before: [" + text + "]");
        System.out.println("trim(): [" + text.trim() + "]");   // Doesn't remove Unicode spaces
        System.out.println("strip(): [" + text.strip() + "]"); // Removes all spaces
    }
}
```

## **Output**
```
Before: [ Hello World ] 
trim(): [ Hello World ]   // Unicode spaces remain
strip(): [Hello World]    // All spaces removed
```
