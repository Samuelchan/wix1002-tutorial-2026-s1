# Tutorial 06 — Java Methods

## Question 1

### (a)

```java
public static int maximum(int a, int b, int c) {
    int max = a;

    if (b > max) {
        max = b;
    }

    if (c > max) {
        max = c;
    }

    return max;
}
```

### (b)

```java
public static boolean isSquare(int number) {
    if (number < 0) {
        return false;
    }

    int root = (int) Math.sqrt(number);
    return root * root == number;
}
```

### (c)

```java
public static long factorial(int number) {
    long result = 1;

    for (int i = 1; i <= number; i++) {
        result *= i;
    }

    return result;
}

public static long combination(int n, int k) {
    return factorial(n) / (factorial(k) * factorial(n - k));
}
```

### (d)

```java
public static boolean isPentagonal(int number) {
    if (number < 1) {
        return false;
    }

    int n = 1;

    while (n * (3 * n - 1) / 2 < number) {
        n++;
    }

    return n * (3 * n - 1) / 2 == number;
}
```

### (e)

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

### (f)

```java
public static void generateRandomNumbers(int[] numbers) {
    for (int i = 0; i < numbers.length; i++) {
        numbers[i] = (int) (Math.random() * 101);
    }
}
```

Example use in `main()`:

```java
public static void main(String[] args) {
    int[] numbers = new int[10];

    generateRandomNumbers(numbers);

    for (int i = 0; i < numbers.length; i++) {
        System.out.println(numbers[i]);
    }
}
```

### (g)

```java
public static void calculateCircle(double radius, double[] results) {
    results[0] = Math.PI * radius * radius;
    results[1] = 2 * Math.PI * radius;
}
```

Example use in `main()`:

```java
public static void main(String[] args) {
    double[] results = new double[2];

    calculateCircle(5, results);

    System.out.println("Area: " + results[0]);
    System.out.println("Circumference: " + results[1]);
}
```

### (h)

```java
public static int firstRepeatedRandomNumber() {
    boolean[] generated = new boolean[11];

    while (true) {
        int number = (int) (Math.random() * 11);

        if (generated[number]) {
            return number;
        }

        generated[number] = true;
    }
}
```

## Question 2

```java
import java.util.Scanner;

public class DecreasingOrder {

    public static void displayDecreasing(int a, int b, int c) {
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

        System.out.println(a + " " + b + " " + c);
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Enter three numbers: ");
        int num1 = input.nextInt();
        int num2 = input.nextInt();
        int num3 = input.nextInt();

        displayDecreasing(num1, num2, num3);

        input.close();
    }
}
```
