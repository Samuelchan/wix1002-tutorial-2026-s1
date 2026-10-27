# Tutorial 03 — Answers

## Question 1

### a. Determine whether 3x8=27

```java
if (3 * 8 == 27)
    System.out.println("Correct");
else
    System.out.println("Incorrect");
```

```text
Incorrect
```

### b. Determine whether an input integer is odd or even

```java
import java.util.Scanner;

Scanner input = new Scanner(System.in);
System.out.print("Enter an integer: ");
int number = input.nextInt();

if (number % 2 == 0)
    System.out.println("Even number");
else
    System.out.println("Odd number");
```

### c. Determine whether a character is a capital letter

```java
char ch = 'A';

if (ch >= 'A' && ch <= 'Z')
    System.out.println(ch + " is a capital letter");
else
    System.out.println(ch + " is not a capital letter");
```

Alternative using a built-in method: `Character.isUpperCase(ch)`.

### d. Display two strings in alphabetical order ignoring case

```java
String str1 = "banana";
String str2 = "Apple";

if (str1.compareToIgnoreCase(str2) < 0)
    System.out.println(str1 + " " + str2);
else
    System.out.println(str2 + " " + str1);
```

```text
Apple banana
```

### e. Switch statement for days of the week

```java
int day = 3;

switch (day) {
    case 0:
        System.out.println("Sunday");
        break;
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    case 4:
        System.out.println("Thursday");
        break;
    case 5:
        System.out.println("Friday");
        break;
    case 6:
        System.out.println("Saturday");
        break;
    default:
        System.out.println("Invalid input");
}
```

## Question 2

### a.

```java
if (num1 == num2)
    System.out.println("Number 1 is equal to number 2.");
```

`=` is assignment. `==` is used to compare values.

### b.

```java
if (x > y && x > z)
    System.out.println("x is the largest number");
```

Java cannot chain comparisons like `x > y > z`. Each comparison must be written separately and joined with `&&`.

### c.

```java
String s1 = "Java", s2 = "Java";

if (s1.equals(s2))
    System.out.println("They are equal strings.");
else
    System.out.println("They are not equal strings.");
```

- Strings are compared with `equals()`, not `==`, because `==` compares references.
- `else` does not take a condition.
- The variables must be initialized before use.

### d.

```java
if (x > 0 || y > 0)
    System.out.println("Either x or y is positive");
```

The condition needs parentheses, `or` is written `||`, and the `;` after the condition must be removed.

## Question 3

For all parts, x = 9 and y = 10.

### a.

```text
#####
$$$$$
```

`x < 10` is true and `y > 10` is false, so the `else` prints `#####`. The last statement is outside the `if`, so `$$$$$` always prints.

### b.

```text
#####
$$$$$
```

`x < 10` is true and `y < 10` is false, so the `else` block prints both lines.

### c.

```text
#####
```

`y < 10` is false, so `*****` is skipped. `#####` is inside the outer `if` block, so it prints. The `else` is not executed.

### d.

```text
(no output)
```

`x > 10` is false, so nothing inside the block runs.

## Question 4

```java
import java.util.Scanner;

public class BiggestNumber {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter first integer: ");
        int a = input.nextInt();
        System.out.print("Enter second integer: ");
        int b = input.nextInt();
        System.out.print("Enter third integer: ");
        int c = input.nextInt();

        int biggest;

        if (a >= b && a >= c)
            biggest = a;
        else if (b >= a && b >= c)
            biggest = b;
        else
            biggest = c;

        System.out.println("The biggest number is " + biggest);
    }
}
```

```text
Enter first integer: 12
Enter second integer: 45
Enter third integer: 30
The biggest number is 45
```

Using `>=` means the program still gives the right answer when two or more numbers are equal.

## Question 5

```java
import java.util.Scanner;

public class LeapYear {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter year: ");
        int year = input.nextInt();

        if ((year % 4 == 0 && year % 100 != 0) || year % 400 == 0)
            System.out.println(year + " is a leap year.");
        else
            System.out.println(year + " is not a leap year.");
    }
}
```

```text
Enter year: 2024
2024 is a leap year.

Enter year: 1900
1900 is not a leap year.

Enter year: 2000
2000 is a leap year.
```