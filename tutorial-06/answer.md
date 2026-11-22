# Tutorial 06 — Java Methods

## Question 1

### (a) Define a static method that returns the maximum number from 3 integer parameters.

**Answer**

```java
public static int maximum(int num1, int num2, int num3) {
    int max = num1;

    if (num2 > max) {
        max = num2;
    }

    if (num3 > max) {
        max = num3;
    }

    return max;
}
```

**Explanation**

- `public static int` means this is a static method that returns an integer.
- The method receives three integer arguments: `num1`, `num2` and `num3`.
- We initially assume `num1` is the maximum.
- We compare `num2` and `num3` with the current maximum and update `max` when a larger value is found.
- `return max;` sends the largest value back to the statement that called the method.

**Example call**

```java
int result = maximum(12, 25, 8);
System.out.println(result); // 25
```

### (b) Define a static method that determines whether the given integer is a square number.

**Answer**

```java
public static boolean isSquare(int number) {
    if (number < 0) {
        return false;
    }

    int root = (int) Math.sqrt(number);
    return root * root == number;
}
```

**Explanation**

- The return type is `boolean` because the method answers a yes-or-no question.
- A negative integer cannot be a square number, so the method immediately returns `false`.
- `Math.sqrt(number)` calculates the square root. We convert it to an integer and store it in `root`.
- We check whether `root * root` equals the original number. If they are equal, the number is a perfect square.

**Example calls**

```java
System.out.println(isSquare(25)); // true
System.out.println(isSquare(26)); // false
```

### (c) Define a static method that computes the combination function C(n,k).

The question gives:

\[
C(n,k) = \frac{n!}{k!(n-k)!}
\]

**Answer**

```java
public static long factorial(int number) {
    long result = 1;

    for (int i = 1; i <= number; i++) {
        result *= i;
    }

    return result;
}

public static long combination(int n, int k) {
    if (n < 0 || k < 0 || k > n) {
        return -1;
    }

    return factorial(n) / (factorial(k) * factorial(n - k));
}
```

**Explanation**

- `factorial()` is a separate helper method that calculates the factorial of a non-negative integer.
- We start `result` at `1` because factorial is calculated by multiplication.
- The `for` loop multiplies `result` by every integer from `1` to `number`.
- In `combination()`, the condition checks that `n` and `k` are non-negative and that `k` is not greater than `n`.
- If the arguments are invalid, the method returns `-1` as an invalid-input indicator.
- Otherwise, it applies the formula given in the question.

**Example call**

```java
System.out.println(combination(5, 2)); // 10
```

For this example, \(C(5,2) = 5! / (2! \times 3!) = 10\).

**Note:** A `long` has a limited range, so factorial values and combination results that are too large can overflow. This simple implementation is suitable for small inputs.

### (d) Define a static method that determines whether the parameter is a pentagonal number.

The question gives:

\[
P_n = \frac{n(3n-1)}{2}
\]

**Answer**

```java
public static boolean isPentagonal(int number) {
    if (number < 1) {
        return false;
    }

    int n = 1;
    int pentagonal = 1;

    while (pentagonal < number) {
        n++;
        pentagonal = n * (3 * n - 1) / 2;
    }

    return pentagonal == number;
}
```

**Explanation**

- A pentagonal number is generated using the formula \(P_n = n(3n-1)/2\), where `n` starts from `1`.
- Numbers smaller than `1` are rejected.
- We calculate pentagonal numbers one by one using the `while` loop.
- The loop stops when the calculated pentagonal number is equal to or greater than the given number.
- Finally, `pentagonal == number` checks whether the given number is exactly a pentagonal number.

**Example calls**

```java
System.out.println(isPentagonal(12)); // true
System.out.println(isPentagonal(10)); // false
```

### (e) Define a static method that displays the number of letters and the number of digits of a String parameter.

**Answer**

```java
public static void countLettersAndDigits(String text) {
    int letters = 0;
    int digits = 0;

    for (int i = 0; i < text.length(); i++) {
        char ch = text.charAt(i);

        if (Character.isLetter(ch)) {
            letters++;
        } else if (Character.isDigit(ch)) {
            digits++;
        }
    }

    System.out.println("Number of letters: " + letters);
    System.out.println("Number of digits: " + digits);
}
```

**Explanation**

- This method has `void` as its return type because it displays the results instead of returning a value.
- `letters` and `digits` are counters, both starting at `0`.
- The `for` loop visits each character in the string.
- `text.charAt(i)` gets the character at index `i`.
- `Character.isLetter(ch)` checks whether the character is a letter.
- `Character.isDigit(ch)` checks whether the character is a digit.
- The appropriate counter increases by `1`. Spaces and punctuation are not counted.

**Example call**

```java
countLettersAndDigits("Java 2026!");
```

Output:

```text
Number of letters: 4
Number of digits: 4
```

### (f) Define a static void method that generates 10 random numbers within 0 to 100 to the method's parameter. The random numbers can be accessed by the main method.

**Answer**

```java
public static void generateRandomNumbers(int[] numbers) {
    for (int i = 0; i < numbers.length; i++) {
        numbers[i] = (int) (Math.random() * 101);
    }
}
```

**Example use in `main()`**

```java
public static void main(String[] args) {
    int[] numbers = new int[10];

    generateRandomNumbers(numbers);

    for (int i = 0; i < numbers.length; i++) {
        System.out.println(numbers[i]);
    }
}
```

**Explanation**

- The method receives an integer array through the parameter `numbers`.
- `Math.random()` generates a decimal value from `0.0` (inclusive) up to, but not including, `1.0`.
- Multiplying by `101` and converting to `int` produces an integer from `0` to `100`, inclusive.
- Each generated number is stored in an array element.
- In `main()`, we create an array with 10 elements and pass it to the method.
- Because the method fills the array supplied by `main()`, the generated values can be accessed from `main()` after the method call.

### (g) Define a static void method that returns the area and circumference of a circle given the argument is radius.

The question gives:

\[
Area = \pi r^2
\]

\[
Circumference = 2\pi r
\]

**Answer**

```java
public static void calculateCircle(double radius, double[] results) {
    results[0] = Math.PI * radius * radius;
    results[1] = 2 * Math.PI * radius;
}
```

**Example use in `main()`**

```java
public static void main(String[] args) {
    double radius = 5;
    double[] results = new double[2];

    calculateCircle(radius, results);

    System.out.println("Area: " + results[0]);
    System.out.println("Circumference: " + results[1]);
}
```

**Explanation**

- The method receives the radius and a `double` array named `results`.
- `Math.PI` provides the value of π.
- `results[0]` stores the area.
- `results[1]` stores the circumference.
- The method is `void`, so it does not return a value using `return`. Instead, it places both calculated results in the array supplied by `main()`.
- `main()` can access the two results after the method call.

**Important Java concept:** A Java method cannot directly return two separate primitive values. An array is one way to make multiple calculated values available to the calling method.

### (h) Define a static method that generates random numbers within 0–10. The method will return the first random number that is generated twice.

**Answer**

```java
public static int firstRepeatedRandomNumber() {
    boolean[] seen = new boolean[11];

    while (true) {
        int number = (int) (Math.random() * 11);

        if (seen[number]) {
            return number;
        }

        seen[number] = true;
    }
}
```

**Explanation**

- `Math.random() * 11`, converted to `int`, generates an integer from `0` to `10`, inclusive.
- `seen` is a boolean array with 11 elements. Each index represents one possible random number.
- Initially, every element is `false`, meaning that no number has been generated yet.
- The `while (true)` loop keeps generating random numbers.
- `seen[number]` checks whether the generated number has appeared before.
- If it is already `true`, the number has been generated previously, so the method returns it.
- Otherwise, we set `seen[number] = true` to record that the number has appeared.

**Example call**

```java
int repeated = firstRepeatedRandomNumber();
System.out.println("First repeated number: " + repeated);
```

The exact result changes each time the program runs.

---

## Question 2

### Write a program that consists of a method that can display three numbers in decreasing order.

**Answer**

```java
import java.util.Scanner;

public class DecreasingOrder {

    public static void displayDescending(int a, int b, int c) {
        int temp;

        if (a < b) {
            temp = a;
            a = b;
            b = temp;
        }

        if (a < c) {
            temp = a;
            a = c;
            c = temp;
        }

        if (b < c) {
            temp = b;
            b = c;
            c = temp;
        }

        System.out.println("Numbers in decreasing order: " + a + " " + b + " " + c);
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter three numbers: ");
        int num1 = input.nextInt();
        int num2 = input.nextInt();
        int num3 = input.nextInt();

        displayDescending(num1, num2, num3);

        input.close();
    }
}
```

**Explanation**

- `displayDescending()` is a static method that receives three integers.
- `temp` is a temporary variable used when swapping two values.
- The first `if` statement ensures that `a` is not smaller than `b`.
- The second `if` statement ensures that `a` is not smaller than `c`. Therefore, `a` becomes the largest number.
- The third `if` statement ensures that `b` is not smaller than `c`.
- After these three comparisons, the values are arranged in decreasing order: `a >= b >= c`.
- Finally, the method displays the three numbers.
- In `main()`, `Scanner` reads three integers from the user and passes them to `displayDescending()`.

**Example run**

```text
Enter three numbers: 12 35 8
Numbers in decreasing order: 35 12 8
```

The method also works when some or all of the numbers are equal.

---

## Summary of Methods Used

| Question | Method name | Return type | Main concept |
|---|---|---|---|
| 1(a) | `maximum()` | `int` | Finding the maximum |
| 1(b) | `isSquare()` | `boolean` | Square-number checking |
| 1(c) | `factorial()`, `combination()` | `long` | Method reuse and factorial |
| 1(d) | `isPentagonal()` | `boolean` | Formula and repetition |
| 1(e) | `countLettersAndDigits()` | `void` | String traversal and character checking |
| 1(f) | `generateRandomNumbers()` | `void` | Arrays as method parameters |
| 1(g) | `calculateCircle()` | `void` | Passing an array to store multiple results |
| 1(h) | `firstRepeatedRandomNumber()` | `int` | Random numbers and boolean arrays |
| 2 | `displayDescending()` | `void` | Methods, selection and swapping |
