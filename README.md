
### Q) How is the Java code that you write executed on the machine/CPU?*
# Java Code Execution Process

This section provides an overview of how Java code is translated into machine-executable code on the CPU, detailing each step in the process.

## 1. Java Code to Bytecode
   - **Java Compiler (`javac`)**:  
     The Java code you write in human-readable format (in `.java` files) is first compiled by the Java compiler, invoked using the command `javac`. The compiler converts the source code into platform-independent bytecode, which is stored in `.class` files.
   - **Compilation Process**:  
     The `javac` compiler analyzes the Java source code and translates it into bytecode instructions. Each `.java` file corresponds to a `.class` file containing the bytecode.

## 2. Bytecode to Machine Code
   - **Java Virtual Machine (JVM)**:  
     The JVM is responsible for executing the compiled bytecode. It translates the bytecode into native machine code that the underlying hardware (CPU) can execute.
   
   ### Key Components of JVM Execution:
   - **Interpreter**:  
     Initially, the JVM uses an interpreter to execute bytecode. The interpreter processes each bytecode instruction one by one, allowing the program to start running quickly, albeit at a slower speed.
   
   - **Just-In-Time (JIT) Compiler**:  
     To improve performance, the JVM uses the JIT compiler to optimize frequently executed bytecode sections (known as "hot spots").
Hotspots are nothing but those portion which need optimisation which executes a lot that needs optimisation eg.a for loop consist of a sum of  million condition but with the help of JIT they are converted to natural number sum formula for easier execution.
These sections are compiled into native machine code for more efficient execution. 
   *Performance doesnot depends upon compiler it is depend upon running of bytecode to machine code. 
   - **Optimized Native Code Execution**:  
     Once the bytecode is converted into native machine code by the JIT compiler, the JVM directly executes the optimized native code on the CPU, similar to how native applications run on a machine.

## Summary
- The Java compiler (`javac`) translates the source code into platform-independent bytecode.
- The Java Virtual Machine (JVM) interprets and/or compiles the bytecode into native machine code.
- The JVM uses a combination of an interpreter and Just-In-Time (JIT) compiler for optimal performance, ensuring the bytecode is efficiently executed on the CPU.
![Java Code Execution Process](./Translate.png)

**Credits :https://www.youtube.com/watch?v=G5a91WqNytI&t=1825s**

### Q) What is JVM?*
JVM stands for Java Virtual Machine it is a Java interpreter.It is responsible for loading,verifying and executing the bytecode created in Java.
Although it is platform dependent which means the software of JVM is diff for diffrent OS it plays a vital role in making Java platform independent.

![Java Code Execution Process](./JVM.png)

### Q) Is Java Platform Independent if then how?*
Yes,Java is PI language.Unlike many programming language javac compiler compiles the program to form a bytecode or .class file.This file is independent of the software or hardware running but needs a JVM file preinstalled in the OS for further execution of the bytecode.
Athough JVM is platform dependent the bytecode can be created on any System and can be executed in any other system despite hardware or software being used which makes Java platform independent.
concise read here:https://www.scaler.com/topics/why-java-is-platform-independent/

### What is the purpose of the String[] args parameter?
The args parameter allows passing command -line argument to the main method when the program is executed.These arguments can be used to provide input or configuration to the program.

### Can there be mutiple main method in a class?
No there can only be one main method with the signature,public static ovid main(String[] args) in a Java class.It serves as the entry point for the program

## Can the main method be overloaded?
Yes the main method can be overloded like any other method in Java.However,only the public static main(String[] args) method is recognized as the entry point by the JVM.
change,type and order of arguments overloads main method
```java
public class MainExample {
    public static void main(String[] args) {
        System.out.println("Standard main method");
        // Call overloaded main methods
        main(5);
        main(args,"Hello");
    }

    // Overloaded main method with an int parameter
    public static void main(String[]args,int arg) {
        System.out.println("Overloaded main method with int: " + arg);
    }

    // Overloaded main method with a String parameter
    public static void main(String arg) {
        System.out.println("Overloaded main method with String: " + arg);
    }
}
```
##Difference between JDK,JRE and JVM?
# Understanding JDK, JRE, and JVM


![Java Code Execution Process](./diff.png)

## Purpose

- **JDK (Java Development Kit)**: Provides tools for developing Java applications, including compilers and debuggers.
- **JRE (Java Runtime Environment)**: Provides the runtime environment to execute Java applications. It includes the JVM and libraries necessary for running Java programs.
- **JVM (Java Virtual Machine)**: Executes Java bytecode and translates it into native machine code. It is responsible for running Java applications.

## Components

- **JDK**:
  - **JRE**: Includes JVM and libraries needed to run Java applications.
  - **Development Tools**: Includes tools like the Java compiler (`javac`), debugger, and other utilities for development.

- **JRE**:
  - **JVM**: The Java Virtual Machine.
  - **Libraries**: Provides the libraries and additional components needed for the runtime environment.

- **JVM**:
  - **Interpreter**: Executes bytecode instructions.
  - **JIT Compiler**: Compiles bytecode to native machine code at runtime for performance optimization.
  - **Garbage Collector**: Manages memory by reclaiming unused objects.
  - **Runtime Libraries**: Provides core libraries used during execution.

## Inclusions

- **JDK**: 
  - Includes the JRE (which includes libraries).
  - Development tools (compiler, debugger, etc.).
  - Libraries for development.

- **JRE**:
  - Includes libraries for the runtime environment.
  - Does not include development tools.

- **JVM**:
  - Does not include libraries or development tools.
  - It is built into the JRE.

## Installation

- **JDK**:
  - Installed separately for Java development and running Java applications.
  - Provides the full suite of development tools and runtime environment.

- **JRE**:
  - Installed separately for running Java applications.
  - Does not include development tools.

- **JVM**:
  - Not installed separately.
  - Built into the JRE.

## Usage

- **JDK**: Required for Java development tasks including writing, compiling, and debugging code.
- **JRE**: Required for running Java applications.
- **JVM**: Required for executing Java programs.

## Summary

- **JDK** is used for development and includes both the JRE and additional tools.
- **JRE** is used to run Java applications and includes the JVM.
- **JVM** is the engine that executes Java bytecode and is included as part of the JRE.

For a Java application to run, you need the JRE (which includes the JVM). For development, you need the JDK (which includes the JRE and additional development tools).




# Why Do We Need Wrapper Classes?

Wrapper classes in Java are used to convert primitive data types into objects. Here are several reasons why they are necessary and useful:

## 1. **Object Requirements**
   - **Primitive Types**: Java’s primitive types (e.g., `int`, `char`, `double`) cannot be used where objects are required. Wrapper classes provide a way to use primitive values as objects.

## 2. **Handling Null Values**
   - **Null Values**: Wrapper classes can be assigned `null`, whereas primitive types cannot. This is useful for situations where you need to represent the absence of a value.

## 3. **Generic Types**
   - **Generics**: Java’s generic types require objects. Wrapper classes allow primitive types to be used with generics, such as in `ArrayList<Integer>`.

## 4. **Collections Framework**
   - **Collections**: The Java Collections Framework (e.g., `List`, `Map`, `Set`) only works with objects. Wrapper classes enable the use of primitive types in these collections.

## 5. **Additional Functionality**
   - **Type Conversion**: Wrapper classes provide methods for converting between different data types. For example, `Integer.parseInt(String)` converts a `String` to an `int`.
   - **String Parsing**: Methods like `Double.parseDouble(String)` and `Boolean.parseBoolean(String)` allow conversion from `String` representations to their respective primitive types.
   - **Value Comparison**: Wrapper classes provide methods to compare values. For example, `Integer.compare(int x, int y)` and `Double.compare(double x, double y)`.


## 6. **Autoboxing and Unboxing**
   - **Autoboxing**: Java automatically converts between primitive types and their corresponding wrapper classes. For example, converting an `int` to `Integer` automatically when adding it to a `List<Integer>`.
   - **Unboxing**: Java also automatically converts from wrapper classes back to primitive types when needed. For example, extracting an `Integer` from a `List<Integer>` and using it as an `int`.

## Summary
Overall wrapper classes are essential in Java for providing OOPS functionality and compatibility with APIs and libraries that require objects rather than primitive data types.They bridge the gap between primitive data types and objects,enabling a wider range of programming scenarios




## **Q:** What is the difference between instance variables and local variables in Java?



### **Instance Variables**
- **Scope**: Accessible throughout the class in which they are declared.
- **Accessibility**: Can be accessed by all methods and constructors in the class.
- **Initialization**: Automatically initialized to default values if not explicitly initialized (e.g., `0` for `int`, `null` for objects).
- **Lifetime**: Exists as long as the object exists.
- **Memory Allocation**: Memory is allocated when an object is created and deallocated when the object is destroyed.

### **Local Variables**
- **Scope**: Accessible only within the block or method where they are declared.
- **Accessibility**: Can only be accessed within the specific method or block.
- **Initialization**: Must be explicitly initialized before use.
- **Lifetime**: Exists only during the execution of the block or method where they are declared.
- **Memory Allocation**: Memory is allocated when the method or block is entered and deallocated when the method or block is exited.

**NOTE:**
Local Variables: Must be explicitly initialized before they are used. This is because local variables are allocated on the stack and their initial values are not automatically set by the JVM. If you try to use a local variable before assigning it a value, the compiler will flag this as an error.

Instance Variables: Unlike local variables, instance variables are automatically initialized to default values if not explicitly set (e.g., 0 for int, null for objects). This is because instance variables are allocated on the heap as part of the object’s state.

ChatGPT

Here’s a comparison of class variables (static variables), instance variables, and local variables in Java, covering their key differences:
1. Class Variables (Static Variables)

    Declaration: Declared with the static keyword inside a class but outside any method.

   ``` java

    public class MyClass {
        static int classVar;
    }
   ```

    Memory Allocation: Allocated once per class when the class is first loaded by the Java Virtual Machine (JVM). They reside in the heap and are shared among all instances of the class.

    Scope and Access:
        Scope: Accessible by all methods and constructors within the class, and can also be accessed using the class name (e.g., MyClass.classVar).
        Access: Can be accessed without creating an instance of the class. However, they can also be accessed via an instance reference.

    Lifetime: Exists for the duration of the class's lifetime, which is the duration of the JVM's runtime.

    Usage: Used for data that is common across all instances, such as constants or shared resources.

2. Instance Variables

    Declaration: Declared inside a class but outside any method, and without the static keyword.

    ```java

    public class MyClass {
        int instanceVar;
    }
    ```

    Memory Allocation: Allocated when an object of the class is created. Each instance of the class has its own copy of instance variables.

    Scope and Access:
        Scope: Accessible by all methods and constructors within the class.
        Access: Must be accessed through an instance of the class (e.g., obj.instanceVar).

    Lifetime: Exists for as long as the object exists. When the object is garbage collected, the instance variables are also collected.

    Usage: Used for data that is unique to each instance of the class, such as the state or attributes of an object.

3. Local Variables

    Declaration: Declared inside a method or a block of code.

```java

public void myMethod() {
    int localVar;
}
```

Memory Allocation: Allocated on the stack when the method or block is executed. They are created when the method is called and destroyed when the method exits.

Scope and Access:

   Scope: Only accessible within the method or block where they are declared.
   Access: Can only be accessed within the method or block where they are declared. Must be initialized before use.

Lifetime: Exists only during the execution of the method or block. They are automatically destroyed when the method or block exits.

Usage: Used for temporary storage of data within a method or block, often for intermediate calculations or to hold temporary results.

## **Q:**  Discuss  Serialization , Deserialization and Externalization

![Overview](./SeriDesiDig.png)

**Serialization**:
- Conversion of a Java object into a static stream(sequence) of bytes,which we can then save to a database or transfer over a network.
                
- Classes that are eligible for serialization need to implement a special marker interface,**Serializable**(A marker interface in Java is an interface that doesn't have any methods or fields).
- The JVM allows special privileges to the class which implements the Serializable Interface.

- Byte Stream is platform-independent.This means once you have a stream of bytes you can convert in into an object and run it on
any kind of environment.

### Marker Interface is empty whats the use of it then ?
Even though the Serializable interface is empty (it has no methods), it plays an important role by acting as a marker to signal the Java Virtual Machine (JVM) and other components that objects of a particular class can be serialized.

Here’s why we use it:
 ## 1. Signaling the JVM:

By implementing Serializable, you are informing the JVM that objects of this class are safe to serialize (convert into a byte stream) and deserialize (reconstruct from the byte stream). Without this marker, the JVM wouldn’t allow the object to be serialized.

   If a class is not marked as Serializable and you attempt to serialize it, the JVM will throw a NotSerializableException.

 ## 2. Maintain Security and Control:

Not all objects should be serialized. By using the Serializable interface, the developer explicitly marks the classes that are safe and meaningful to serialize. This prevents accidental serialization of classes that shouldn't be serialized (like security-sensitive objects).
 ## 3. Custom Serialization Logic:

Once a class implements Serializable, you can still customize its serialization process by overriding special methods like:

   private void writeObject(ObjectOutputStream oos) — to control how the object is written.
   private void readObject(ObjectInputStream ois) — to control how the object is read back.

 ## 4. Backward Compatibility:

By marking a class as Serializable, you ensure that it can be serialized into files, sent over networks, or stored in databases. This enables backward compatibility and data exchange between different versions of software or distributed systems.

 ## 5. Framework Integration:

Many frameworks (e.g., distributed systems like RMI, Hibernate, and messaging systems) require objects to be serializable for remote transmission, caching, or persistence. If your class is not marked Serializable, these frameworks may not work properly with your objects.

### NOTE(MORE CLARIFICATION) : 
Imagine you're playing a video game. The game's progress, like your character's health, score, and inventory, is stored as objects in the game's memory. When you save your game, these objects are serialized into a file. This file can be loaded later to continue your game from where you left off.

Here's another example: When you send an email attachment, the attachment is often serialized into a format like ZIP or RAR. This allows the email to be transmitted over the internet and then reconstructed on the recipient's device.

In essence, serialization is like taking a snapshot of an object and storing it in a way that can be easily transported or saved.

#### A class to be serialized successfully,two conditions must be met-

 - The class must implement the java.io.Serializablt interface
 - All of the fields in the class must be serializable.If a field is not serializable,it must be marked transient.
 - static fields belong to a class(as opposed to an object) and are not serializable.


**Way to convert an object into a stream of Bytes -"ObjectOuputStream" which consists of a method "writeObject"**
**Way to convert stream of Bytes into an object- "ObjectInputStream" which consists of a method "readObject()"**
   ```java
   -FileOutputStream fileOut=new FileOutputStream("/tmp/emplyee.ser");
   ObjectOutputStream out =new ObjectOutputStream(fileOut);
   out.writeObject(e);
   out.close();
   fileOut.close();
```

![OutputStream need fileouputStream](./Ser.png)
**NOTE:private and final field allowed during serialization/desiralisation and transient and static are not allowed they are ignored**

## Deserialization
 - Deserialization is precisely the opposite of serialization.With deserialization you start with a bytestream and recreate the object  you previously serialized in its original state.However you must have the definition of the object(you have to explicitly pass the class when recreating object) to successfully re-create it

```java
FileInputStream fieldIn=new FIleInputStream("/emplyee.ser");
ObjectInputStream in =new ObjectInputStream(fileIn);
e =(Employee).inreadObject();
in.close();
fileIn.close();
```
![OutputStream need fileouputStream](./Desi.png)
credits :https://www.youtube.com/watch?v=nUFoDfGl1II&t=68s


![Serial](https://github.com/user-attachments/assets/5611c612-0450-4bcf-bfde-c4d98a81add4)


## Externalisation:
![Ext](https://github.com/user-attachments/assets/0d8bccca-41c1-431d-bd71-6f6fb36268df)

  
![image](https://github.com/user-attachments/assets/32103a85-5961-4b49-814d-d275d9a4809a)
![image](https://github.com/user-attachments/assets/c5c92af0-de12-462d-972b-f673585a9c57)

## **Q:** Why to use char[] array over  a string for storing passwords in Java?
- 1. Strings are Immutable:

    - Strings in Java are immutable, meaning once created, their content cannot be changed.
    If you store a password as a String, it stays in memory until garbage collection occurs, and since Strings are pooled for reuse, they might stay in memory longer, creating a security risk.
    - With a char[], you can explicitly clear the array (e.g., by overwriting it with zeros) once the password is no longer needed, ensuring it is removed from memory immediately.

- 2. Memory Safety:

    If someone takes a memory dump of your program, a password stored as a String can be easily found in plain text.
    By using a char[], you can overwrite the password, reducing the risk of it being exposed in memory.

- 3. Log File Safety:

    Strings are more prone to being accidentally printed in logs or system outputs.
    Using a char[] avoids this, as arrays are typically printed as object references (e.g., [C@15db9742]), making it harder to leak the actual password.

- 4. Java Recommendation:

    Java itself recommends using char[] for password handling. For example, the method getPassword() in JPasswordField returns a char[], while its older version getText() (which returns a String) has been deprecated for security reasons.

By using char[] for passwords, you gain more control over the data and reduce the chances of accidental exposure.

**NOTE😄To convert override toString()method**

## **Q:** Aggregation,Composition and Association(HAS-A) 
**An association can be considered a generic term to indicate the relationship between two independent classes; the relationship may be one-to-one, one-to-many, or many-to-many, but it need not indicate ownership.**

-- Association is nothing but the relationship between 2 classes : basically of 2 types: aggregation and composition
   --aggregation is weak association or loose coupling i.e one object can live without another object
   --composition is strong association i.e one object cannot live without another object

EXAMPLE:) Driver and car ,both objects can exist independently this is aggregation,they HAS-A relationship but can live independetly
```java
public class Driver{
   private Car car;
}

public class Teams{
List<Plater>players;
}  
```
Example :) Car engine cannot exist without car this is a composition relationship,both objects cannot exist independently.One object cannot exist without owner object;(TIGHT COUPLING)

```java
public class Car{
private Engine engine
}
```
FOR MORE:https://www.geeksforgeeks.org/association-composition-aggregation-java/

## **Q:** Default Capacity Of ArrayList and difference between poll()and remove() ,also difference between ArrayList and Vector?
 - Default capacity of ArrayList id 10
 - poll():
    - Returns the top element of the stack if the stack is not empty.
    - If the stack is empty, returns null.
    - Does not throw an exception if the stack is empty.
- remove():
    - Returns the top element of the stack if the stack is not empty.
    - If the stack is empty, throws an EmptyStackException.

Difference between ArrayList and Vector
    - synchronization – The first major difference between these two. Vector is synchronized and ArrayList isn’t.
    - size growth – Another difference between the two is the way they resize while reaching their capacity. The Vector doubles its size. In contrast, ArrayList increases only by half of its length
    - iteration – And Vector can use Iterator and Enumeration to traverse over the elements. On the other hand, ArrayList can only use Iterator.
    - performance – Largely due to synchronization, Vector operations are slower when compared to ArrayList
    - framework – Also, ArrayList is a part of the Collections framework and was introduced in JDK 1.2. Meanwhile, Vector is present in the earlier versions of Java as a legacy class.

    
## **Q:**In Java, when using HashSet or HashMap with keys, especially when the key is an Integer, we use wrapper classes (like Integer) instead of primitive types (like int).why?

 - 1. Generics Require Objects:

    Both HashSet and HashMap are part of Java’s Collections Framework, which is based on generics.
    Generics in Java work only with objects, not with primitive types. Since int is a primitive type, it cannot be used directly in a generic collection.
    Wrapper classes like Integer allow primitives to be used as objects. So, when you want to use int in a HashMap or HashSet, you must use its wrapper class Integer.

Example:

```java

HashMap<Integer, String> map = new HashMap<>();  // Valid
HashMap<int, String> map = new HashMap<>();      // Invalid (won't compile)
```
 - 2. Autoboxing:

    Java provides autoboxing, which automatically converts a primitive type (like int) to its corresponding wrapper class (like Integer), making it easier for the programmer.
    This allows you to pass primitive values, and Java will internally convert them to objects, but under the hood, only the wrapper object (Integer) is used.

Example:

```java

HashMap<Integer, String> map = new HashMap<>();
map.put(1, "One");  // Autoboxing converts int 1 to Integer(1)
```
 - 3. Methods and Object Functionality:

    Wrapper classes like Integer provide additional methods and functionality that primitives don’t have. For example, you can call Integer.compare(), Integer.hashCode(), and Integer.equals() methods, which are necessary for HashMap and HashSet to function properly (since they rely on hashCode() and equals() for key comparison).
    Primitives like int don’t have methods, so they can’t be used in places where methods like hashCode() are required.

 - 4. HashMap/HashSet Internals:

    HashMap and HashSet rely on the hashCode() method to compute the position of a key in the hash table.
    Since primitive types do not have methods, you need to use the wrapper class (Integer), which provides a proper hashCode() implementation.

 - 5. Null Handling:

    Wrapper classes like Integer can represent null values, while primitive types like int cannot. This is useful when working with HashMap keys, where you might want to allow null as a key.

 Example:
```java
 HashMap<Integer, String> map = new HashMap<>();
 map.put(null, "Null Key");  // Valid, as null is allowed for wrapper classes
```
## **Q:**When to use static and when to use final,also can we override those methods starting with these two keywords?

   **FINAL**:
   - A variable declared as final cannot be reassigned after value is set.
   - A method declared as final cannot be overridden by any subclass.
   - A class declared as final cannot be subclassed or extended
   - No,a final method cannot be overridden in a subclass because the purpose of declaring a method as final is to prevent modification by inheritance
  **STATIC**:
     - A static variable belongs to a class rather than to instances of the class,it is shared among all instances of the class(multiple copies ban sakti hai).
     - A method declared as static belongs to the class,not instances of the class.It can be called without creating an instances of the class.
     - Static method cannot access instance variables or instance methods directly. They can only access static variables and other static methods.
     - In java,only nested classes(inner classes) can be declared as static.A static neested class can be instatiated without creating an instance of the outer class.
     - No,static methods cannot be overriden in the same sense as instance methods.Instead static methods can be hidden bt declaring a method with the same signature in a subclass.This is called method hiding.
     - Example:
```java
class Parent {
    static void show() {
        System.out.println("Parent static method");
    }
}

class Child extends Parent {
    static void show() {
        System.out.println("Child static method");
    }
}

public class Main {
    public static void main(String[] args) {
        Parent.show();  // Calls Parent's static method
        Child.show();   // Calls Child's static method
    }
}
```
   - In this case, you are not actually overriding the method, but rather hiding it. The method is resolved based on the        reference type at compile-time, not at runtime (no polymorphism with static).
   - final methods exhibit dynamic binding (resolved at runtime).
   - static methods exhibit static binding (resolved at compile time).


 **NOTE:CAN FINAL and STATIC be used together?**
 Yes, you can combine final and static for variables or methods:

   - Final static variables: This is often used for constants. A final static variable can only be assigned once and belongs to the class.

```java
public class MyClass {
    public static final int MAX_SIZE = 100;
}
```

   - Final static methods: A method can be both final and static, which means it belongs to the class and cannot be overridden.

```java

public class MyClass {
    public static final void showMessage() {
        System.out.println("Final static method");
    }
}
```
#### SUMMARY:
Final can only be set once, but it still can be set and it can have a different value for each instance. Say you have a car class. Your make and model could be final and set in the constructor. Each new car can have a different make and model, but you can't change their make and model after it is set.

Static variables are specific to the class and are cannot have seperate values for each instance. Your car class can have a car registry. To track all cars ever created, there is a static int that starts at 0 and is incremented by one each time a car is constructed. If this wasn't static, each car would have its own totalCars which would be one, since each instance starts at zero and that gets incremented in the constructor. However, since it is static, it is initialized with the class and each new car increases it by one so that it's value is equal to how many cars have been made.

Static final is for constants. You need to know how fast your cars accelerate due to gravity. This value is set to 9.8. It is static because it doesn't matter which instance, it belongs to the class as a whole and you don't allow the value to be changed, so it can be final.
Final:

- Each instance has its own copy of the field.
- The value cannot be changed after initialization.
- Useful for creating immutable objects.

Static:

- There is only one copy of the field shared by all instances.
- The value can be changed, but it affects all instances.
- Useful for class-level constants or variables that need to be shared across all instances.

## **Q:What are access modifiers?**
CREDITS:**ANUJ BHAIYA** 
![image](https://github.com/user-attachments/assets/b1081fc6-2c77-4cca-bea5-dfb0d9997f12)
![image](https://github.com/user-attachments/assets/6def745b-bac6-4df2-bdbf-0a1892cdf4ee)

Access modifiers in Java control the visibility and accessibility of classes, methods, and variables. Java has four types of access modifiers: public, private, protected, and default (no keyword).

- Default (Package-Private): When no access modifier is specified, the default access is applied. This means that the class, method, or variable is accessible only within the same package but not from other packages.

- Public: Public members are accessible from anywhere, including different packages. This is the most open access level, making the member globally available.

- Private: Private members are only accessible within the class where they are defined. It’s the most restrictive access level and is essential for encapsulation, as it hides implementation details from outside the class.

- Protected: Protected members can be accessed within the same package and also by subclasses, even if they’re in different packages.

At the top level, classes can only be public or default, while member-level entities (methods, fields) can use any of the four.

**WHAT IF A METHOD IN CHILD CLASS IS MORE RESTRICTED THAN A PARENT CLASS**
- In Java, if a method in a child class is more restricted than the corresponding method in its parent class, it will result in a compilation error. This is because Java enforces that you cannot reduce the visibility of an overridden method compared to the method in the parent class.

**Why?**
When a class is extended, the child class should honor the access level defined in the parent class. If you were allowed to reduce the visibility (e.g., make a public method in the parent class private in the child class), it could break the code that relies on accessing the method from outside the child class.

Example:
```java
class Parent {
    public void show() {
        System.out.println("Parent class method");
    }
}

class Child extends Parent {
    // Compilation error: Cannot reduce the visibility of the inherited method
    private void show() {
        System.out.println("Child class method");
    }
}
```
In this case, trying to make show() private in the Child class would result in an error because it has a more restricted access than the public method in Parent.

**Key Rule**:
When overriding a method, the access level must be the same or less restrictive. So, a protected method in the parent class can be overridden as protected or public, but not private. A public method must remain public when overridden.

## **Q:What is Shadowing in Static Methods?**
In Java, shadowing occurs when a subclass defines a static method with the same name and signature as a static method in its parent class. However, static methods are not overridden in the traditional sense. Instead, they are shadowed (or hidden).

Key Points:
Static methods are bound to the class, not to instances.
Shadowing happens when the subclass defines a static method with the same signature as the one in the parent class.
Which method gets called depends on the reference type (not the object type), meaning the method that belongs to the class type of the reference is called, not the class of the actual object.
Example:
```java
class Parent {
    static void show() {
        System.out.println("Parent static method");
    }
}

class Child extends Parent {
    static void show() {
        System.out.println("Child static method");
    }
}

public class Test {
    public static void main(String[] args) {
        Parent obj1 = new Parent();
        Parent obj2 = new Child();

        obj1.show();  // Output: Parent static method
        obj2.show();  // Output: Parent static method (since reference is of Parent)
    }
}
```
In this example, both Parent and Child classes have a static method show(). However, when the method is called through an instance reference of type Parent, the static method in Parent is executed, even if the object is an instance of Child.

Important Notes:
- Static methods are resolved at compile time based on the reference type, not at runtime (unlike instance methods, which use dynamic dispatch).simple se baat hai static onyl cares about class,they did'nt care about where the memory allocated.
- Shadowing does not involve polymorphism, so no method overriding or runtime method selection occurs with static methods.

 **Q Java is pass/callby value of pass/call by reference**

 In Java, all arguments are passed by value, not by reference. However, this concept can sometimes be confusing because of how Java handles primitive types versus objects.

**Key Points**:
- Primitive Types (int, float, etc.): Java passes a copy of the value. Changes made to the parameter inside the method do not affect the original variable.
- Objects (references to objects): Java passes a copy of the reference to the object. So, the reference itself is passed by value. This means you can modify the object's internal state via the reference, but you cannot change the reference to point to a new object outside the method.

Example 1: Pass-by-Value with Primitives
```java

class Test {
    public static void modifyPrimitive(int x) {
        x = 10;  // This only modifies the local copy
    }

    public static void main(String[] args) {
        int a = 5;
        modifyPrimitive(a);
        System.out.println(a);  // Output: 5 (original variable is unchanged)
    }
}
```
Explanation: Here, a is passed as a copy of its value, so modifying x inside modifyPrimitive() does not affect the original value of a.
Example 2: Pass-by-Value with Objects (References)
```java

class Person {
    String name;
    Person(String name) {
        this.name = name;
    }
}

class Test {
    public static void modifyObject(Person p) {
        p.name = "John";  // This modifies the object's internal state
    }

    public static void main(String[] args) {
        Person person = new Person("Alice");
        modifyObject(person);
        System.out.println(person.name);  // Output: John (object's state is modified)
    }
}
```
Explanation: Here, person is passed by value, but what is passed is a copy of the reference to the Person object. Inside the modifyObject() method, we can modify the object's internal state (the name field), and this change reflects outside the method because the reference still points to the same object.
Example 3: Attempting to Change the Object Reference
```java

class Person {
    String name;
    Person(String name) {
        this.name = name;
    }
}

class Test {
    public static void changeReference(Person p) {
        p = new Person("Tom");  // This only changes the local copy of the reference
    }

    public static void main(String[] args) {
        Person person = new Person("Alice");
        changeReference(person);
        System.out.println(person.name);  // Output: Alice (reference is unchanged)
    }
}
```
Explanation: In this case, even though we try to reassign p inside changeReference(), it only affects the local copy of the reference. The original reference person in main() still points to the Person object with the name "Alice".
Summary:
- Java is pass-by-value. For primitives, the value itself is copied. For objects, a copy of the reference is passed. This allows you to modify the object's state inside the method, but you cannot reassign the reference to a new object and have it affect the original reference outside the method.
- Modifying object fields (like p.name = "John";) changes the actual object in memory because both p and person point to the same object.
 - Changing the reference itself (like p = new Person("Tom");) only changes the local reference p inside the method and does not affect the original reference (person) outside the method.


## **Q Equals and HashCode contract in Java?**

- Understanding equals() and hashCode() Contract
In Java, when you override equals(), you must also override hashCode(). The two methods work together, especially when objects are stored in collections like HashSet or used as keys in a HashMap.

 - equals(): Determines if two objects are "meaningfully equal." By default, the equals() method in Java compares memory addresses, which is why two objects, even with the same values, return false if equals() isn't overridden.

- hashCode(): Produces an integer (hash code) that represents the object. If two objects are considered equal according to equals(), they must have the same hashCode().
  
**Key Points for the Contract:**
- If two objects are equal (equals() returns true), they must have the same hashCode().
- If two objects have the same hashCode(), they might not be equal, but it’s recommended to try to avoid this (called a hash collision).Better hash function prevent this.

  **Examples of proper equals()and hashCode() override?**
  
```java
class Employee {
    private int id;
    private String name;

   // Constructor, getters, and setters
    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }

 @Override
    public boolean equals(Object o) {
        // Step 1: Check if the object is compared to itself
        if (this == o) return true;
        // Step 2: Check if the other object is null or of a different class
        if (o == null || getClass() != o.getClass()) return false;
        // Step 3: Typecast the object to compare properties
        Employee employee = (Employee) o;
        // Step 4: Compare id and name (you can add more fields if necessary)
        return id == employee.id && name.equals(employee.name);
    }
    @Override
    public int hashCode() {
        // Combine id and name to produce a unique hash code for proper hashcode overriding as same hashcode does not means equal objects 
        return Objects.hash(id, name);
    }
}
```
**2. Why == and equals() Might Return False for Two Objects with Same Data**
In Java:

==: Compares references, not the actual object content. So, e1 == e2 will return false because they are two different objects in memory, even if they have the same id and name.
equals(): By default, the equals() method also compares references (unless overridden), so e1.equals(e2) also returns false unless we override it to compare object content.
Code Example Before Overriding equals():
```java

Employee e1 = new Employee(1, "John");
Employee e2 = new Employee(1, "John");

// Both of these will return false, even though the id and name are the same
System.out.println(e1 == e2);     // false (compares memory addresses)
System.out.println(e1.equals(e2)); // false (compares references by default)
3. What Happens After Overriding equals()
When we override the equals() method (as shown earlier), we make it compare the content of the objects (in this case, the id and name), instead of just comparing their references.
```

```java
Code Example After Overriding equals():

Employee e1 = new Employee(1, "John");
Employee e2 = new Employee(1, "John");

// Now `equals()` will return true because the objects have the same id and name
System.out.println(e1 == e2);     // false (still compares memory addresses)
System.out.println(e1.equals(e2)); // true (compares content after overriding)
Here’s what’s happening:
```
==: Still returns false because it compares memory locations, and e1 and e2 are different objects.
equals(): Now returns true because we have overridden it to compare the actual id and name values, which are the same for both object

**Q  What happens if you override equals() without overriding hashCode()?**
If you override equals() alone without overriding hashCode(), the objects can be considered equal when you compare them using equals(). However, this can cause problems in hash-based collections like HashMap, HashSet, or Hashtable, where both equals() and hashCode() are used together.

If you override equals() without overriding hashCode(), here's what happens:

Two objects might be considered equal by equals(), but they can still have different hash codes.
In collections like HashSet or HashMap, objects are stored based on their hashCode(), so even if two objects are equal, they might end up in different hash buckets, and the collection will think they are different objects.
Example:
```java

import java.util.HashSet;

class Employee {
    private int id;
    private String name;

    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Employee employee = (Employee) o;
        return id == employee.id && name.equals(employee.name);
    }

    // No hashCode() override
}

public class Test {
    public static void main(String[] args) {
        Employee e1 = new Employee(1, "John");
        Employee e2 = new Employee(1, "John");

        HashSet<Employee> set = new HashSet<>();
        set.add(e1);
        set.add(e2);

        // Both e1 and e2 are equal according to equals(), but different hash codes
        System.out.println(e1.equals(e2));  // Output: true

        // e1 and e2 will both be in the set, even though they are considered equal
        // This is because they have different hash codes
        System.out.println(set.size());  // Output: 2 (should be 1 if equals and hashCode were consistent)
    }
}
```
**SUMMARY**
- If you override equals() but not hashCode(), two objects can be considered equal when compared using equals(). However, they may still have different hashCode() values because the default hashCode() implementation from the Object class is used.

- This can cause problems in hash-based collections like HashSet and HashMap, where both equals() and hashCode() are used. Even though two objects are equal according to equals(), they might be treated as different objects in a hash-based collection because they have different hash codes.

- Therefore, whenever you override equals(), you must also override hashCode() to maintain the contract that equal objects must have the same hashCode().

## **Q All you know about String pool ,String literals etc etc**

We know that String objects can be created in 2 ways:
Using the 'new' operator
Using double-quotes

String s1=new String("hi");
String s2="hi";
When the String is created with the double quotes,JVM searches it for in the string pool; if the same value is found,it returns the reference to that String else creates a new object with the new value provided.

In the other case,if the String is created with the 'new' operator,then JVM creates a new object but not in the string pool.If we want to create the object in the stirng pool,we can use the intern() method.

**What is String constant pool?**
The memory space allocated in the heap memory to store the string literal is called the string constant pool.
No two string objects can have the same value in a string constant pool.
It provides the facility of reusability of the existing string objects.
When a new string object is created using the string literals,the JVM first checks in the pool if this Stirng already exists or not.
If it exists,then it will reference the existing STRING RATHER THAN creating  a new object.
This will help in the speeding up of the application and also help in saving the memory as no 2 objects will have the same content.
```java
Stirng s1="hi";
Strinng s2="hi";
System.out.println(s1==s2); //true;
```
String s1=new String("hi");
what JVM does is that it checks first in the strin pool if "hi" is not present then it creates a copy for reusability purpose.
String pool does not have given any right for GARBAGE COLLECT any of the object becuase of reusability,thats why even not after pointing out by nobody "hi" is present in the stirng pool
########################
String s1="hi";
Stirng s2=new String("hi");
2 objects are created in the above 2 
s1 is created in the string constant pool as it is created by string literals.
s2 is created by new and non new object will be created in string pool as it is already created by s1.

##########################
String s1=new String("code");
here only 2 objects are created 1 in heap and 1 in pool

##########################
String s1=new String("code");
String s2=new String("code");

3 objects will be created 
s1 --> 1 in string pool and in heap 
s2 ---> 1 will be created in heap memory.as the object with the same value is already present in the string constat pool.

" == " compares memory address while .equals comapres the content and as String is a class so equals and hashCode methods overrides 

##############################
intern() method is to put String(which is passed to the intern method) into the string constant pool.
When the intern method is invoked,if the String constant pool already contains a string equal to the String object as determined by the equals(Object)method,the STRING FROM the pool is returned 
Otherwise the string is added to the pool,and a refernce to the Stirng object is returned.

String s1="hi";
String s2=new String("hi");
String s3=s2.intern();
s1 and s3 reference to the same "hi" object in string pool 

##############################
Strings are immutable 
s1="hi";
s1=s1+"hellow";
then hashcode() for both are different as 2 diffrent objects are made in the string pool

## **Q What is Object class?**
Object Class:

    The root of the class hierarchy in Java.
    Every class directly or indirectly inherits from Object.
    Provides fundamental methods for object manipulation and behavior.

Key Methods:

    equals(Object obj): Determines if two objects are equal.
    hashCode(): Generates a unique hash code for an object.
    toString(): Returns a string representation of the object.
    clone(): Creates a copy of the object (if supported by the class).
    getClass(): Retrieves the runtime class of the object.
    notify() and notifyAll(): Wakes up one or all threads waiting on the object's monitor.
    wait(): Causes the current thread to wait until notified or a timeout occurs.

Purpose:

    Serves as a foundation for all other classes.
    Defines common methods and behavior shared by all objects.
    Provides a starting point for custom class implementations.

Usage:

    Inheritance: All classes implicitly inherit from Object.
    Method Overriding: Subclasses can override methods like equals, hashCode, and toString to provide specific implementations.
    Object Comparison: Use equals to compare objects for equality.
    Hashing: Use hashCode for efficient object storage and retrieval in hash-based data structures.
    String Representation: Use toString to debug or display object information.
    Cloning: Use clone to create copies of objects (if supported).
    Synchronization: Use wait, notify, and notifyAll for thread coordination and synchronization.

Additional Notes:

    The finalize method is rarely used and has potential issues. It's generally recommended to use try-with-resources or explicit resource management instead.
    The clone method is protected by default and requires careful implementation to avoid shallow copies.
    The getClass method can be used to obtain runtime type information.

## **Q:Difference between Deepcopy and ShallowCopy?**
Deep Copy vs. Shallow Copy

In Java, when you create a copy of an object, you can either make a deep copy or a shallow copy.

Shallow Copy:

    A shallow copy creates a new object, but the fields of the new object are references to the same objects as the original object.
    If the original object contains references to other objects, the copy will also reference those same objects.
    Changes made to the original object's fields will be reflected in the copy, and vice versa.

Deep Copy:

    A deep copy creates a new object and recursively copies all the fields and their values of the original object.
    If the original object contains references to other objects, the deep copy will create new copies of those objects as well.
    Changes made to the original object's fields or the fields of its nested objects will not affect the copy.

Example:
```Java

class Person {
    private String name;
    private Address address;

    // ...
}

class Address {
    private String street;
    // ...
}

Person originalPerson = new Person("Alice", new Address("123 Main St."));
Person shallowCopy = originalPerson; // Shallow copy
Person deepCopy = originalPerson.deepClone(); // Assuming deepClone() is implemented

// Change the address in the original person
originalPerson.getAddress().setStreet("456 Elm St.");

System.out.println(originalPerson.getAddress().getStreet()); // Output: 456 Elm St.
System.out.println(shallowCopy.getAddress().getStreet()); // Output: 456 Elm St. (shallow copy references the same address)
System.out.println(deepCopy.getAddress().getStreet()); // Output: 123 Main St. (deep copy has its own address)
```
In this example:
    - The shallowCopy references the same Address object as the original person, so changing the address in the original affects the shallow copy.
    - The deepCopy has its own copy of the Address object, so changing the address in the original does not affect the deep copy.

When to Use Deep or Shallow Copies:

    - Shallow copy: When you want to quickly create a new object that shares references to the same objects.
    - Deep copy: When you want to create a truly independent copy of an object, including its nested objects.

**Note**: Java's built-in clone() method typically creates a shallow copy. To create a deep copy, you often need to implement a custom deepClone() method that recursively copies all fields and their values.
      and also Objects using Serialization/Desirialization typically created DeepCopy.

*Fore Clear Example*:https://www.geeksforgeeks.org/difference-between-shallow-and-deep-copy-of-a-class/

## **Q:Different Ways to create an Object in Java**

In Java, objects can be created using several different techniques. These methods differ in how they instantiate the object and how constructors or initialization occurs. Here are the most common ways to create objects:
1. Using the new Keyword

This is the most common way to create an object in Java. The new keyword is followed by a call to the class constructor to create an object in heap memory.

Key Points:

    Constructor is called directly.
    Memory is allocated for the object on the heap.
    Constructor can have parameters.

2. Using Class's newInstance() Method (Reflection)

The newInstance() method of the Class class creates a new instance of a class using reflection. It can either be used with a default constructor or parameterized constructor (in Java 9+).

Key Points:

    Creates an object dynamically at runtime.
    Uses reflection, so the class name may not be known until runtime.
    InstantiationException or IllegalAccessException may be thrown.

3. Using Clone Method

The clone() method is part of the Cloneable interface, and it creates a copy of an existing object.

Key Points:

    clone() copies the values from the original object.
    Shallow copy by default, deep copy requires custom logic.
    Needs to implement the Cloneable interface and override clone() method.

4. Using Deserialization

Deserialization is the process of reading an object from a file or stream and restoring it in memory.

Key Points:

    No constructor is called when an object is deserialized.
    Deserializes from a file/stream into memory.

```java

import java.io.*;

// Define a Car class
class Car implements Cloneable, Serializable {
    String model;
    
    // Constructor
    Car(String model) {
        this.model = model;
        System.out.println("Constructor called: Car model is " + model);
    }
    
    // Default Constructor
    Car() {
        this.model = "Default Model";
        System.out.println("Constructor called: Default Car model");
    }

    // Overriding the clone() method to create a copy of the object
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }

    // toString() to print the reference memory and model
    @Override
    public String toString() {
        return "Car{model=" + model + "}@" + Integer.toHexString(System.identityHashCode(this));
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        // 1. Using the 'new' keyword
        System.out.println("\n--- Using 'new' keyword ---");
        Car car1 = new Car("Tesla Model S");
        System.out.println("Object Reference: " + car1);
        
        // 2. Using Class's newInstance() method (Reflection)
        System.out.println("\n--- Using Class.forName() and newInstance() ---");
        Class<?> carClass = Class.forName("Car");
        Car car2 = (Car) carClass.getDeclaredConstructor().newInstance();
        System.out.println("Object Reference: " + car2);
        
        // 3. Using the clone() method
        System.out.println("\n--- Using clone() method ---");
        Car car3 = (Car) car1.clone();
        System.out.println("Object Reference: " + car3);
        
        // 4. Using Deserialization
        System.out.println("\n--- Using Deserialization ---");
        // Serialize car1 to a file
        FileOutputStream fileOut = new FileOutputStream("car.ser");
        ObjectOutputStream out = new ObjectOutputStream(fileOut);
        out.writeObject(car1);
        out.close();
        fileOut.close();
        
        // Deserialize from the file
        FileInputStream fileIn = new FileInputStream("car.ser");
        ObjectInputStream in = new ObjectInputStream(fileIn);
        Car car4 = (Car) in.readObject();
        in.close();
        fileIn.close();
        
        System.out.println("Object Reference: " + car4);
    }
}
```
**Output Explanation:**

    Using the new Keyword:
        When Car car1 = new Car("Tesla Model S") is executed, the constructor is called, and an object is created in heap memory. The constructor outputs a message, and the memory reference is printed.
        Output:

    Constructor called: Car model is Tesla Model S
    Object Reference: Car{model=Tesla Model S}@<memory reference>

Using Class's newInstance() Method:

    When Car car2 = (Car) carClass.getDeclaredConstructor().newInstance() is executed, the default constructor is called, and a new object is created at runtime using reflection.
    Output:
    Constructor called: Default Car model
    Object Reference: Car{model=Default Model}@<memory reference>

Using the clone() Method:

    When Car car3 = (Car) car1.clone() is executed, the clone() method creates a shallow copy of the car1 object. No constructor is called.
    Output:
    Object Reference: Car{model=Tesla Model S}@<memory reference>

Using Deserialization:

    Deserialization restores the object from a file without calling the constructor. The object reference after deserialization is printed.
    Output:
      Object Reference: Car{model=Tesla Model S}@<memory reference>

## **Q: What is Custom Exception?Difference between Checked and Unchecked Exceptions in java?**
Custom exceptions in Java are user-defined exceptions created by extending the Exception class (for checked exceptions) or RuntimeException class (for unchecked exceptions). They allow developers to create their own exception classes for handling specific application or business logic errors that are not covered by Java’s standard exceptions.

Why use custom exceptions?

    To represent specific errors related to the application domain.
    To make error handling more meaningful and readable.
    To provide additional information or context about the exception.

How to Create a Custom Exception:

    For checked exceptions: Extend the Exception class.
    For unchecked exceptions: Extend the RuntimeException class.

Example of a Custom Exception:

Let’s create a custom exception InvalidAgeException, which is thrown when a user's age is invalid (e.g., below 18).

java

// Custom checked exception
class InvalidAgeException extends Exception {
    // Constructor accepting a custom message
    public InvalidAgeException(String message) {
        super(message);  // Passing the message to the Exception class constructor
    }
}

public class CustomExceptionExample {
    // Method that checks age and throws the custom exception if age is invalid
    public static void validateAge(int age) throws InvalidAgeException {
        if (age < 18) {
            throw new InvalidAgeException("Age is not valid. Must be 18 or older.");
        } else {
            System.out.println("Valid age: " + age);
        }
    }

    public static void main(String[] args) {
        try {
            validateAge(16);  // This will throw an InvalidAgeException
        } catch (InvalidAgeException e) {
            System.out.println("Caught exception: " + e.getMessage());
        }
    }
}

Output:


Caught exception: Age is not valid. Must be 18 or older.

**Runtime vs Compile-time Exceptions (Unchecked vs Checked Exceptions)**

*Java exceptions are divided into two main categories: checked exceptions and unchecked exceptions.*
- 1. Checked Exceptions (Compile-time Exceptions):

    These are exceptions that the compiler checks at compile time.
    They must either be caught using a try-catch block or declared using the throws keyword in the method signature.
    Examples include IOException, SQLException, and ClassNotFoundException.

Characteristics:

  - Checked exceptions represent conditions that the application should anticipate and recover from.
  - If a checked exception occurs, it is required to handle it explicitly during compilation, otherwise, the program won’t compile.

Example:

```java

import java.io.*;

public class CheckedExceptionExample {
    public static void main(String[] args) {
        try {
            FileReader file = new FileReader("nonexistentfile.txt"); // File may not exist
            BufferedReader reader = new BufferedReader(file);
            String line = reader.readLine();
        } catch (IOException e) {
            System.out.println("File not found or could not be opened: " + e.getMessage());
        }
    }
}
```
In the above example, if the file does not exist, an IOException is thrown, which is a checked exception. The compiler forces you to either handle it using try-catch or declare it using throws.
- 2. Unchecked Exceptions (Runtime Exceptions):

    - These are exceptions that occur at runtime and are not checked by the compiler.
    - They are typically caused by programming logic errors like division by zero, accessing an invalid index in an array, or NullPointerException.
    - Examples include NullPointerException, ArrayIndexOutOfBoundsException, ArithmeticException, and IllegalArgumentException.

Characteristics:

    Unchecked exceptions are generally due to bugs or programming mistakes that could be avoided by writing better code.
    The compiler does not force the handling of unchecked exceptions. The application can recover or terminate, but it does not require explicit handling.

Example:

```java

public class UncheckedExceptionExample {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3};
        System.out.println(numbers[3]);  // This will cause ArrayIndexOutOfBoundsException
    }
}
```
In this example, accessing an invalid index in an array results in an ArrayIndexOutOfBoundsException, which is an unchecked exception. The compiler doesn't check for it at compile time, but it will cause a crash at runtime.
## Key Differences Between Runtime (Unchecked) and Compile-time (Checked) Exceptions

| **Aspect**                | **Checked Exceptions**                                     | **Unchecked Exceptions**                           |
|---------------------------|-----------------------------------------------------------|---------------------------------------------------|
| **Exception Type**         | Subclass of `Exception` (excluding `RuntimeException`)     | Subclass of `RuntimeException`                    |
| **Checked by Compiler**    | Yes                                                       | No                                                |
| **Handling Required**      | Must be handled using `try-catch` or `throws`             | Not required to handle explicitly                 |
| **Common Examples**        | `IOException`, `SQLException`, `ClassNotFoundException`   | `NullPointerException`, `ArrayIndexOutOfBoundsException`, `ArithmeticException` |
| **Occurs**                 | Typically due to external factors like file system, network issues | Typically due to programming logic errors        |
| **When Raised**            | At compile-time                                           | At runtime                                        |

Interview Perspective:

    Custom Exception: An interviewer may ask why and when to create custom exceptions. The correct answer involves explaining that custom exceptions are used when standard exceptions do not adequately represent the specific error conditions in your application (e.g., domain-specific errors).
    Checked vs Unchecked Exceptions: Interviewers may ask about the difference between these two. The key point is that checked exceptions must be handled at compile time, whereas unchecked exceptions are runtime errors that the programmer is not forced to handle.

Typical Interview Question:

   When would you prefer using a custom exception?
        - You should use a custom exception when a standard Java exception doesn’t fit your application’s domain, such as validating business logic (e.g., age, email format).
 What is the difference between checked and unchecked exceptions?
        - Checked exceptions must be handled or declared in method signatures, while unchecked exceptions are not checked by the compiler and typically represent programming errors.
## Q**Differnce between this() and super() ? **
# `this` vs `super` in Java

## 1. Basic Definitions:

### `this`:
- Refers to the current instance of the class in which it is used.
- It is used to differentiate between class attributes and parameters or to explicitly reference the current object.

### `super`:
- Refers to the superclass (parent class) of the current object.
- It is primarily used to access methods and constructors of the superclass, allowing the subclass to inherit or modify behavior.

---

## 2. Usage of `this`:

### Accessing Class Members:
`this` is used to refer to instance variables or methods of the current class. It's especially useful when parameter names shadow instance variable names.

```java
class A {
    private int value;
    
    public A(int value) {
        // 'this.value' refers to the instance variable, 'value' refers to the parameter
        this.value = value;
    }

    public void showValue() {
        System.out.println(this.value); // 'this' can be omitted here, but it's more explicit
    }
}
Calling Another Constructor (Constructor Chaining):
this can also be used to call another constructor in the same class. This is called constructor chaining and must be the first statement in the constructor.
```
```java

class B {
    private int x, y;
    
    // Constructor 1
    public B(int x) {
        this(x, 0); // Calls Constructor 2
    }

    // Constructor 2
    public B(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```
- 3. Usage of super:
Accessing Superclass Methods and Variables:
super is used to access members (variables or methods) of the superclass that are hidden or overridden by the subclass.

java
Copy code
class Parent {
    public void display() {
        System.out.println("Display from Parent");
    }
}

class Child extends Parent {
    public void display() {
        System.out.println("Display from Child");
    }
    
    public void show() {
        super.display(); // Calls the superclass method
    }
}
Calling Superclass Constructor:
super is used to call the parent class's constructor. It must be the first statement in the subclass constructor. If not called explicitly, Java automatically inserts a call to the no-argument constructor of the parent class.

```java

class A {
    public A(String message) {
        System.out.println("A's Constructor: " + message);
    }
}

class B extends A {
    public B(String message) {
        super(message); // Calls A's constructor
        System.out.println("B's Constructor");
    }
}
```
## 4. Key Differences: `this` vs `super`

| **Feature**                   | **`this`**                              | **`super`**                                 |
|-------------------------------|-----------------------------------------|---------------------------------------------|
| **Refers to**                  | The current object                     | The parent (superclass) object              |
| **Used in**                    | The class itself                       | The subclass                               |
| **Accesses**                   | Current class members                  | Parent class members                       |
| **Constructor Usage**          | Calls another constructor in the same class | Calls a constructor of the superclass   |
| **Overridden Methods**         | Refers to the current class's method    | Refers to the superclass's method           |
| **Constructor Call Position**  | Can appear anywhere                    | Must be the first statement in constructor  |

- 5. When to Use this and super:
Use this:
When you want to differentiate between instance variables and parameters.
When you need to call another constructor within the same class.
When you explicitly want to reference the current object (e.g., returning this from a method).
Use super:
When you want to call the superclass's constructor.
When you want to access members of the superclass that are overridden or hidden in the subclass.
- 6. Example to Illustrate Both Together:

```java

class Animal {
    String name;

    public Animal(String name) {
        this.name = name;
    }

    public void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    String breed;

    public Dog(String name, String breed) {
        super(name); // Calls the superclass (Animal) constructor
        this.breed = breed; // Refers to the current class (Dog) instance variable
    }

    @Override
    public void sound() {
        super.sound(); // Calls the superclass method
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog("Buddy", "Labrador");
        dog.sound(); // Calls overridden method in Dog
    }
}
Output:
css
Copy code
Animal makes a sound
Dog barks
Explanation:
super(name) calls the parent Animal constructor.
this.breed refers to the Dog class's own field.
super.sound() calls the Animal class's sound method before calling the overridden sound method in Dog.
```
### Additional Notes:
- this() vs super(): Both are constructor calls, but this() is used for constructor chaining within the same class, while super() is for invoking the parent class constructor.
- Implicit vs Explicit: If you don't explicitly call super(), Java automatically calls the parent class's no-argument constructor. If the parent class doesn't have a no-argument constructor, you'll get a compile-- 
  time error unless you explicitly provide a call to a valid constructor.


## Q:Difference between interface and abstract class ,also when to use it ??**

# Interface vs Abstract Class in Java

## 1. Definitions:

- **Abstract Class**: 
  An abstract class is a class that cannot be instantiated directly. It can contain both abstract methods (without a body) and concrete methods (with a body). It is used to provide a base class with some common functionality for derived classes.

- **Interface**: 
  An interface is a reference type in Java, similar to a class, that can contain only abstract methods (before Java 8) and static constants. From Java 8 onwards, interfaces can also contain default and static methods with implementations, but no state (instance variables).

---

## 2. Key Differences:

| **Feature**                       | **Abstract Class**                          | **Interface**                              |
|-----------------------------------|---------------------------------------------|--------------------------------------------|
| **Purpose**                       | To share common code across related classes | To define a contract that unrelated classes can implement |
| **Methods**                       | Can have both abstract and concrete methods | Can have only abstract methods (before Java 8) and default/static methods (from Java 8 onwards) |
| **Inheritance**                   | A class can extend only one abstract class  | A class can implement multiple interfaces  |
| **Fields**                        | Can have instance variables                 | Cannot have instance variables (only constants, `public static final`) |
| **Access Modifiers**              | Methods can have any access modifier        | Methods are `public` by default; no modifiers allowed |
| **Constructors**                  | Can have constructors                       | Cannot have constructors                   |
| **Use of `extends` vs `implements`** | A class uses `extends` to inherit           | A class uses `implements` to adopt         |
| **State Management**              | Can hold state (instance variables)         | Cannot hold state, only constants          |

---

## 3. When to Use Abstract Class vs Interface:

### Use an Abstract Class When:
- You want to provide some **common functionality** to all subclasses, but allow certain methods to be overridden or implemented differently.
- You have **shared state or fields** (like instance variables) that you want to use across subclasses.
- You expect a **clear, hierarchical relationship** between classes. For example, when you have a base class and closely related subclasses (e.g., `Vehicle` as the abstract class, with `Car` and `Bike` as subclasses).

### Use an Interface When:
- You want to define a **contract** that can be implemented by any class, regardless of the class hierarchy (e.g., `Flyable` or `Serializable` interface).
- You need to allow **multiple inheritance** of behavior (Java doesn’t allow multiple class inheritance, but you can implement multiple interfaces).
- You want to ensure that **unrelated classes** follow the same set of rules. For example, `Dog`, `Plane`, and `Bird` could all implement the `Flyable` interface.

---

## 4. Example of Abstract Class:

```java
abstract class Animal {
    String name;

    // Abstract method (must be implemented by subclasses)
    public abstract void sound();

    // Concrete method (optional to override in subclasses)
    public void sleep() {
        System.out.println("This animal is sleeping.");
    }
}

class Dog extends Animal {
    // Must implement the abstract method
    @Override
    public void sound() {
        System.out.println("Dog barks");
    }
}
```
In this example:

Animal is an abstract class that provides a common base for animals.
The Dog class is forced to implement the sound() method but can choose to use the sleep() method as is or override it.
5. Example of Interface:
java
Copy code
interface Flyable {
    void fly(); // Abstract method
}

interface Swimmable {
    void swim(); // Abstract method
}

class Bird implements Flyable, Swimmable {
    @Override
    public void fly() {
        System.out.println("Bird flies");
    }

    @Override
    public void swim() {
        System.out.println("Bird swims");
    }
}
In this example:

Flyable and Swimmable are interfaces that define behaviors.
The Bird class can implement both interfaces, providing concrete behavior for both fly() and swim() methods.
- 6. Java 8 and Later: Interfaces with Default Methods:
From Java 8, interfaces can also have default methods with implementations.

```java
Copy code
interface Walkable {
    default void walk() {
        System.out.println("Walking on two legs");
    }
}

class Human implements Walkable {
    // Inherits the default walk() method
}
```
In this case, the Human class inherits the walk() method from the Walkable interface without the need to implement it.
############################################################################################################################################################
- Use an abstract class when you have a common base for related classes, especially when you need to share code or state (instance variables).
- Use an interface when you want to define a contract that can be applied across unrelated classes or when you need to achieve multiple inheritance.
- By understanding when to use each, you can structure your code more effectively, encouraging code reusability and flexibility.
 ##############################################################################################################################################################


**Q:ABOUT EXCEPTIONS**
CREDITS : https://www.baeldung.com/java-global-exception-handler
