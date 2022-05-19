# [CSAIA](https://introcs.cs.princeton.edu/java/code/)
Computer Science: An Interdisciplinary Approach from Princeton 

## Intro to Programming 
### 1.1 Elements of Programming 

**build-in types**: ```int, long, double, char, String, boolean```   
**operations on numeric**: ```+, -, *, /, %, ++, --```     
**String Operations**: ```+, " ", length(), charAt(), compareTo(), matches()```    
**assignment**: ```= ```    
**object oriented**: ```static, class, public, private, new, final, toString(), main()```   
**Math Methods**: ```Math.sin(), Math.cos(), Math.log(), Math.exp(), Math.pow(), Math.sqrt(), Math.min(), Math.max(), Math.abs(). Math.PI```    
**System methods**: ```System.print(), System.println(), System.printf()```   
**punctuation**: ```{ }, ( ), ;```   
**comparisions**: ```<, <=, >, >=, ==, !=```   
**Boolean operations**: ```true, false, !, &&, ||```   
**arrays**: ```a[], length, new```   
**type conversion methods**: ```Integer.parseInt(), Double.parseDouble()```    
**ourStd methods**: ```StdIn.read*(), StdOut.print*(), StdDraw.*(), StdAudio.*(), StdRandom.*()```


**1.1.1 HelloWorld.java** 
```Java
// text file named HelloWorld.java 
// HelloWorld: program name 
public class HelloWorld {
   public static void main(String[] args) { // main() method
      // Prints "Hello, World" in the terminal window.
      System.out.println("Hello, World"); // body of main(), a single statement
   }
}
```

#### Errors 
* *Compile-time error*    
These errors are caught by the system when we compile the program, because they prevent the compiler from doing the translation (so it issues an error message that tries to explain why).
* *Run-time errors*    
when we execute the program, because the program tries to perform an invalid operation (e.g., division by zero).
* *Logical errors*    
it produces the wrong answer

**1.1.2 Use Argument.java**
```Java
public class UseArgument {
   public static void main(String[] args) {
      System.out.println("Hi,");
      System.out.println(args[0]);
      System.out.println(". How are you?");
   }
}
```

#### Exercise 

**1.1.3 HelloTenWorld.java**

Write a program TenHelloWorlds.java that prints "Hello, World" ten times.
```Java 
public class TenHelloWorlds {

    public static void main(String[] args) {
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
        System.out.println("Hello, World");
    }

}
```

### 1.2 Build-in Datatypes 

A *data type* is a set of values and a set of operations defined on them. 
```
int: integers -- whole number between  −2^31 and 2^31 − 1 
double: floating-point numbers 
boolean: boolean values -- true or false
char: characters -- an alphanumeric character or symbol, usually assigning values 
String: sequences of characters, concatenation 串联,  
```
**1.2.1 Ruler.java**
```Java 
public class Ruler {
    public static void main(String[] args) {
        String ruler1 = "1";
        String ruler2 = ruler1 + "2" + ruler1;
        String ruler3 = ruler2 + "3" + ruler2;
        String ruler4 = ruler3 + "4" + ruler3;
        String ruler5 = ruler4 + "5" + ruler4;
        
        System.out.println(ruler1);
        System.out.println(ruler2);
        System.out.println(ruler3);
        System.out.println(ruler4);
        System.out.println(ruler5);
    }
}

Output: 
1121
1213121
121312141213121
1213121412131215121312141213121
```
**1.2.2 IntOps**
```Java 
public class IntOps {
    public static void main(String[] args) {
        int a = Integer.parseInt(args[0]);
        int b = Integer.parseInt(args[1]);
        int sum = a + b; 
        int prod = a * b;
        int quot = a / b; 
        int rem = a % b;
        
        System.out.println(a + " + " + b + " = " + sum);
        System.out.println(a + " * " + b + " = " + prod);
        System.out.println(a + " / " + b + " = " + quot);
        System.out.println(a + " % " + b + " = " + rem);
        System.out.println(a + " = " + quot + " * " + b + " + "+ rem);

    }
}
```
**1.2.3 Quadratic.java**
```Java 
public class Quadratic { 

    public static void main(String[] args) { 
        double b = Double.parseDouble(args[0]);
        double c = Double.parseDouble(args[1]);

        double discriminant = b*b - 4.0*c;
        double sqroot =  Math.sqrt(discriminant);

        double root1 = (-b + sqroot) / 2.0;
        double root2 = (-b - sqroot) / 2.0;

        System.out.println(root1);
        System.out.println(root2);
    }
}
```
#### Boolean 
true or false

* and: a && b is T if a & b are T
* or:  a || b is T if either a or b is T, or both 
* not: !a is T if a is F 
<img src = 'https://user-images.githubusercontent.com/56160038/169400173-188c185d-71e9-469d-b2bc-87cbac06510c.png' height=150 />

#### Comparison
mixed-type operations, take operands of one type and produce a resul of type boolean.     

<img src= 'https://user-images.githubusercontent.com/56160038/169400805-55a0fca8-d01a-4bfe-b587-b5e4d438ce92.png' height=150 />

**1.2.4 LeapYear.java**
```Java 
public class LeapYear {
    public static void main(String[] args) {
        int year = Integer.parseInt(args[0]);
        boolean isLeapYear;
        
        // divisible by 4
        isLeapYear = (year % 4 == 0);
        
        // divisible by 4 and not 100
        isLeapYear = isLeapYear || (year % 100 != 0);
        
        // divisible by 4 and not 100 unless divisible by 400
        isLeapYear = isLeapYear || (year % 400 == 0);
        
        System.out.println(isLeapYear);
    }
}
```

#### Library methods and APIs 

* Printing strings to the terminal window 
<img src='https://user-images.githubusercontent.com/56160038/169402062-633fd929-61bc-4af1-87e6-8f19a48ed23e.png' width=450 />

* Converting strings to primitive types
<img src='https://user-images.githubusercontent.com/56160038/169402130-3b499e95-336d-4bec-8894-eb7f43eebd38.png' width=450 />

* Mathematical functions 
<img src='https://user-images.githubusercontent.com/56160038/169402191-54696198-202d-4b15-945d-33e689a587cd.png' width=450 />

#### Type Conversion 
converting data form one type to another one. 
* Explicit type conversion 
* Automatic type conversion -- for primitive numeric types
```Java
public class RandomInt {
    public static void main(String[] args) {
        // a positive integer
        int n = Integer.parseInt(args[0]);
        
        // a pseudo-random integer between 0.0 and 1.0
        double r = Math.random();
        
        // a pseudo-random integer between 0 and n-1
        int value = (int) (r * n);
        
        System.out.println(value);
    }
}
```
* Automatic conversions for strings 

#### Exercise 
**1.2.6 Distance** 

takes two integer command-line arguments x and y and prints the Euclidean distance from the point (x, y) to the origin (0, 0).
```Java
public class Distance {
    public static void main(String[] args) {
        // parse x- and y-coordinates from command-line arguments
        int x = Integer.parseInt(args[0]);
        int y = Integer.parseInt(args[1]);
        
        // compute distance to (0,0)
        double dist = Math.sqrt(x*x + y*y);
        
        // output distance 
        System.out.println();
    }
}
```
**1.2.7 SumOfTwoDice.java**

prints the sum of two random integers between 1 and 6 
```Java 
public class SumOfTwoDice {
    public static void main(String[] args) {
        int SIDES = 6;
        int a = 1 + (int) (Math.random() * SIDES);
        int b = 1 + (int) (Math.random() * SIDES);
        int sum = a + b;
        System.out.println(sum);
    }
}
```
**1.2.8 SumOfSines**

takes a double command-line argument t (in degrees) and prints the value of sin(2t) + sin(3t).
```java
public class SumOfSines {
    public static void main(String[] args) {
        double degrees = Double.parseDouble(args[0]);
        double radians = Math.toRadians(degrees);
        double sum = Math.sin(2 * radians) + Math.sin(3 * radians);
        System.out.println(sum);
    }
}
```
**1.2.9 SpringSeason.java**

takes two int values m and d from the command line and prints true if day d of month m is between March 20 (m = 3, d =20) and June 20 (m = 6, d = 20), false otherwise.
```Java
public class SpringSeason {
    public static void main(String[] args) {
        int month = Integer.parseInt(args[0]);
        int day = Integer.parseInt(args[1]);
        boolean inSpring = (month == 3 && day >= 20 && day <= 31)
        || (month == 4 && day >= 1 && day <= 30)
        || (month == 5 && day >= 1 && day <= 31)
        || (month == 6 && day >= 1 && day <= 20);
        System.out.println(inSpring);
    }
}
```
**1.2.10 WindChill.java** 

Given the temperature t (in Fahrenheit) and the wind speed v (in miles per hour), the National Weather Service defines the wind chill to be:

```w = 35.74 + 0.6215 t + (0.4275 t - 35.75) v0.16```

takes two double command-line arguments t and v and prints the wind chill.
```Java 
public class WindChill {
    public static void main(String[] args) {
        double t = Double.parseDouble(args[0]);
        double v = Double.parseDouble(args[1]);
        
        double w = 35.74 + 0.6215 * t + (0.4275 * t - 35.75) * Math.pow(v, 0.16);
        System.out.println("temperature = " + t);
        System.out.println("Wind Speed = " + v);
        System.out.println("Wind Chill = " + w);
    }
}
```
**1.2.11 CatesianToPolar.java**

converts from Cartesian to polar coordinates. 
```Java 
public class WindChill {
    public static void main(String[] args) {
        double x = Double.parseDouble(args[0]);
        double y = Double.parseDouble(args[1]);
        
        double r = Math.sqrt(x*x + y*y);
        double theta = Math.atan2(y, x);
        
        System.out.println("r = " + r);
        System.out.println("theta =" + theta);
    }
}
```








