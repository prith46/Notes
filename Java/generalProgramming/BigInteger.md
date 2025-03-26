# BigInteger in Java

## What is BigInteger in Java?
In Java, the `BigInteger` class (from `java.math` package) is used to store and perform operations on very large integers that cannot fit in primitive types like `int` or `long`.

## Why Use BigInteger?
- `int` can store numbers up to `2^31 - 1` (≈ 2 billion).
- `long` can store numbers up to `2^63 - 1` (≈ 9 quintillion).
- If you need numbers larger than this, `BigInteger` is the solution!

## Declaring and Initializing a BigInteger
```
import java.math.BigInteger;

public class Main {
    public static void main(String[] args) {
        // Creating a BigInteger from a String
        BigInteger bigNum1 = new BigInteger("123456789012345678901234567890");
        System.out.println(bigNum1); // Output: 123456789012345678901234567890

        // Creating a BigInteger from an int
        BigInteger bigNum2 = BigInteger.valueOf(1000);
        System.out.println(bigNum2); // Output: 1000
    }
}
```

## Other Useful Methods in BigInteger

### 1. Arithmetic Operations
🔹 `add()`, `subtract()`, `multiply()`, `divide()`, `mod()`
```
BigInteger a = new BigInteger("100");
BigInteger b = new BigInteger("25");

System.out.println(a.add(b));      // 125
System.out.println(a.subtract(b)); // 75
System.out.println(a.multiply(b)); // 2500
System.out.println(a.divide(b));   // 4
System.out.println(a.mod(b));      // 0 (100 % 25)
```

## **Can We Use Normal Arithmetic Operators (`+`, `-`, `*`, `/`) with BigInteger?**
No, you **cannot** use normal arithmetic operators like `+`, `-`, `*`, `/` with `BigInteger` in Java.

### **Why?**
- `BigInteger` is **immutable** and is a **class**, not a primitive type like `int` or `long`.
- Java **does not support operator overloading** (unlike C++).
- You must use **methods** instead of operators.

### 2. Power and GCD
🔹 `pow(n)`, `gcd()`
```
BigInteger x = new BigInteger("5");
System.out.println(x.pow(3)); // 5^3 = 125

BigInteger y = new BigInteger("18");
BigInteger z = new BigInteger("24");
System.out.println(y.gcd(z)); // GCD of 18 and 24 = 6
```

### 3. Comparison Methods
🔹 `compareTo()`, `min()`, `max()`
```java
BigInteger num1 = new BigInteger("50");
BigInteger num2 = new BigInteger("75");

System.out.println(num1.compareTo(num2)); // -1 (num1 < num2)
System.out.println(num1.min(num2));       // 50
System.out.println(num1.max(num2));       // 75
```

### 4. Checking Properties
🔹 `isProbablePrime()`, `bitLength()`, `bitCount()`
```
BigInteger primeCandidate = new BigInteger("37");
System.out.println(primeCandidate.isProbablePrime(10)); // true (probably prime)

BigInteger largeNum = new BigInteger("1024");
System.out.println(largeNum.bitLength()); // 11 (since 1024 = 10000000000 in binary)

BigInteger bitCountExample = new BigInteger("15"); // Binary: 1111
System.out.println(bitCountExample.bitCount()); // 4 (Number of 1s in binary)
```

### 5. Random BigInteger Generation
🔹 `BigInteger.probablePrime()`, `BigInteger(int bitLength, Random rand)`
```
import java.math.BigInteger;
import java.util.Random;

public class Main {
    public static void main(String[] args) {
        // Generate a random 20-bit number
        BigInteger randomNum = new BigInteger(20, new Random());
        System.out.println(randomNum);

        // Generate a random prime number with 20 bits
        BigInteger primeNum = BigInteger.probablePrime(20, new Random());
        System.out.println(primeNum);
    }
}
```
## isProbablePrime(int certainty)

The `isProbablePrime(int certainty)` method in `BigInteger` checks if a number is **probably prime** with high probability. A higher `certainty` value increases the accuracy of the test. If it returns `true`, the number is **likely prime**, but not guaranteed.

### Example:
```
BigInteger num = new BigInteger("17");
System.out.println(num.isProbablePrime(10)); // true
```

## Uses

- **Cryptography** – Used in algorithms like RSA for secure encryption.  
- **Prime Number Generation** – Helps generate large prime numbers for secure key pairs.  
- **Mathematical Research** – Assists in testing large prime numbers for various studies.  
- **Efficient Primality Testing** – A faster alternative when exact primality tests are computationally expensive.  
- **Random Prime Generation** – Generates prime numbers efficiently for security and cryptographic protocols.

# BigInteger Bit Manipulation in Java

## 1️⃣ `testBit(int n)`

Checks if the `n`-th bit (starting from 0) in the binary representation of a `BigInteger` is 1 or 0.

- **Returns:** `true` if the bit is 1, otherwise `false`.

### Example:
```java
import java.math.BigInteger;

public class Main {
    public static void main(String[] args) {
        BigInteger num = new BigInteger("42"); // Binary: 101010

        System.out.println(num.testBit(0)); // false (0th bit is 0)
        System.out.println(num.testBit(1)); // true  (1st bit is 1)
        System.out.println(num.testBit(3)); // true  (3rd bit is 1)
    }
}
```

---

## 2️⃣ `setBit(int n)`

Returns a new `BigInteger` with the `n`-th bit set to 1, keeping other bits unchanged.

### Example:
```java
BigInteger num = new BigInteger("42"); // Binary: 101010
BigInteger modified = num.setBit(0);   // Sets 0th bit to 1

System.out.println(modified); // Output: 43 (Binary: 101011)
```

---

## 3️⃣ `clearBit(int n)`

Returns a new `BigInteger` with the `n`-th bit cleared (set to 0).

### Example:
```java
BigInteger num = new BigInteger("43"); // Binary: 101011
BigInteger modified = num.clearBit(0); // Clears 0th bit (sets it to 0)

System.out.println(modified); // Output: 42 (Binary: 101010)
```

---

## 4️⃣ `flipBit(int n)`

Toggles (flips) the `n`-th bit (`0 → 1` or `1 → 0`).

### Example:
```java
BigInteger num = new BigInteger("42"); // Binary: 101010
BigInteger modified = num.flipBit(1);  // Flips 1st bit

System.out.println(modified); // Output: 40 (Binary: 101000)
```


