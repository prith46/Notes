- `replaceAll("[^a-z0-9]", "")` is a Java method used to clean strings.
- The `[^a-z0-9]` is a regular expression.
- `^` inside `[]` negates the character set.
- It matches any character **not** a lowercase letter (`a-z`) or digit (`0-9`).
- `replaceAll(..., "")` removes those matched characters by replacing them with an empty string.
- Result: A string containing only lowercase letters and digits.
