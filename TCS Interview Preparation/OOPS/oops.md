# TCS OOPS Interview Preparation - Complete Question Bank

## 1️⃣ Core OOP Concepts (MUST-ASK)

### What is Object-Oriented Programming?

Object-Oriented Programming (OOP) is a programming paradigm that organizes code around objects and classes rather than functions and logic. It models real-world entities as objects that have:
- **Properties** (attributes/data)
- **Behaviors** (methods/functions)
- **Identity** (unique existence)

### What are the four pillars of OOP?

1. **Encapsulation** - Bundling data and methods together, hiding internal details
2. **Inheritance** - Creating new classes based on existing classes
3. **Polymorphism** - Same interface, different implementations
4. **Abstraction** - Hiding complex implementation details, showing only essential features

### Explain Encapsulation with real example.

Encapsulation is wrapping data and methods together and controlling access to them.

**Real Example: Bank Account**
```java
class BankAccount {
    private double balance;  // Hidden from outside
    
    public void deposit(double amount) {
        if(amount > 0) {
            balance += amount;
        }
    }
    
    public double getBalance() {
        return balance;  // Controlled access
    }
}
```

**Benefits:**
- Data security (balance cannot be directly modified)
- Validation (only positive amounts can be deposited)
- Controlled access through methods

### Explain Abstraction with example.

Abstraction hides complex implementation details and shows only essential features.

**Real Example: Car**
```java
abstract class Car {
    abstract void start();  // How it starts is hidden
    abstract void stop();   // Implementation details hidden
    
    void honk() {           // Common behavior
        System.out.println("Beep!");
    }
}

class PetrolCar extends Car {
    void start() {
        // Complex engine starting process hidden
        System.out.println("Petrol engine started");
    }
    
    void stop() {
        System.out.println("Petrol engine stopped");
    }
}
```

### Difference between abstraction and encapsulation.

**Abstraction:**
- Hides complexity
- Shows what an object does
- Achieved through abstract classes/interfaces
- Design level concept

**Encapsulation:**
- Hides data
- Shows how to access data safely
- Achieved through access modifiers
- Implementation level concept

### Explain Inheritance.

Inheritance allows a class to acquire properties and methods of another class. It establishes "IS-A" relationship.

**Example:**
```java
class Animal {
    void eat() { System.out.println("Animal eats"); }
    void sleep() { System.out.println("Animal sleeps"); }
}

class Dog extends Animal {
    void bark() { System.out.println("Dog barks"); }
    // Dog inherits eat() and sleep() from Animal
}
```

**Benefits:**
- Code reusability
- Method overriding
- Hierarchical classification

### Types of inheritance.

1. **Single Inheritance** - One child, one parent
2. **Multilevel Inheritance** - Chain of inheritance (A→B→C)
3. **Hierarchical Inheritance** - Multiple children, one parent
4. **Multiple Inheritance** - One child, multiple parents (not in Java)
5. **Hybrid Inheritance** - Combination of above types

### Explain Polymorphism.

Polymorphism means "many forms" - same interface behaving differently based on context.

**Example:**
```java
class Shape {
    void draw() { System.out.println("Drawing shape"); }
}

class Circle extends Shape {
    void draw() { System.out.println("Drawing circle"); }
}

class Rectangle extends Shape {
    void draw() { System.out.println("Drawing rectangle"); }
}

// Same method call, different behavior
Shape s1 = new Circle();
Shape s2 = new Rectangle();
s1.draw(); // "Drawing circle"
s2.draw(); // "Drawing rectangle"
```

### Compile-time vs run-time polymorphism.

**Compile-time Polymorphism:**
- Method overloading
- Operator overloading
- Resolved during compilation
- Static binding

**Run-time Polymorphism:**
- Method overriding
- Resolved during execution
- Dynamic binding
- Uses virtual method table

### Real-world example of polymorphism.

**Payment System:**
```java
abstract class Payment {
    abstract void processPayment(double amount);
}

class CreditCard extends Payment {
    void processPayment(double amount) {
        System.out.println("Processing $" + amount + " via Credit Card");
    }
}

class PayPal extends Payment {
    void processPayment(double amount) {
        System.out.println("Processing $" + amount + " via PayPal");
    }
}

// Same interface, different implementations
Payment payment = new CreditCard();
payment.processPayment(100); // Credit card processing
```

### Why OOP is better than procedural programming?

**OOP Advantages:**
- **Modularity** - Code organized in classes
- **Reusability** - Inheritance and composition
- **Maintainability** - Easier to modify and debug
- **Security** - Data hiding through encapsulation
- **Scalability** - Easy to add new features
- **Real-world modeling** - Natural way to represent entities

**Procedural Limitations:**
- Global data accessibility
- Difficult to maintain large codebases
- Limited code reusability
- No data security

### When should you NOT use OOP?

- **Simple scripts** - Small, one-time tasks
- **Performance-critical systems** - Where overhead matters
- **Mathematical computations** - Functional approach better
- **System programming** - Low-level operations
- **Small embedded systems** - Memory constraints
- **When team lacks OOP knowledge**

## 2️⃣ Classes, Objects & Access Control

### What is a class?

A class is a blueprint or template for creating objects. It defines:
- **Attributes** (data members)
- **Methods** (functions)
- **Constructors** (initialization)

```java
class Student {
    String name;        // Attribute
    int age;           // Attribute
    
    void study() {     // Method
        System.out.println(name + " is studying");
    }
}
```

### What is an object?

An object is an instance of a class. It's a real entity with:
- **State** (attribute values)
- **Behavior** (method calls)
- **Identity** (unique memory location)

```java
Student s1 = new Student(); // s1 is an object
s1.name = "John";
s1.age = 20;
s1.study(); // Calling method
```

### Class vs object difference.

**Class:**
- Blueprint/template
- No memory allocated
- Logical entity
- Defined once
- Example: Student class

**Object:**
- Instance of class
- Memory allocated
- Physical entity
- Can create multiple
- Example: s1, s2 objects

### What are access modifiers?

Access modifiers control the visibility and accessibility of classes, methods, and variables.

**Types:**
- **public** - Accessible everywhere
- **private** - Accessible only within same class
- **protected** - Accessible within package and subclasses
- **default** - Accessible within same package

### private vs protected vs public.

**private:**
- Same class only
- Most restrictive
- Data hiding

**protected:**
- Same package + subclasses
- Inheritance support
- Moderate access

**public:**
- Accessible everywhere
- Least restrictive
- Interface methods

### Default access modifier.

**Default (package-private):**
- No keyword specified
- Accessible within same package only
- Not accessible from different packages

```java
class MyClass {
    int value; // default access
    void method() { } // default access
}
```

### Why do we use private variables?

- **Data Security** - Prevent unauthorized access
- **Validation** - Control how data is modified
- **Encapsulation** - Hide implementation details
- **Maintainability** - Change internal structure without affecting external code

```java
class Person {
    private int age; // Cannot be accessed directly
    
    public void setAge(int age) {
        if(age > 0 && age < 150) { // Validation
            this.age = age;
        }
    }
}
```

### What is data hiding?

Data hiding is the concept of hiding internal data from outside access. It's achieved through:
- **Private variables**
- **Public methods** for controlled access
- **Validation** in setter methods

**Benefits:**
- Security
- Data integrity
- Flexibility to change implementation

### Can a class be final?

**Yes**, a class can be final.

```java
final class MyClass {
    // This class cannot be extended
}
```

**Examples:**
- String class
- Integer class
- All wrapper classes

**Purpose:**
- Prevent inheritance
- Security reasons
- Immutable classes

### Can an object be final?

**Yes**, an object reference can be final.

```java
final List<String> list = new ArrayList<>();
// list reference cannot be changed
// But list contents can be modified
list.add("item"); // This is allowed
// list = new ArrayList(); // This is NOT allowed
```

**Note:** Final makes the reference constant, not the object itself.

## 3️⃣ Constructors & Initialization (Frequently Asked)

### What is a constructor?

A constructor is a special method that initializes objects when they are created.

**Characteristics:**
- Same name as class
- No return type
- Called automatically during object creation
- Can be overloaded

```java
class Student {
    String name;
    
    Student() { // Default constructor
        name = "Unknown";
    }
    
    Student(String name) { // Parameterized constructor
        this.name = name;
    }
}
```

### Types of constructors.

1. **Default Constructor**
   - No parameters
   - Provided by compiler if not defined
   
2. **Parameterized Constructor**
   - Takes parameters
   - Used for initialization with specific values
   
3. **Copy Constructor**
   - Not available in Java (unlike C++)
   - Can be implemented manually

### Default constructor vs parameterized constructor.

**Default Constructor:**
- No parameters
- Sets default values
- Called when no arguments provided

**Parameterized Constructor:**
- Takes parameters
- Sets specific values
- Called when arguments provided

```java
Student s1 = new Student();        // Default constructor
Student s2 = new Student("John");  // Parameterized constructor
```

### Can constructors be overloaded?

**Yes**, constructors can be overloaded.

```java
class Rectangle {
    int length, width;
    
    Rectangle() {
        length = width = 1;
    }
    
    Rectangle(int side) {
        length = width = side;
    }
    
    Rectangle(int l, int w) {
        length = l;
        width = w;
    }
}
```

### Can constructors be inherited?

**No**, constructors are not inherited.

**Reasons:**
- Constructors have same name as class
- Child class has different name
- Each class needs its own initialization logic

**However:**
- Child constructor can call parent constructor using `super()`

### Can constructor be private?

**Yes**, constructors can be private.

**Use Cases:**
- **Singleton Pattern** - Only one instance allowed
- **Factory Pattern** - Object creation through factory methods
- **Utility Classes** - Prevent instantiation

```java
class Singleton {
    private static Singleton instance;
    
    private Singleton() { } // Private constructor
    
    public static Singleton getInstance() {
        if(instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

### What is constructor chaining?

Constructor chaining is calling one constructor from another constructor in the same class or parent class.

```java
class Student {
    String name;
    int age;
    
    Student() {
        this("Unknown", 0); // Calling parameterized constructor
    }
    
    Student(String name) {
        this(name, 18); // Calling another constructor
    }
    
    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

### What is this keyword?

`this` keyword refers to the current object instance.

**Uses:**
1. **Distinguish between instance and parameter variables**
2. **Call other constructors**
3. **Pass current object as parameter**
4. **Return current object**

```java
class Person {
    String name;
    
    void setName(String name) {
        this.name = name; // this.name refers to instance variable
    }
    
    Person getThis() {
        return this; // Return current object
    }
}
```

### Difference between this and super.

**this:**
- Refers to current object
- Access current class members
- Call current class constructors
- Used within same class

**super:**
- Refers to parent object
- Access parent class members
- Call parent class constructors
- Used for inheritance

```java
class Parent {
    int value = 10;
}

class Child extends Parent {
    int value = 20;
    
    void display() {
        System.out.println(this.value);  // 20 (current class)
        System.out.println(super.value); // 10 (parent class)
    }
}
```

## 4️⃣ Inheritance (Prime Favorite)

### What is inheritance?

Inheritance is a mechanism where a new class acquires properties and methods of an existing class. It establishes "IS-A" relationship.

**Syntax:**
```java
class Parent {
    // Parent class members
}

class Child extends Parent {
    // Child class inherits Parent members
    // Plus its own members
}
```

### Why is inheritance used?

**Benefits:**
- **Code Reusability** - Avoid writing duplicate code
- **Method Overriding** - Customize parent behavior
- **Hierarchical Classification** - Organize related classes
- **Polymorphism** - Runtime method resolution
- **Maintainability** - Changes in parent reflect in children

### Types of inheritance supported in Java.

**Java Supports:**
1. **Single Inheritance** - One parent, one child
2. **Multilevel Inheritance** - Chain of inheritance
3. **Hierarchical Inheritance** - Multiple children, one parent

**Java Does NOT Support:**
- **Multiple Inheritance** (through classes)
- **Hybrid Inheritance** (combination involving multiple inheritance)

### Why multiple inheritance not supported in Java?

**Diamond Problem:**
```
    A
   / \
  B   C
   \ /
    D
```

If B and C both override method from A, which version should D inherit?

**Issues:**
- **Ambiguity** - Which parent method to call
- **Complexity** - Difficult to resolve conflicts
- **Maintenance** - Hard to debug and maintain

### How Java supports multiple inheritance?

**Through Interfaces:**
```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

class Duck implements Flyable, Swimmable {
    public void fly() { System.out.println("Duck flies"); }
    public void swim() { System.out.println("Duck swims"); }
}
```

**Why Interfaces Work:**
- No implementation conflicts (abstract methods)
- Clear contract definition
- Default methods have resolution rules

### What is super keyword?

`super` keyword refers to the immediate parent class object.

**Uses:**
1. **Access parent class variables**
2. **Call parent class methods**
3. **Call parent class constructors**

```java
class Animal {
    String name = "Animal";
    void eat() { System.out.println("Animal eats"); }
}

class Dog extends Animal {
    String name = "Dog";
    
    void display() {
        System.out.println(super.name); // "Animal"
        System.out.println(this.name);  // "Dog"
        super.eat(); // Call parent method
    }
}
```

### Method overriding rules.

1. **Same method signature** (name, parameters, return type)
2. **Cannot reduce visibility** (public → private not allowed)
3. **Cannot override static methods**
4. **Cannot override private methods**
5. **Cannot override final methods**
6. **Exception handling rules** apply

```java
class Parent {
    protected void method() { }
}

class Child extends Parent {
    @Override
    public void method() { } // Visibility increased (allowed)
}
```

### Can we override static methods?

**No**, static methods cannot be overridden.

**Reason:**
- Static methods belong to class, not object
- Method resolution happens at compile time
- No dynamic binding for static methods

**What happens:**
```java
class Parent {
    static void method() { System.out.println("Parent"); }
}

class Child extends Parent {
    static void method() { System.out.println("Child"); } // Method hiding, not overriding
}
```

This is **method hiding**, not overriding.

### Can we override private methods?

**No**, private methods cannot be overridden.

**Reason:**
- Private methods are not inherited
- Child class cannot access parent's private methods
- No inheritance means no overriding

```java
class Parent {
    private void method() { } // Not inherited
}

class Child extends Parent {
    private void method() { } // This is a new method, not overriding
}
```

### What is upcasting and downcasting?

**Upcasting:**
- Child object → Parent reference
- Implicit conversion
- Always safe
- Lose access to child-specific methods

**Downcasting:**
- Parent reference → Child object
- Explicit conversion
- May throw ClassCastException
- Gain access to child-specific methods

```java
class Animal { }
class Dog extends Animal {
    void bark() { }
}

// Upcasting (safe)
Animal animal = new Dog(); // Implicit

// Downcasting (risky)
Dog dog = (Dog) animal; // Explicit casting required
dog.bark(); // Now can access Dog methods
```

### When to use inheritance vs composition?

**Use Inheritance when:**
- True "IS-A" relationship exists
- Need to override parent methods
- Want to achieve polymorphism
- Shared behavior among related classes

**Use Composition when:**
- "HAS-A" relationship exists
- Need flexibility in relationships
- Want to avoid tight coupling
- Multiple inheritance-like behavior needed

```java
// Inheritance: Car IS-A Vehicle
class Car extends Vehicle { }

// Composition: Car HAS-A Engine
class Car {
    private Engine engine; // Composition
}
```

## 5️⃣ Polymorphism & Method Behavior

### What is method overloading?

Method overloading allows multiple methods with the same name but different parameters in the same class.

**Rules:**
- Same method name
- Different parameter list (number, type, or order)
- Return type can be different
- Resolved at compile time

```java
class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
}
```

### Overloading vs overriding.

**Method Overloading:**
- Same class
- Same method name, different parameters
- Compile-time polymorphism
- No inheritance required

**Method Overriding:**
- Different classes (inheritance)
- Same method signature
- Runtime polymorphism
- Inheritance required

### Can return type change in overloading?

**Yes**, return type can change in overloading.

```java
class Example {
    int method(int x) { return x; }
    double method(double x) { return x; } // Different return type allowed
}
```

**Note:** Return type alone cannot distinguish overloaded methods.

### Can return type change in overriding?

**Partially yes** - return type can change if it's a subtype (covariant return type).

```java
class Animal { }
class Dog extends Animal { }

class Parent {
    Animal getAnimal() { return new Animal(); }
}

class Child extends Parent {
    @Override
    Dog getAnimal() { return new Dog(); } // Covariant return type
}
```

### Can we overload main()?

**Yes**, main() method can be overloaded.

```java
class Test {
    public static void main(String[] args) {
        System.out.println("Original main");
        main(5);
    }
    
    public static void main(int x) {
        System.out.println("Overloaded main: " + x);
    }
}
```

**Note:** JVM will only call `main(String[] args)` to start the program.

### Can we overload constructors?

**Yes**, constructors can be overloaded.

```java
class Student {
    String name;
    int age;
    
    Student() { }
    Student(String name) { this.name = name; }
    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

### How does runtime polymorphism work internally?

**Virtual Method Table (VMT):**
1. Each class has a virtual method table
2. Contains pointers to actual method implementations
3. Object reference points to appropriate VMT
4. Method call resolved through VMT lookup

```java
Animal animal = new Dog();
animal.sound(); // Resolved at runtime through Dog's VMT
```

**Steps:**
1. Check object's actual type (Dog)
2. Look up method in Dog's VMT
3. Execute Dog's implementation

### Example of runtime polymorphism.

```java
abstract class Shape {
    abstract double calculateArea();
}

class Circle extends Shape {
    double radius;
    Circle(double radius) { this.radius = radius; }
    
    @Override
    double calculateArea() {
        return Math.PI * radius * radius;
    }
}

class Rectangle extends Shape {
    double length, width;
    Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }
    
    @Override
    double calculateArea() {
        return length * width;
    }
}

// Runtime polymorphism
Shape[] shapes = {
    new Circle(5),
    new Rectangle(4, 6)
};

for(Shape shape : shapes) {
    System.out.println(shape.calculateArea()); // Different implementations called
}
```

## 6️⃣ Abstraction Deep Dive

### What is abstraction?

Abstraction is hiding implementation complexity and showing only essential features to the user.

**Key Points:**
- Focus on WHAT an object does, not HOW
- Hide unnecessary details
- Provide simplified interface
- Achieved through abstract classes and interfaces

**Real Example:** TV Remote
- You know what buttons do (abstraction)
- You don't know internal circuitry (hidden complexity)

### What is an abstract class?

An abstract class is a class that cannot be instantiated and may contain abstract methods.

```java
abstract class Animal {
    String name;
    
    abstract void sound(); // Abstract method (no implementation)
    
    void sleep() { // Concrete method
        System.out.println(name + " is sleeping");
    }
}
```

**Characteristics:**
- Cannot create objects directly
- Can have both abstract and concrete methods
- Can have constructors, variables, static methods

### Can abstract class have constructors?

**Yes**, abstract classes can have constructors.

```java
abstract class Vehicle {
    String brand;
    
    Vehicle(String brand) { // Constructor in abstract class
        this.brand = brand;
    }
    
    abstract void start();
}

class Car extends Vehicle {
    Car(String brand) {
        super(brand); // Calling abstract class constructor
    }
    
    void start() {
        System.out.println(brand + " car started");
    }
}
```

**Purpose:**
- Initialize common fields
- Called by child class constructors

### Can abstract class have non-abstract methods?

**Yes**, abstract classes can have concrete (non-abstract) methods.

```java
abstract class Shape {
    // Concrete method
    void display() {
        System.out.println("This is a shape");
    }
    
    // Abstract method
    abstract double calculateArea();
}
```

**Benefits:**
- Provide common functionality
- Reduce code duplication
- Partial implementation

### Can we create object of abstract class?

**No**, we cannot create objects of abstract classes directly.

```java
abstract class Animal { }

// Animal animal = new Animal(); // Compilation error
```

**However:**
- Can create reference variables
- Can instantiate through child classes

```java
Animal animal = new Dog(); // Valid (Dog extends Animal)
```

### What is an interface?

An interface is a contract that defines what methods a class must implement, without providing implementation.

```java
interface Drawable {
    void draw(); // Abstract method (public abstract by default)
    
    default void print() { // Default method (Java 8+)
        System.out.println("Printing...");
    }
    
    static void info() { // Static method (Java 8+)
        System.out.println("Drawable interface");
    }
}
```

**Characteristics:**
- All methods are public abstract by default
- All variables are public static final
- Supports multiple inheritance
- Cannot have constructors

### Abstract class vs interface.

**Abstract Class:**
- Can have concrete methods
- Can have constructors
- Can have instance variables
- Single inheritance only
- Can have access modifiers

**Interface:**
- All methods abstract (except default/static)
- No constructors
- Only constants (public static final)
- Multiple inheritance supported
- All methods public by default

**When to use:**
- **Abstract Class**: When classes share common code
- **Interface**: When defining contracts for unrelated classes

### Why interfaces are preferred?

**Advantages:**
- **Multiple Inheritance** - Class can implement multiple interfaces
- **Loose Coupling** - Depend on abstraction, not implementation
- **Flexibility** - Easy to change implementations
- **Testability** - Easy to mock for testing
- **Contract Definition** - Clear API specification

### Can interface have variables?

**Yes**, but with restrictions:
- All variables are **public static final** by default
- Must be initialized at declaration
- Act as constants

```java
interface Constants {
    int MAX_SIZE = 100; // public static final by default
    String DEFAULT_NAME = "Unknown";
}
```

### Can interface have methods with body?

**Yes** (since Java 8):

1. **Default Methods** - Have implementation
2. **Static Methods** - Have implementation
3. **Private Methods** - Have implementation (Java 9+)

```java
interface MyInterface {
    void abstractMethod(); // No body
    
    default void defaultMethod() { // Has body
        System.out.println("Default implementation");
    }
    
    static void staticMethod() { // Has body
        System.out.println("Static method");
    }
}
```

### Functional interface.

A functional interface has exactly one abstract method.

```java
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b); // Only one abstract method
    
    // Can have default and static methods
    default void print() { }
    static void info() { }
}
```

**Used for:**
- Lambda expressions
- Method references
- Functional programming

### What is default method in interface?

Default methods provide implementation in interfaces (Java 8+).

```java
interface Vehicle {
    void start(); // Abstract method
    
    default void honk() { // Default method
        System.out.println("Beep beep!");
    }
}

class Car implements Vehicle {
    public void start() {
        System.out.println("Car started");
    }
    // honk() is inherited, no need to implement
}
```

**Benefits:**
- Add new methods without breaking existing implementations
- Provide common functionality
- Enable interface evolution

## 7️⃣ Encapsulation & Data Hiding

### What is encapsulation?

Encapsulation is bundling data and methods together and controlling access to them through access modifiers.

**Key Components:**
- **Data Hiding** - Private variables
- **Controlled Access** - Public methods
- **Validation** - Input checking
- **Security** - Prevent unauthorized access

### How to achieve encapsulation?

1. **Make variables private**
2. **Provide public getter/setter methods**
3. **Add validation in setters**
4. **Control access through methods**

```java
class Employee {
    private String name;
    private double salary;
    
    // Getter methods
    public String getName() { return name; }
    public double getSalary() { return salary; }
    
    // Setter methods with validation
    public void setName(String name) {
        if(name != null && !name.trim().isEmpty()) {
            this.name = name;
        }
    }
    
    public void setSalary(double salary) {
        if(salary > 0) {
            this.salary = salary;
        }
    }
}
```

### Benefits of encapsulation.

- **Data Security** - Prevent unauthorized access
- **Data Validation** - Ensure data integrity
- **Flexibility** - Change internal implementation
- **Maintainability** - Easier to modify and debug
- **Code Organization** - Related data and methods together
- **Reusability** - Well-defined interfaces

### Getters and setters usage.

**Getters (Accessors):**
- Provide read access to private variables
- Can add logic before returning value
- Control what data is exposed

**Setters (Mutators):**
- Provide write access to private variables
- Add validation before setting value
- Control how data is modified

```java
class Person {
    private int age;
    
    public int getAge() {
        return age;
    }
    
    public void setAge(int age) {
        if(age >= 0 && age <= 150) { // Validation
            this.age = age;
        } else {
            throw new IllegalArgumentException("Invalid age");
        }
    }
}
```

### Can encapsulation exist without inheritance?

**Yes**, encapsulation is independent of inheritance.

**Encapsulation** is about:
- Data hiding
- Controlled access
- Single class concept

**Inheritance** is about:
- Code reusability
- IS-A relationship
- Multiple class concept

```java
// Encapsulation without inheritance
class BankAccount {
    private double balance; // Encapsulated
    
    public void deposit(double amount) {
        if(amount > 0) balance += amount;
    }
    
    public double getBalance() { return balance; }
}
```

### Real-world example of encapsulation.

**ATM Machine:**
```java
class ATM {
    private double balance;
    private String pin;
    
    public boolean validatePin(String inputPin) {
        return pin.equals(inputPin);
    }
    
    public void withdraw(double amount, String inputPin) {
        if(!validatePin(inputPin)) {
            System.out.println("Invalid PIN");
            return;
        }
        
        if(amount > balance) {
            System.out.println("Insufficient funds");
            return;
        }
        
        balance -= amount;
        System.out.println("Withdrawal successful");
    }
    
    public double checkBalance(String inputPin) {
        if(validatePin(inputPin)) {
            return balance;
        }
        return -1; // Invalid access
    }
}
```

**Encapsulation Benefits Here:**
- PIN and balance are hidden
- Access only through validated methods
- Business logic encapsulated
- Security maintained

---

**Total Questions Covered: 100+**

This comprehensive guide covers all OOPS questions with modern formatting and real-world examples! 🎯
## 8️⃣ Static Keyword (Very Common)

### What is static keyword?

`static` keyword belongs to the class rather than any instance. It can be applied to variables, methods, blocks, and nested classes.

**Key Points:**
- Shared among all instances
- Loaded when class is first loaded
- Accessed without creating objects
- Memory allocated once

### Static variable vs instance variable.

**Static Variable:**
- Belongs to class
- Shared among all objects
- Single copy in memory
- Initialized when class loads
- Also called class variable

**Instance Variable:**
- Belongs to object
- Separate copy for each object
- Multiple copies in memory
- Initialized when object is created

```java
class Student {
    static String school = "ABC School"; // Static variable
    String name; // Instance variable
    
    static int count = 0; // Shared counter
    
    Student(String name) {
        this.name = name;
        count++; // Increment for each object
    }
}
```

### Static method vs instance method.

**Static Method:**
- Belongs to class
- Called without object
- Cannot access instance variables directly
- Cannot use `this` or `super`
- Resolved at compile time

**Instance Method:**
- Belongs to object
- Called through object reference
- Can access both static and instance variables
- Can use `this` and `super`
- Resolved at runtime

```java
class MathUtils {
    static int add(int a, int b) { // Static method
        return a + b;
    }
    
    void display() { // Instance method
        System.out.println("Instance method");
    }
}

// Usage
int result = MathUtils.add(5, 3); // No object needed
MathUtils obj = new MathUtils();
obj.display(); // Object needed
```

### Why main() is static?

**Reasons:**
1. **JVM can call without creating object**
2. **Entry point** - No object exists initially
3. **Class loading** - Available when class loads
4. **Memory efficiency** - No object creation overhead

```java
public class Test {
    public static void main(String[] args) {
        // JVM calls this without creating Test object
        System.out.println("Program starts");
    }
}
```

### Can static method access non-static members?

**No**, static methods cannot directly access non-static members.

**Reason:**
- Static methods belong to class
- Non-static members belong to objects
- No object context in static methods

```java
class Example {
    int instanceVar = 10;
    static int staticVar = 20;
    
    static void staticMethod() {
        // System.out.println(instanceVar); // ERROR
        System.out.println(staticVar); // OK
        
        // To access instance variable, need object
        Example obj = new Example();
        System.out.println(obj.instanceVar); // OK
    }
}
```

### Static block.

Static block is executed when class is first loaded, before any object creation or static method calls.

```java
class InitDemo {
    static int value;
    
    static { // Static block
        System.out.println("Static block executed");
        value = 100;
        // Complex initialization logic
    }
    
    static {
        System.out.println("Second static block");
        // Multiple static blocks allowed
    }
}
```

**Use Cases:**
- Initialize static variables
- Load native libraries
- Complex static initialization
- One-time setup operations

### Use-cases of static keyword.

**Static Variables:**
- Constants (final static)
- Counters (object count)
- Shared configuration

**Static Methods:**
- Utility functions (Math.max())
- Factory methods
- Helper functions

**Static Blocks:**
- Static variable initialization
- Loading resources
- One-time setup

```java
class DatabaseConfig {
    static final String URL = "jdbc:mysql://localhost"; // Constant
    static int connectionCount = 0; // Counter
    
    static { // Static block
        // Load database driver
        System.out.println("Database driver loaded");
    }
    
    static Connection getConnection() { // Utility method
        connectionCount++;
        // Return database connection
        return null;
    }
}
```

## 9️⃣ Memory & Object Lifecycle

### Stack vs heap memory.

**Stack Memory:**
- Stores method calls and local variables
- LIFO (Last In, First Out) structure
- Fast access
- Limited size
- Automatic memory management
- Thread-specific

**Heap Memory:**
- Stores objects and instance variables
- Shared among all threads
- Larger size
- Slower access than stack
- Garbage collection manages memory

```java
void method() {
    int x = 10; // Stored in stack
    String str = new String("Hello"); // Reference in stack, object in heap
}
```

### Where are objects stored?

**Objects are stored in Heap Memory.**

**Heap Sections:**
1. **Young Generation**
   - Eden Space (new objects)
   - Survivor Spaces (survived objects)

2. **Old Generation**
   - Long-lived objects
   - Objects promoted from young generation

3. **Metaspace** (Java 8+)
   - Class metadata
   - Replaced permanent generation

### What is garbage collection?

Garbage Collection (GC) is automatic memory management that removes unused objects from heap memory.

**Process:**
1. **Mark** - Identify unreachable objects
2. **Sweep** - Remove marked objects
3. **Compact** - Defragment memory (optional)

**Benefits:**
- Prevents memory leaks
- Automatic memory management
- No manual memory deallocation needed

### How garbage collection works (basic).

**Steps:**
1. **Root Set Identification** - Find all reachable objects from roots (stack variables, static variables)
2. **Mark Phase** - Mark all reachable objects
3. **Sweep Phase** - Remove unmarked objects
4. **Compaction** - Move surviving objects together

**Generational Hypothesis:**
- Most objects die young
- Young generation collected frequently
- Old generation collected less frequently

### Can we force garbage collection?

**Technically yes, but not recommended.**

```java
System.gc(); // Suggests JVM to run GC
Runtime.getRuntime().gc(); // Same as above
```

**Important Notes:**
- It's only a suggestion, not a guarantee
- JVM may ignore the request
- Can impact performance
- Better to let JVM manage automatically

### finalize() method (basic).

`finalize()` method is called by garbage collector before object destruction.

```java
class Resource {
    @Override
    protected void finalize() throws Throwable {
        try {
            // Cleanup code
            System.out.println("Object being finalized");
        } finally {
            super.finalize();
        }
    }
}
```

**Problems with finalize():**
- No guarantee when it's called
- Can prevent garbage collection
- Performance impact
- Deprecated in Java 9+

**Better Alternatives:**
- try-with-resources
- AutoCloseable interface
- Explicit cleanup methods

### Memory leak in Java?

**Yes**, memory leaks can occur in Java despite garbage collection.

**Common Causes:**
1. **Static Collections** - Objects never removed
2. **Listeners not removed** - Event listeners holding references
3. **Inner Classes** - Hold reference to outer class
4. **ThreadLocal variables** - Not cleaned up
5. **Unclosed Resources** - Files, connections not closed

```java
// Memory leak example
class MemoryLeak {
    static List<Object> list = new ArrayList<>();
    
    void addObject() {
        list.add(new Object()); // Objects never removed
    }
}
```

### Object creation steps internally.

**Steps when `new Object()` is called:**

1. **Class Loading** - Load class if not already loaded
2. **Memory Allocation** - Allocate memory in heap
3. **Instance Variable Initialization** - Set default values
4. **Constructor Execution** - Run constructor code
5. **Reference Return** - Return object reference

```java
Student s = new Student("John");
```

**Detailed Process:**
1. Check if Student class is loaded
2. Allocate memory for Student object in heap
3. Initialize instance variables to default values
4. Call Student constructor with "John"
5. Return reference to created object
6. Assign reference to variable 's'

## 🔟 Exception Handling (Basic but Important)

### What is exception?

An exception is an unexpected event that occurs during program execution and disrupts normal flow.

**Types:**
- **Checked Exceptions** - Must be handled (IOException)
- **Unchecked Exceptions** - Runtime exceptions (NullPointerException)
- **Errors** - System-level problems (OutOfMemoryError)

### Checked vs unchecked exception.

**Checked Exceptions:**
- Must be handled or declared
- Checked at compile time
- Extend Exception class
- Examples: IOException, SQLException

**Unchecked Exceptions:**
- Not required to handle
- Checked at runtime
- Extend RuntimeException class
- Examples: NullPointerException, ArrayIndexOutOfBoundsException

```java
// Checked exception - must handle
try {
    FileReader file = new FileReader("file.txt");
} catch (FileNotFoundException e) {
    e.printStackTrace();
}

// Unchecked exception - optional to handle
String str = null;
int length = str.length(); // NullPointerException
```

### try-catch-finally flow.

```java
try {
    // Code that may throw exception
    int result = 10 / 0;
} catch (ArithmeticException e) {
    // Handle specific exception
    System.out.println("Division by zero");
} catch (Exception e) {
    // Handle any other exception
    System.out.println("General exception");
} finally {
    // Always executed (cleanup code)
    System.out.println("Finally block");
}
```

**Execution Flow:**
1. Execute try block
2. If exception occurs, jump to appropriate catch block
3. Execute finally block (always)
4. Continue with rest of program

### Can finally block be skipped?

**Rarely**, finally block can be skipped in these cases:

1. **System.exit()** called
2. **JVM crash**
3. **Infinite loop** in try/catch
4. **Thread interruption**

```java
try {
    System.exit(0); // Finally block skipped
} finally {
    System.out.println("This won't print");
}
```

**Normal cases where finally executes:**
- Exception thrown and caught
- Exception thrown but not caught
- No exception occurs
- Return statement in try/catch

### throw vs throws.

**throw:**
- Used to explicitly throw an exception
- Used inside method body
- Followed by exception object
- Can throw only one exception at a time

**throws:**
- Used to declare exceptions that method might throw
- Used in method signature
- Followed by exception class names
- Can declare multiple exceptions

```java
class ExceptionDemo {
    // throws - declares exceptions
    void method1() throws IOException, SQLException {
        if (someCondition) {
            throw new IOException("File not found"); // throw - throws exception
        }
    }
}
```

### Custom exception.

Create custom exceptions by extending Exception or RuntimeException.

```java
// Custom checked exception
class InvalidAgeException extends Exception {
    public InvalidAgeException(String message) {
        super(message);
    }
}

// Custom unchecked exception
class InsufficientBalanceException extends RuntimeException {
    public InsufficientBalanceException(String message) {
        super(message);
    }
}

// Usage
class Person {
    void setAge(int age) throws InvalidAgeException {
        if (age < 0 || age > 150) {
            throw new InvalidAgeException("Age must be between 0 and 150");
        }
    }
}
```

### Multiple catch blocks.

Multiple catch blocks handle different types of exceptions.

```java
try {
    // Code that may throw different exceptions
    int[] arr = new int[5];
    arr[10] = 20; // ArrayIndexOutOfBoundsException
    String str = null;
    str.length(); // NullPointerException
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Array index out of bounds");
} catch (NullPointerException e) {
    System.out.println("Null pointer exception");
} catch (Exception e) {
    System.out.println("General exception");
}
```

**Rules:**
- Specific exceptions first, general exceptions last
- Cannot have unreachable catch blocks
- Only one catch block executes

### Exception hierarchy.

```
Throwable
├── Error
│   ├── OutOfMemoryError
│   ├── StackOverflowError
│   └── VirtualMachineError
└── Exception
    ├── IOException (Checked)
    ├── SQLException (Checked)
    └── RuntimeException (Unchecked)
        ├── NullPointerException
        ├── ArrayIndexOutOfBoundsException
        └── IllegalArgumentException
```

## 1️⃣1️⃣ Interfaces, Abstract, Final Keywords

### final variable vs final method vs final class.

**final Variable:**
- Cannot be reassigned
- Must be initialized
- Acts as constant

**final Method:**
- Cannot be overridden
- Can be inherited
- Implementation is fixed

**final Class:**
- Cannot be extended
- No subclasses allowed
- Examples: String, Integer

```java
final class FinalClass { } // Cannot be extended

class Parent {
    final void finalMethod() { } // Cannot be overridden
}

class Example {
    final int value = 10; // Cannot be changed
}
```

### Why make a class final?

**Reasons:**
- **Security** - Prevent malicious extension
- **Immutability** - Ensure object state cannot change
- **Performance** - Enable compiler optimizations
- **Design** - Class is complete and shouldn't be extended

**Examples:**
- String class (immutability)
- Wrapper classes (Integer, Double)
- Utility classes

### Can interface extend another interface?

**Yes**, interfaces can extend other interfaces.

```java
interface Animal {
    void eat();
}

interface Mammal extends Animal {
    void breathe();
}

interface Dog extends Mammal {
    void bark();
}

// Dog interface has: eat(), breathe(), bark()
```

**Multiple Inheritance:**
```java
interface A { void methodA(); }
interface B { void methodB(); }

interface C extends A, B {
    void methodC();
    // C has: methodA(), methodB(), methodC()
}
```

### Can class implement multiple interfaces?

**Yes**, a class can implement multiple interfaces.

```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

class Duck implements Flyable, Swimmable {
    public void fly() {
        System.out.println("Duck flies");
    }
    
    public void swim() {
        System.out.println("Duck swims");
    }
}
```

### Diamond problem.

Diamond problem occurs in multiple inheritance when a class inherits from two classes that have a common parent.

```
    A
   / \
  B   C
   \ /
    D
```

**Problem:** If B and C both override method from A, which version should D inherit?

**Java Solution:**
- **Classes:** Multiple inheritance not allowed
- **Interfaces:** Default method resolution rules handle conflicts

### Marker interface.

Marker interface is an empty interface used to mark or tag classes.

```java
interface Serializable { 
    // Empty interface - just a marker
}

class Student implements Serializable {
    // Student objects can be serialized
}
```

**Examples:**
- Serializable - Objects can be serialized
- Cloneable - Objects can be cloned
- Remote - Objects can be used in RMI

### Serializable vs Cloneable (basic idea).

**Serializable:**
- Converts object to byte stream
- Used for persistence and network transfer
- Automatic process

**Cloneable:**
- Creates copy of object
- Must implement clone() method
- Shallow vs deep copy considerations

```java
class Person implements Serializable, Cloneable {
    String name;
    
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
```

## 1️⃣2️⃣ Collections (Basic OOP + Practical)

### What is Collection framework?

Collection framework provides architecture to store and manipulate groups of objects.

**Core Interfaces:**
- **Collection** - Root interface
- **List** - Ordered collection (duplicates allowed)
- **Set** - No duplicates
- **Map** - Key-value pairs

### List vs Set vs Map.

**List:**
- Ordered collection
- Allows duplicates
- Index-based access
- Examples: ArrayList, LinkedList

**Set:**
- No duplicates
- May or may not be ordered
- Examples: HashSet, TreeSet

**Map:**
- Key-value pairs
- Keys are unique
- Examples: HashMap, TreeMap

```java
List<String> list = Arrays.asList("A", "B", "A"); // Duplicates allowed
Set<String> set = new HashSet<>(Arrays.asList("A", "B", "A")); // {A, B}
Map<String, Integer> map = new HashMap<>(); // Key-value pairs
map.put("A", 1);
```

### Array vs ArrayList.

**Array:**
- Fixed size
- Can store primitives and objects
- Direct memory access
- No built-in methods

**ArrayList:**
- Dynamic size
- Only stores objects (autoboxing for primitives)
- Wrapper around array
- Rich API methods

```java
// Array
int[] arr = new int[5]; // Fixed size
arr[0] = 10;

// ArrayList
ArrayList<Integer> list = new ArrayList<>(); // Dynamic size
list.add(10);
list.add(20);
```

### HashSet vs TreeSet.

**HashSet:**
- Hash table implementation
- No ordering
- O(1) average time complexity
- Allows one null value

**TreeSet:**
- Red-black tree implementation
- Sorted order
- O(log n) time complexity
- No null values allowed

```java
Set<Integer> hashSet = new HashSet<>();
hashSet.add(3); hashSet.add(1); hashSet.add(2);
// Order: unpredictable

Set<Integer> treeSet = new TreeSet<>();
treeSet.add(3); treeSet.add(1); treeSet.add(2);
// Order: [1, 2, 3] (sorted)
```

### HashMap vs TreeMap.

**HashMap:**
- Hash table implementation
- No ordering
- O(1) average time complexity
- Allows one null key

**TreeMap:**
- Red-black tree implementation
- Sorted by keys
- O(log n) time complexity
- No null keys allowed

### When to use which collection?

**ArrayList:**
- Frequent random access
- More reads than writes
- Need indexed access

**LinkedList:**
- Frequent insertions/deletions
- Queue/Stack operations
- Sequential access

**HashSet:**
- Need unique elements
- Fast lookups
- No ordering required

**TreeSet:**
- Need unique elements
- Sorted order required
- Range operations

**HashMap:**
- Key-value mapping
- Fast lookups
- No ordering required

**TreeMap:**
- Key-value mapping
- Sorted by keys
- Range operations on keys

### Why HashMap allows one null key?

**Design Decision:**
- null is treated as a special key
- Hashed to index 0
- Only one null key possible (uniqueness)
- Multiple null values allowed

```java
Map<String, String> map = new HashMap<>();
map.put(null, "value1"); // Allowed
map.put(null, "value2"); // Overwrites previous
map.put("key", null);    // Null values allowed
```

### Iterator vs ListIterator.

**Iterator:**
- Forward direction only
- Works with all collections
- Methods: hasNext(), next(), remove()

**ListIterator:**
- Bidirectional (forward and backward)
- Only for List implementations
- Additional methods: hasPrevious(), previous(), add(), set()

```java
List<String> list = Arrays.asList("A", "B", "C");

// Iterator
Iterator<String> iter = list.iterator();
while (iter.hasNext()) {
    System.out.println(iter.next());
}

// ListIterator
ListIterator<String> listIter = list.listIterator();
while (listIter.hasNext()) {
    System.out.println(listIter.next());
}
// Can go backward
while (listIter.hasPrevious()) {
    System.out.println(listIter.previous());
}
```

## 1️⃣3️⃣ Frequently Asked Trick / Rapid Questions

### Can a class have multiple constructors?

**Yes**, a class can have multiple constructors (constructor overloading).

```java
class Student {
    String name;
    int age;
    
    Student() { } // Default constructor
    Student(String name) { this.name = name; } // One parameter
    Student(String name, int age) { // Two parameters
        this.name = name;
        this.age = age;
    }
}
```

### Can we override equals()?

**Yes**, equals() method can and should be overridden.

```java
class Person {
    String name;
    int age;
    
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        
        Person person = (Person) obj;
        return age == person.age && Objects.equals(name, person.name);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
}
```

### equals() vs == operator.

**== Operator:**
- Compares references for objects
- Compares values for primitives
- Cannot be overridden

**equals() Method:**
- Compares object content
- Can be overridden
- Default implementation uses ==

```java
String s1 = new String("Hello");
String s2 = new String("Hello");

System.out.println(s1 == s2);      // false (different references)
System.out.println(s1.equals(s2)); // true (same content)
```

### hashCode() contract.

**Rules:**
1. If two objects are equal (equals() returns true), they must have same hashCode
2. If two objects have same hashCode, they may or may not be equal
3. hashCode should be consistent during object lifetime
4. If equals() is overridden, hashCode() must also be overridden

```java
class Person {
    String name;
    
    @Override
    public boolean equals(Object obj) {
        // equals implementation
        return Objects.equals(name, ((Person) obj).name);
    }
    
    @Override
    public int hashCode() {
        return Objects.hash(name); // Must override when equals is overridden
    }
}
```

### Shallow copy vs deep copy.

**Shallow Copy:**
- Copies object references
- Original and copy share same nested objects
- Changes in nested objects affect both

**Deep Copy:**
- Copies entire object hierarchy
- Original and copy have separate nested objects
- Changes in nested objects don't affect each other

```java
class Address {
    String city;
    Address(String city) { this.city = city; }
}

class Person implements Cloneable {
    String name;
    Address address;
    
    // Shallow copy
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone(); // Only copies references
    }
    
    // Deep copy
    public Person deepCopy() {
        Person copy = new Person();
        copy.name = this.name;
        copy.address = new Address(this.address.city); // New Address object
        return copy;
    }
}
```

### Immutable class.

Immutable class is a class whose objects cannot be modified after creation.

**Rules to create immutable class:**
1. Make class final
2. Make all fields private and final
3. No setter methods
4. Initialize all fields through constructor
5. Return defensive copies of mutable objects

```java
public final class ImmutablePerson {
    private final String name;
    private final int age;
    private final List<String> hobbies;
    
    public ImmutablePerson(String name, int age, List<String> hobbies) {
        this.name = name;
        this.age = age;
        this.hobbies = new ArrayList<>(hobbies); // Defensive copy
    }
    
    public String getName() { return name; }
    public int getAge() { return age; }
    
    public List<String> getHobbies() {
        return new ArrayList<>(hobbies); // Return defensive copy
    }
}
```

### String vs StringBuilder vs StringBuffer.

**String:**
- Immutable
- Thread-safe (immutable objects are inherently thread-safe)
- Creates new object for each modification
- Slower for multiple concatenations

**StringBuilder:**
- Mutable
- Not thread-safe
- Modifies existing buffer
- Faster for multiple concatenations
- Introduced in Java 5

**StringBuffer:**
- Mutable
- Thread-safe (synchronized methods)
- Modifies existing buffer
- Slower than StringBuilder due to synchronization

```java
// String - creates multiple objects
String str = "Hello";
str += " World"; // Creates new String object

// StringBuilder - modifies buffer
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // Modifies existing buffer

// StringBuffer - thread-safe version
StringBuffer sbf = new StringBuffer("Hello");
sbf.append(" World"); // Thread-safe modification
```

### Why String is immutable?

**Reasons:**
1. **String Pool** - Enables string literal sharing
2. **Security** - Strings used in security contexts (passwords, URLs)
3. **Thread Safety** - Immutable objects are inherently thread-safe
4. **Caching** - hashCode can be cached
5. **Performance** - JVM optimizations possible

```java
String s1 = "Hello"; // Stored in string pool
String s2 = "Hello"; // Reuses same object from pool
System.out.println(s1 == s2); // true (same reference)
```

### Can main() be overloaded?

**Yes**, main() method can be overloaded.

```java
public class MainOverload {
    public static void main(String[] args) {
        System.out.println("Original main");
        main(5);
        main(5, 10);
    }
    
    public static void main(int x) {
        System.out.println("main with int: " + x);
    }
    
    public static void main(int x, int y) {
        System.out.println("main with two ints: " + x + ", " + y);
    }
}
```

**Note:** JVM will only call `main(String[] args)` to start the program.

### Can main() be private?

**No**, main() method cannot be private.

**Reason:**
- JVM needs to access main() method
- Private methods are not accessible from outside class
- JVM is external to your class

```java
// This won't work
private static void main(String[] args) {
    // JVM cannot access private main
}
```

**main() must be:**
- public (accessible to JVM)
- static (no object creation needed)
- void (no return value expected)

### What happens if constructor throws exception?

**If constructor throws exception:**
1. **Object creation fails**
2. **Memory allocated is garbage collected**
3. **Reference variable remains null**
4. **Exception propagates to caller**

```java
class Person {
    String name;
    
    Person(String name) {
        if (name == null) {
            throw new IllegalArgumentException("Name cannot be null");
        }
        this.name = name;
    }
}

// Usage
try {
    Person p = new Person(null); // Constructor throws exception
    // p remains null, object not created
} catch (IllegalArgumentException e) {
    System.out.println("Object creation failed");
}
```

### Can abstract method be static?

**No**, abstract methods cannot be static.

**Reasons:**
- Abstract methods need to be overridden
- Static methods cannot be overridden
- Static methods belong to class, not instance
- Abstract methods are meant for polymorphism

```java
abstract class Example {
    // abstract static void method(); // Compilation error
    abstract void method(); // Correct
}
```

### Can interface extend class?

**No**, interfaces cannot extend classes.

**Rules:**
- Interface can extend other interfaces
- Class can extend other classes
- Class can implement interfaces
- Interface cannot extend classes

```java
class MyClass { }

// interface MyInterface extends MyClass { } // ERROR

interface MyInterface extends AnotherInterface { } // OK
class MyClass extends AnotherClass { } // OK
class MyClass implements MyInterface { } // OK
```

### Is Java 100% object-oriented? (why?)

**No**, Java is not 100% object-oriented.

**Reasons:**
1. **Primitive Data Types** - int, char, boolean, etc. are not objects
2. **Procedural Programming** - Can write procedural code in main()
3. **Static Methods** - Belong to class, not objects
4. **Primitive Operations** - Arithmetic operations on primitives

**What makes it mostly OOP:**
- Everything else is object-oriented
- Wrapper classes for primitives
- Rich class library
- Inheritance, polymorphism, encapsulation supported

```java
// Not object-oriented aspects
int x = 5; // Primitive, not object
static void method() { } // Static method, no object needed

// Object-oriented aspects
String s = new String("Hello"); // Object
List<Integer> list = new ArrayList<>(); // Objects
```

---

**🎯 What Interviewers ACTUALLY CHECK**

**They check whether:**
- ✅ You can explain clearly with examples
- ✅ You understand WHY, not just definitions
- ✅ You can give real-world applications
- ✅ You don't contradict yourself
- ✅ You understand relationships between concepts

**They do NOT expect:**
- ❌ JVM internals and memory management details
- ❌ Complex design patterns
- ❌ Advanced concurrency concepts
- ❌ Framework-specific knowledge

**Total Questions Covered: 150+**

This comprehensive guide covers all OOPS questions with modern formatting, real examples, and interview-ready explanations! 🎯