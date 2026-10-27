# Tutorial 04 — Answers

## Question 1

### a. Largest integer n so that n³ is less than 2000

```java
int n = 1;

while ((n + 1) * (n + 1) * (n + 1) < 2000)
    n++;

System.out.println("The largest n where n^3 < 2000 is " + n);
```

```text
The largest n where n^3 < 2000 is 12
```

12³ = 1728 is less than 2000, but 13³ = 2197 is not.

### b. Square of the first twelve integers

```java
for (int i = 1; i <= 12; i++) {
    System.out.println("Square of " + i + " = " + (i * i));
}
```

### c. 4-by-5 matrix of random numbers from 0 to 100

```java
import java.util.Random;

public class RandomMatrix {
    public static void main(String[] args) {
        Random rand = new Random();

        for (int row = 1; row <= 4; row++) {
            for (int col = 1; col <= 5; col++) {
                System.out.print(rand.nextInt(101) + " ");
            }
            System.out.println();
        }
    }
}
```

Sample output (values change on every run):

```text
45 7 98 23 100
0 62 31 77 14
88 53 9 41 66
72 19 85 3 50
```

`nextInt(101)` returns a value from 0 to 100 inclusive.

### d. Sum of numbers from 1 to a given number

```java
import java.util.Scanner;

public class SumToN {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int n = input.nextInt();

        int total = 0;
        for (int i = 1; i <= n; i++) {
            total += i;
        }

        System.out.println("Sum of 1 to " + n + " = " + total);
    }
}
```

```text
Enter a number: 10
Sum of 1 to 10 = 55
```

### e. Sum of the series 1/25 + 2/24 + 3/23 + ... + 25/1

```java
double total = 0;

for (int i = 1; i <= 25; i++) {
    total += (double) i / (26 - i);
}

System.out.printf("Sum of the series = %.2f%n", total);
```

```text
Sum of the series = 74.21
```

The numerator goes from 1 to 25 and the denominator from 25 to 1, so the denominator is `26 - i`. The cast to `double` is needed to avoid integer division.

## Question 2

### a.

```java
int sum = 0;
for (int x = 10; x > 0; x--)
    sum += x;
```

`x++` makes `x` grow forever, so the condition `x > 0` is never false. It must be `x--`. `sum` also needs to be declared and initialized.

### b.

```java
int x = 0, y = 0;

do {
    x += 2;
    y += x;
    System.out.println(x + " and " + y);
} while (x < 100);
```

- The loop body has more than one statement, so it needs braces `{ }`.
- A `do-while` must end with a semicolon after the condition.
- `x` and `y` must be declared and initialized before the loop.

### c.

```java
for (int x = 1, y = 20; x < y; x++, y -= 2) {
    System.out.println(x + " " + y);
}
```

- The initialization uses `=`, not `==`.
- The parts of a `for` header are separated by `;`. The `,` is only used to separate several expressions within one part.
- The `;` after the `for (...)` creates an empty loop body.
- `&` is not how Java joins strings. It should be `+`.

### d.

```java
int i = 1;
while (i <= 10) {
    if (i == 10)
        System.out.println("Program End");
    i++;
}
```

`i` is never changed in the original, so the loop never ends. The condition `i < 10` also means `i == 10` can never be true. The fix is to declare `i`, use `i <= 10`, and put `i++` inside the loop body but outside the `if`.

## Question 3

```java
public class Fibonacci {
    public static void main(String[] args) {
        int f1 = 1, f2 = 1;

        System.out.print("First 10 Fibonacci numbers: ");
        System.out.print(f1 + " " + f2 + " ");

        for (int i = 3; i <= 10; i++) {
            int fn = f1 + f2;
            System.out.print(fn + " ");
            f1 = f2;
            f2 = fn;
        }
    }
}
```

```text
First 10 Fibonacci numbers: 1 1 2 3 5 8 13 21 34 55
```

## Question 4

```java
import java.util.Scanner;

public class ReverseString {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String text = input.nextLine();

        System.out.println("Original string: " + text);
        System.out.print("Reversed string: ");

        for (int i = text.length() - 1; i >= 0; i--) {
            System.out.print(text.charAt(i));
        }
        System.out.println();
    }
}
```

```text
Enter a string: Hello
Original string: Hello
Reversed string: olleH
```