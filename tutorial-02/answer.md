# Tutorial 02 — Answers

## Question 1

### a. In one line using multiple Java statements

```java
System.out.print("Faculty ");
System.out.print("of ");
System.out.print("Computer Science ");
System.out.print("and ");
System.out.print("Information Technology.");
```

### b. In multiple lines using one Java statement

```java
System.out.println("Faculty of\nComputer Science\nand Information\nTechnology.");
```

## Question 2

```java
System.out.println("\"SDN\" - Software-defined networking");
```

## Question 3

### a.

```java
System.out.println("Java Programming");
```

`println` must be all lowercase because Java is case sensitive.

### b.

```java
System.out.println("Introduction to Java!");
```

Output uses `System.out`, not `System.in`, and the statement needs a semicolon.

### c.

```java
System.out.println("\\t is the horizontal tab character");
```

`\\` prints a literal backslash, so `\t` appears as text instead of acting as a tab.

### d.

```java
System.out.println("Java is case sensitive!");
```

`System` must start with a capital S.

## Question 4

### a.

```java
String matricNumber;
```

### b.

```java
double pi;
```

### c.

```java
boolean M = false;
```

### d.

```java
long P = 8800000000L;
```

### e.

```java
char letter = 'U';
```

### f.

```java
final String PRO = "Java";
```

## Question 5

### a.

```java
double amount = 32.5;
amount += 10;
System.out.println("The amount is " + amount);
```

A `double` cannot hold the String `"32.5"`, and a `final` variable cannot be changed with `+=`.

### b.

```java
String chapter = "Summary";
System.out.println(chapter);
```

The type is `String` (capital S), and strings use double quotes.

### c.

```java
int num = 0;
++num;
int num1 = num;
```

`num` must be initialized, `++num++` is invalid, and `num1` must be declared.

### d.

```java
int num = 3000;
System.out.printf("%d\n", num);
```

`%d` is for integers. `%f` only works with floating-point values.

### e.

```java
import java.util.Scanner;

String contact;
Scanner keyboard = new Scanner(System.in);
contact = keyboard.nextLine();
```

Keyboard input uses `System.in`, and `Scanner` must be imported.

## Question 6

```java
import java.util.Scanner;

public class CircleCircumference {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        double diameter, circumference;

        System.out.print("Enter diameter: ");
        diameter = input.nextDouble();

        circumference = Math.PI * diameter;

        System.out.printf("The circumference of the circle is: %.3f%n", circumference);
    }
}
```

```text
Enter diameter: 11.8
The circumference of the circle is: 37.071
```

## Question 7

```java
import java.util.Scanner;

public class InchToMeter {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        double inch, meter;

        System.out.print("Enter value in inch: ");
        inch = input.nextDouble();

        meter = inch * 2.54 / 100;

        System.out.printf("%.2f inches = %.2f meters%n", inch, meter);
    }
}
```

```text
Enter value in inch: 20.17
20.17 inches = 0.51 meters
```