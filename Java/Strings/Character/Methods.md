# Java Character Classification Methods

### **Character Classification Methods**

| Method | Description | Example |
|--------|-------------|---------|
| `Character.isLetter(char ch)` | Checks if the character is a letter (A-Z or a-z). | `Character.isLetter('A')` → `true` |
| `Character.isDigit(char ch)` | Checks if the character is a digit (0-9). | `Character.isDigit('5')` → `true` |
| `Character.isLetterOrDigit(char ch)` | Checks if the character is a letter or a digit. | `Character.isLetterOrDigit('A')` → `true` |
| `Character.isWhitespace(char ch)` | Checks if the character is a whitespace character (space, tab, newline, etc.). | `Character.isWhitespace(' ')` → `true` |
| `Character.isUpperCase(char ch)` | Checks if the character is an uppercase letter. | `Character.isUpperCase('A')` → `true` |
| `Character.isLowerCase(char ch)` | Checks if the character is a lowercase letter. | `Character.isLowerCase('a')` → `true` |
| `Character.isSpaceChar(char ch)` | Checks if the character is a space character (but not all whitespace like `\n` or `\t`). | `Character.isSpaceChar(' ')` → `true` |
| `Character.isISOControl(char ch)` | Checks if the character is an ISO control character (ASCII values 0-31 and 127). | `Character.isISOControl('\n')` → `true` |
| `Character.isJavaIdentifierStart(char ch)` | Checks if the character is valid as the first character of a Java identifier. | `Character.isJavaIdentifierStart('_')` → `true` |
| `Character.isJavaIdentifierPart(char ch)` | Checks if the character is valid in a Java identifier (except the first position). | `Character.isJavaIdentifierPart('5')` → `true` |
| `Character.isAlphabetic(char ch)` *(Java 7+)* | Checks if the character is alphabetic (includes letters and some Unicode characters). | `Character.isAlphabetic('A')` → `true` |
| `Character.isMirrored(char ch)` | Checks if the character has a mirrored counterpart in Unicode (like brackets). | `Character.isMirrored('(')` → `true` |

## Example Usage in Java

```java
public class CharacterMethodsExample {
    public static void main(String[] args) {
        char ch = 'A';
        System.out.println("isLetter: " + Character.isLetter(ch));
        System.out.println("isDigit: " + Character.isDigit(ch));
        System.out.println("isLetterOrDigit: " + Character.isLetterOrDigit(ch));
        System.out.println("isWhitespace: " + Character.isWhitespace(' '));
        System.out.println("isUpperCase: " + Character.isUpperCase(ch));
        System.out.println("isLowerCase: " + Character.isLowerCase(ch));
        System.out.println("isJavaIdentifierStart: " + Character.isJavaIdentifierStart('_'));
        System.out.println("isJavaIdentifierPart: " + Character.isJavaIdentifierPart('5'));
    }
}
```

This program demonstrates how to use various `Character` methods to analyze characters in Java.

