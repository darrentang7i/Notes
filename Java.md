# Java
- Everything is passed by reference into functions (all objects are accessed and passed by reference)
- Arrays are objects in Java
- Java does not have pointers

## Error Handling
In C, we commonly return a special value, or maybe the function does not actually indicate whether an error occured
- Java, on the other hand uses exceptions to deal with errors. A method is declared with the types of exception or error conditions its likely to produce

```Java
public void operateOnFile(File f) throws IOException {
  ...
}

try {
  operateOnFile(f);
} catch (IOException ioe) {
  warnUser("An error occurred: " + ioe.getMessage());
}
```

- Then, we can catch the exception if it is thrown by the method

## Java Basics
- Every line of code that runs in Java must be inside a class. A class name always starts with an uppercase first letter.
- The name of the java file must match the class name
- main() method exists in every java program
- `println()` method used to print a line of text to the screen 

```Java
public static void main(String[] args) {
    System.out.println("Hello World");
}
```

- single line comments with `//`, multi line with `/* comments */`
- variable types include : String, int, float, char, boolean
- const variables: use keyword `final`

```Java
int myNum = 5;               // Integer (whole number)
float myFloatNum = 5.99f;    // Floating point number
char myLetter = 'D';         // Character
boolean myBool = true;       // Boolean
String myText = "Hello";     // String
```

- A float can use scientific notation ( ie. `float f1 = 35e3f; //gives 35000.0`)

## Strings
- length of a string can be found with the `.length()` method

```Java
String txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
System.out.println("The length of the txt string is: " + txt.length());
```

Some other methods include

```Java
//CONVERT TO UPPER/LOWER CASE
String txt = "Hello World";
System.out.println(txt.toUpperCase());   // Outputs "HELLO WORLD"
System.out.println(txt.toLowerCase());   // Outputs "hello world"

//FIND A CHAR w/ indexOf()
String txt = "Please locate where 'locate' occurs!";
System.out.println(txt.indexOf("locate")); // Outputs 7
```

## Math
- `Math.max(x, y)` finds highest value between x and y
- `Math.min(x, y)` finds lowest value between x and y
- `Math.sqrt(x)` returns sqrt of x
- `Math.abs(x)` returns abs value of x
- `Math.random()` returns random number between 0.0 (inclusive) and 1.0 (exclusive)

## For-each
Used to loop through elements in an array

```Java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
for (String i : cars) {
    System.out.println(i);
}
```

## Arrays
```Java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
System.out.println(cars.length); //outputs 4

//loop through cars array
for (int i = 0; i < cars.length; i++) {
  System.out.println(cars[i]);
}

int[] myNum = {10, 20, 30, 40};

```

## Methods
- Methods must be declared within a class

```Java
public class Main {
    static void myMethod() {
        // code to be executed
  }
}
```
- static means that the method belongs to the Main class, and not an object of the main class

Parameters of functions must be type defined, ie.

```Java
public class Main {
    static void myMethod(String fname, int age) {
        System.out.println(fname + " is " + age);
    }

    public static void main(String[] args) {
        myMethod("Liam", 5);
        myMethod("Jenny", 8);
        myMethod("Anja", 31);
    }
}

```

## Method Overloading
Java supports method overloading, ie. multiple methods can have the same name as long as the number and/or type of params are different

```Java
static int plusMethod(int x, int y) {
  return x + y;
}

static double plusMethod(double x, double y) {
  return x + y;
}
public static void main(String[] args) {
  int myNum1 = plusMethod(8, 5);
  double myNum2 = plusMethod(4.3, 6.26);
}

```

## OOP
Creating a class "Main" and creating an object called "myObj":
```Java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
 
```

- We can create an object of a classs and access it in another class.
- In the above example, `x` is an attribute, aka a field of the class
- We can access fields with the dot syntax (ie. myObj.x)

Java programs have either `static` or `public` attributes and methods. 
- `static` methods can be accessed without creating an object of the class
- `public` methods can only be accessed by objects 

```Java
public class Main {
  // Static method
  static void myStaticMethod() {
    System.out.println("Static methods can be called without creating objects");
  }

  // Public method
  public void myPublicMethod() {
    System.out.println("Public methods must be called by creating objects");
  }

  // Main method
  public static void main(String[] args) {
    myStaticMethod(); // Call the static method
    // myPublicMethod(); This would compile an error

    Main myObj = new Main(); // Create an object of Main
    myObj.myPublicMethod(); // Call the public method on the object
  }
}
```

Constructor
```Java
public class Main {
  int x;

  public Main(int y) {
    x = y;
  }

  public static void main(String[] args) {
    Main myObj = new Main(5);
    System.out.println(myObj.x);
  }
}
// Outputs 5
```

- Of course, the constructor name must match the class name, and it cannot have a return type (not even void). 

Access Modifiers
- For classes, we have `public` or default. `public` means the class is accessible for all classes, default (the default modifier, when u dont specify) means this class is only accessible by classes in the same package 
- For attributes, methods, and constructors, we have `public`, `private`, default, `protected`. 
    - `public`: accessible for all classes,
    - `private`: accessible within the declared class
    -  default: accessible in the same package
    -  `protected`: accessible in the same package and subclasses

Non Access Modifiers
- For classes, there is `final` or `abstract`. `final`: class cannot be inherited by other classes. `abstract`: class cannot be used to create objects, to access an abstract class, it must be inherited from another class
- For attributes and methods, there is `final`, `static`, `abstract`, `transient`, `synchronized`, `volatile`
    - `final`: attributes & methods cannot be overridden/modified
    - `static`: Attributes and methods belongs to the class, rather than an object
    - `abstract`: can only be used in an abstract class, and can only be used on methods. 
    - `transient`: attributes and methods are skipped when serializing the object contaaining them
    - `synchronized`: methods can only be accessed by one thread at a time
    - `volatile`: value of an attribute is not cached thread-locally, and is always read from main memory

An abstract method belongs to an abstract class, and it does not have a body. The body (function definition) is provided by the subclass

## Packages
A package in Java is used to group related classes (kinda like a folder in a file directory)
- The Java API is a library of prewritten classes. The library is divided into packages and classes, meaning u can import a single class, or a whole package containing many classes

```Java
import package.name.Class;   // Import a single class
import package.name.*;   // Import the whole package
```

Here is a example with the Scanner class, showing how to get user input

```Java 
import java.util.Scanner; //java.util is a package, and Scanner is a class in the package which is used to get user input
//import java.util.*        this will import the entire package

class MyClass {
  public static void main(String[] args) {
    Scanner myObj = new Scanner(System.in);
    System.out.println("Enter username");

    String userName = myObj.nextLine();
    System.out.println("Username is: " + userName);
  }
}
```

You can also create your own packages

## Inheritance
```Java
class Vehicle {
  protected String brand = "Ford";        // Vehicle attribute
  public void honk() {                    // Vehicle method
    System.out.println("Tuut, tuut!");
  }
}

class Car extends Vehicle {
  private String modelName = "Mustang";    // Car attribute
  public static void main(String[] args) {

    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (from the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand attribute (from the Vehicle class) and the value of the modelName from the Car class
    System.out.println(myCar.brand + " " + myCar.modelName);
  }
}

```

Note: since brand is a protected string in Vehicle, Car is able to access it. If it was set to private, the Car class is not able to access.

If you do not want other classes to inherit from a class, use the final keyword:
```Java
final class Vehicle {
  ...
}
```

An error will be generated if any class tries to inherit from Vehicle.

## Polymorphism
Polymorphism uses inherited methods to perform different tasks. It allows us to perform a single action in different ways

```Java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}
```
## Inner Classes
In Java, it is possible to nest classes. The purpose of nested classes is to group classes that belong together
- To access the inner class, create an object of the outer class, and then create an object of the inner class

```Java
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}

// Outputs 15 (5 + 10)
```

- An inner class can be private or protected. If you don't want outside objects to access the inner class, declare the class as `private`
- An inner class can also be static, which means you can access it without creating an object of the outer class

```Java
public class Main {
  public static void main(String[] args) {
    OuterClass.InnerClass myInner = new OuterClass.InnerClass();
    System.out.println(myInner.y);
  }
}
// Outputs 5
```
Note: just like static attributes and methods, a static inner class doesn't have access to members of the outer class

Inner classes can access attributes and methods of the outer class

## Abstraction
Data abstraction is the process of hiding certain details and showing only essential info to the user. Can be achieved with abstract cclasses or interfaces.

`abstract` keyword is a non-access modifier, used for classes and methods
- Abstract class: a restricted class, cannot be used to create objects (to access it, must be inherited from another class), in other words, u must create an object of an inherited class
- Abstract method: can only be used in an abstract class, does not have a body. Body is provided by the subclass.

```Java
abstract class Animal {
  public abstract void animalSound();
  public void sleep() {
    System.out.println("Zzz");
  }
}

// Subclass (inherit from Animal)
class Pig extends Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
}

class Main {
  public static void main(String[] args) {
    Animal myObj = new Animal(); // will generate an error

    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}


```

## Interfaces
Interfaces are another way to achieve abstraction in Java. An `interface` is a completely "abstract class", used to group related methods with empty bodies

To access the interface methods, the interface must be "implemented" (similar to inherited) by another class with the `implements` keyword (instead of `extends`). The body of the interface method is provided by the "implement" class

```Java
// Interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```
- Interfaces cannot be used to create objects (similar to abstract classes)
- When implementing an interface, you must override all of its methods
- Interface methods are by default `abstract` and `public`
- Interface attributed are by default `public`, `static` and `final`
- Interfaces have no constructors

When do we use interfaces?
1) For security. Hide certain details and show only important details of an object
2) A class cannot inherit from multiple superclasses. However, a class can implement multiple interfaces. To implement multiple interfaces, separate them with a comma

```Java
class DemoClass implements FirstInterface, SecondInterface {

}
```
## Enums
An enum is a special "class" representing a group of constants.

```Java
enum Level {
  LOW,
  MEDIUM,
  HIGH
}
Level myVar = Level.MEDIUM;

//loop through enum
for (Level myVar : Level.values()) {
  System.out.println(myVar);
}
```

An enum can have attributes and methods, but enum constants are `public`, `static` and `final`. enums cannot create objects, cannot extend other classes, but can implement interfaces

## ArrayList
Used in the same places u would use a vector in cpp. 
- ArrayList implementation has a regular array inside it. If array is not large enough, a new larger array is created to replace the old one.

The ArrayList class is a resizable array, found in the java.util package.

```Java
import java.util.ArrayList; 
import java.util.Collections;  // Import the Collections class

public class Main {
  public static void main(String[] args) {
    ArrayList<String> cars = new ArrayList<String>();   //create ArrayList called cars
    cars.add("Volvo");     //add element to array list
    cars.add("BMW");
    cars.get(0);           //accesses 0th index, so returns "volvo"
    cars.set(0, "Opel");   //sets 0th index to "Opel"
    cars.remove(0);        //removes 0th index
    cars.clear();          // removes all elements in the ArrayList
    cars.size();           // returns number of elements in the Arraylist

    Collections.sort(cars);  // Sort cars

    System.out.println(cars);
  }
}
```

## LinkedList 

The `LinkedList` class is almost identical to the `ArrayList`

Methods include: 
- `addFirst()`
- `addLast()`
- `removeFirst()`
- `removeLast()`
- `getFirst()`
- `getLast()`

## HashMap
```Java
// Import the HashMap class
import java.util.HashMap;

public class Main {
  public static void main(String[] args) {
    // Create a HashMap object called capitalCities
    HashMap<String, String> capitalCities = new HashMap<String, String>();

    // Add keys and values (Country, City)
    capitalCities.put("England", "London");
    capitalCities.get("England");             //access value in hash map
    capitalCities.remove("England");          //remove key, value pair with England as the key
    capitalCities.clear();                    //remove all items from hash table
    capitalCities.size();                     //returns number of items in hash table

    // Print keys
    for (String i : capitalCities.keySet()) {
      System.out.println(i);
    }

    // Print values
    for (String i : capitalCities.values()) {
      System.out.println(i);
    }

    // Print keys and values
    for (String i : capitalCities.keySet()) {
      System.out.println("key: " + i + " value: " + capitalCities.get(i));
    }



    System.out.println(capitalCities);
  }
}
```

## HashSet
Implements a set, using a hashmap. It is a collection of items, where every item is unique

```Java
import java.util.HashSet; // Import the HashSet class

HashSet<String> cars = new HashSet<String>();
```

## Iterator 
An `Iterator` is an object that can be used to loop through collections, like ArrayList and HashSet.

```Java
import java.util.ArrayList;
import java.util.Iterator;

public class Main {
  public static void main(String[] args) {
  
    // Make a collection
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
  
    // Get the iterator
    Iterator<String> it = cars.iterator();
    
    // Loop through a collection
    while(it.hasNext()) {
      System.out.println(it.next());
    }
  }
}

```

## Java Wrapper Classes
Wrapper classes provide a way to use primitive data types (int, boolean, etc.) as objects

Primitive Data Type, Wrapper Class
- byte, Byte
- short, Short
- int, Integer
- long, Long
- float, Float
- double, Double
- boolean, Boolean
- car, Character

Sometimes u must use wrapper classes, for example when working with Collection objects, such as ArrayList, where primitive types cannot be used (the list can only store objects)

```Java
ArrayList<int> myNumbers = new ArrayList<int>(); // Invalid
ArrayList<Integer> myNumbers = new ArrayList<Integer>(); // Valid
```

## Exceptions
```Java
try {
  //  Block of code to try
}
catch(Exception e) {
  //  Block of code to handle errors
}
finally {

}
```
The `finally` statement lets you execute code, after `try...catch`, regardless of the result