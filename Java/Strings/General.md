### Special case while getting nextLine() input

> When the inputs are given in separate lines, and we take a String input using nextLine()
after taking number input[nextInt(), nextLong(), nextFloat(), nextDouble()] or a single
word [next()] then we get a empty String.

```
input -> Hello world

int n = scanner.nextInt();          // n = 5
String str = scanner.nextLine();    // str = ""
String str1 = scanner.nextLine();   // str1 = "Hello world"
```
