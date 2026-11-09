# Tutorial 05 — Answers

## Question 1

### a. Array to store 12 floating point numbers

```java
double[] numbers = new double[12];
```

### b. Array initialized with the values A to E

```java
char[] letters = {'A', 'B', 'C', 'D', 'E'};
```

### c. Array to store 100 students' names

```java
String[] studentNames = new String[100];
```

### d. Table with 6 rows and 2 columns of integers

```java
int[][] table = new int[6][2];
```

### e. Initialize the array with the given values

```java
int[][] matrix = {
    {6, 9},
    {2, 5},
    {4, 6}
};
```

### f. Modify the array to the new values

```java
matrix[1][1] = 4;
matrix[2][0] = 3;
matrix[2][1] = 7;
```

Only three elements change. The first row (6, 9) and `matrix[1][0]` (2) stay the same. The array now holds:

```text
6 9
2 4
3 7
```

### g. Display all values of the array `contact` in separate lines

```java
for (int i = 0; i < contact.length; i++) {
    System.out.println(contact[i]);
}
```

## Question 2

### a.

```java
String[] code = {"AAA", "AAB", "AAC", "AAD"};
```

Strings use double quotes. Single quotes are only for a single `char`.

### b.

```java
int[] num = new int[10];
int sum = 0;

for (int k = 0; k < num.length; k++)
    sum += num[k];
```

- The array type is `int`, so it must be `new int[10]`, not `new num[10]`.
- `length` is a field of an array, so it is written without brackets: `num.length`.
- The condition `k <= num.length` goes one position past the end, so it must be `k < num.length`.
- `sum` was never declared.
- `sum += num` must add one element, `num[k]`, not the whole array.

### c.

```java
int[][] t = new int[3][];
t[1] = new int[3];
t[1][2] = 5;
```

Only the number of rows was created. Each row is still `null`, so `t[1][2] = 5` would cause a `NullPointerException`. Row 1 must be created first with `t[1] = new int[3]`.

### d.

```java
int i = 4;
int[] score = new int[5];
score[1] = 78;
score[i] = 100;
```

`score[++i]` increases `i` to 5 before it is used. The array has 5 elements, so the valid indexes are 0 to 4, and index 5 causes an `ArrayIndexOutOfBoundsException`. Using `score[i]` accesses index 4, which is valid.

## Question 3

```java
int[] marks = new int[5];
int i = 0, j = 1;

marks[i] = 12;                  // marks[0] = 12
marks[j] = marks[i] + 19;       // marks[1] = 12 + 19 = 31
marks[j-1] = marks[j] * marks[j]; // marks[0] = 31 * 31 = 961
marks[j*3] = marks[i+1];        // marks[3] = marks[1] = 31
marks[++j] = marks[i] % 5;      // j = 2, marks[2] = 961 % 5 = 1
marks[2*j] = marks[j-1];        // marks[4] = marks[1] = 31
```

| Index | 0 | 1 | 2 | 3 | 4 |
|-------|-----|----|---|----|----|
| Value | 961 | 31 | 1 | 31 | 31 |

## Question 4

```java
public class CountThe {
    public static void main(String[] args) {
        String[] sentence = {"the", "cat", "sat", "on", "the", "mat", "The", "end"};
        int count = 0;

        for (int i = 0; i < sentence.length; i++) {
            if (sentence[i].equals("the"))
                count++;
        }

        System.out.println("The word \"the\" occurs " + count + " time(s).");
    }
}
```

```text
The word "the" occurs 2 time(s).
```

`equals()` is case sensitive, so `"The"` is not counted.

## Question 5

```java
public class ReverseSentence {
    public static void main(String[] args) {
        String[] sentence = {"Java", "is", "fun", "to", "learn"};

        for (int i = sentence.length - 1; i >= 0; i--) {
            String word = sentence[i];

            for (int j = word.length() - 1; j >= 0; j--) {
                System.out.print(word.charAt(j));
            }
            System.out.print(" ");
        }
        System.out.println();
    }
}
```

```text
nrael ot nuf si avaJ
```

The outer loop goes through the array from the last element to the first. The inner loop prints each string from its last character to its first.

## Question 6

```java
import java.util.Random;

public class RandomBinary {
    public static void main(String[] args) {
        Random rand = new Random();
        int number = rand.nextInt(256);
        int original = number;

        int[] bits = new int[8];

        for (int i = 7; i >= 0; i--) {
            bits[i] = number % 2;
            number = number / 2;
        }

        System.out.println("Random number: " + original);
        System.out.print("Binary: ");
        for (int i = 0; i < bits.length; i++) {
            System.out.print(bits[i]);
        }
        System.out.println();
    }
}
```

Sample output (changes on every run):

```text
Random number: 173
Binary: 10101101
```

`nextInt(256)` gives 0 to 255. The loop fills the array from the last position backwards, so the least significant bit ends up at index 7. Any unused leading positions stay 0, which keeps the number 8 bits long.