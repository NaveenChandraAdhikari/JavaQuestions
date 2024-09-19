
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
