## Java Basics
- [Java Basics](#java-basics)
  - [Basic concepts](#basic-concepts)
      - [1. Charasterics of Java language](#1-charasterics-of-java-language)
      - [2. Differences between object-oriented and procedural programming](#2-differences-between-object-oriented-and-procedural-programming)
      - [3. Three characteristics of OOP](#3-three-characteristics-of-oop)
      - [4. Similarities and Differences between interfaces and abstract classes](#4-similarities-and-differences-between-interfaces-and-abstract-classes)
      - [5. Exception](#5-exception)
      - [6. Serialization and Deserialization](#6-serialization-and-deserialization)
  - [Collections](#collections)
      - [1. Why Collection?](#1-why-collection)
      - [2. List, Set, Queue and Map](#2-list-set-queue-and-map)
  - [Concurrency](#concurrency)
      - [1. Process and Thread](#1-process-and-thread)
      - [2. Lifecycle and Status of Threads](#2-lifecycle-and-status-of-threads)
      - [3.Context switching](#3context-switching)
      - [4. Thread Deadlock](#4-thread-deadlock)
### Basic concepts
##### 1. Charasterics of Java language
    a)Easy to learn
    b)Object Oriented(encapsulation, inheritance, polymorphism)
    c)Java Virtual Machine provides platform independence
    d)Java provides built-in support for multithreading
##### 2. Differences between object-oriented and procedural programming
```Procedural programming breaks down the process of problem-solving into a series of methods that are executed one after the other to solve the problem.```

```Object-oriented programming, on the other hand, begins by abstracting the problem into objects, and then uses methods that are executed by these objects to solve the problem.```
##### 3. Three characteristics of OOP
***Encapsulation***
```Encapsulation refers to the process of hiding an object's state information (i.e., its properties) inside the object, which prevents external objects from accessing the object's internal information directly. However, encapsulation does allow for the provision of methods that can be accessed by external objects to manipulate the object's properties.```

***Inheritance***
```By using inheritance, new classes can be created quickly, which increases code reuse, program maintainability, and saves a lot of time in creating new classes, thus improving development efficiency. ```

**Notes:**
```a)Subclasses have all the properties and methods of the parent class (including private properties and methods), but the subclass cannot access the private properties and methods of the parent class, only inherit them.```

```b)Subclasses can have their own properties and methods, which means they can extend the parent class.```

```c)Subclasses can implement the methods of the parent class in their own way.```

***Polymorphism***
```Polymorphism, as the name suggests, means that an object has multiple states, which is expressed by a reference to a parent class that points to an instance of a child class.```

```The characteristics of polymorphism are: ```
```a)There is an inheritance (class) / implementation (interface) relationship between the object type and the reference type; ```

```b)The method called by the reference type variable must be determined during runtime; ```

```c)polymorphism cannot call a method that only exists in the child class but not in the parent class; ```

```d)If the child class overrides a method of the parent class, the overridden method in the child class will be executed, and if the child class does not override the method of the parent class, the method in the parent class will be executed.```

##### 4. Similarities and Differences between interfaces and abstract classes
***Similarities:***
    
    a)Neither can be instantiated.
    b)Both can contain abstract methods.
    c)Both can have default implementations of methods

***Differences:***

```a)Interfaces are primarily used to constrain the behavior of classes, and if you implement an interface, you will have the corresponding behavior. Abstract classes are primarily used for code reuse and emphasize ownership relationships. A class can only inherit one class, but it can implement multiple interfaces.```

```b)The member variables in an interface can only be public static final, cannot be modified and must have an initial value, while the member variables in an abstract class are default by default, can be redefined in a subclass, and can be reassigned.```

##### 5. Exception
>Throwable

>>Exception
>>>Checked Exception
>>>>IOException
>>>>ClassNotFoundException
>>>>...

>>>Unchecked Exception
>>>>ArthmeticException
>>>>INdexOutOfBoundsException
>>>>...

>>Error
>>>OutOfMemoryError
>>>StackOverFlowError
>>>IOError
>>>...

***Differences between Exception and Error:***
```Exception: An exception that can be handled by the program itself and caught using try-catch blocks. Exceptions can be further divided into Checked Exceptions (must be handled) and Unchecked Exceptions (need not be handled).```

```Error: An error that cannot be handled by the program itself, and we do not catch it using try-catch blocks. For example, Virtual MachineError, OutOfMemoryError, NoClassDefFoundError, etc. When these errors occur, the Java Virtual Machine (JVM) generally terminates the thread.```
##### 6. Serialization and Deserialization
```When we need to persist Java objects, such as saving Java objects to a file or transmitting Java objects over a network, we need to use serialization. ```
```In simple terms, serialization is the process of converting a data structure or object into a binary byte stream, while deserialization is the process of converting the binary byte stream generated during serialization back into a data structure or object.```
    
    Common use cases for serialization and deserialization:

```a)Before an object is transmitted over a network (such as during remote method invocation RPC), it needs to be serialized, and after receiving the serialized object, it needs to be deserialized. ```

```b)Before storing an object in a file, it needs to be serialized, and when reading an object from a file, it needs to be deserialized. ```

```c)Before storing an object in a database (such as Redis), serialization is required, and deserialization is needed when retrieving the object from the cache database. ```

```d)Serialization is also needed before storing an object in memory, and deserialization is needed when reading the object from memory.```
### Collections
##### 1. Why Collection?
```When we need to save a group of data with the same type, we should use a container to store it. This container is an array. However, using arrays to store objects has certain drawbacks. In actual development, the data types that need to be stored are diverse. Therefore, "collections" are used to store multiple data. The disadvantage of arrays is that once they are declared, their length cannot be changed. At the same time, the data type declared for the array determines the type of data that can be stored in the array. Furthermore, the data stored in arrays is ordered and repeatable, which limits its use. However, collections increase the flexibility of data storage. Java collections can not only be used to store objects of different types and quantities, but can also store data with mapping relationships.```
##### 2. List, Set, Queue and Map
```a)List (a handy tool for dealing with order): stores elements in an ordered and repeatable manner. ```

```b)Set (emphasizes uniqueness): stores elements in an unordered and non-repeatable manner. ```

```c)Queue (a call machine that implements queuing functions): determines the order of precedence according to a specific queuing rule, and stores elements in an ordered and repeatable manner. ```

```d)Map (an expert in searching using keys): stores key-value pairs, similar to the mathematical function y=f(x), where "x" represents the key and "y" represents the value. Keys are unordered and non-repeatable, while values are unordered and repeatable. Each key can map to at most one value.```
### Concurrency
##### 1. Process and Thread
***Process:***
```A process is an execution of a program, and it is the basic unit for a system to run programs, so a process is dynamic. Running a program on a system is the process of creating, running, and terminating a process. In Java, when we start the main function, we are actually starting a JVM process, and the thread where the main function is located is one of the threads in this process, also known as the main thread.```

***Thread:***
```Threads are similar to processes, but they are smaller units of execution. A process can generate multiple threads during its execution. Unlike processes, multiple threads of the same type share the heap and method area resources of the process, but each thread has its own program counter, virtual machine stack, and native method stack. Therefore, when the system generates a thread or switches between threads, the burden is much lighter than that of a process. Because of this, threads are also called lightweight processes.```
##### 2. Lifecycle and Status of Threads
```NEW: the initial state where the thread is created but not yet called start(). ```

```RUNNABLE: the running state where the thread is called start() and waiting to run. ```

```BLOCKED: the blocking state where the thread needs to wait for a lock to be released. ```

```WAITING: the waiting state where the thread needs to wait for some specific action (notification or interruption) from other threads. ```

```TIME_WAITING: the timeout waiting state where the thread can return after a specified time rather than waiting indefinitely like WAITING. ```

```TERMINATED: the terminated state where the thread has finished running.```
##### 3.Context switching
```During the execution of a thread, it will have its own running conditions and states (also known as context), such as the program counter and stack information mentioned above. When the following situations occur, the thread will exit from the CPU occupancy state. ```

```a)It voluntarily yields CPU, such as by calling sleep(), wait(), etc. ```

```b)The time slice is used up, because the operating system prevents a thread or process from occupying the CPU for a long time, causing other threads or processes to starve. ```

```c)A blocking type of system interrupt is called, such as an IO request, which blocks the thread. ```

```d)Being terminated or ending execution.```

```The first three of which will result in a thread switch. Thread switching means that the current thread's context needs to be saved and left to resume the next time the thread occupies the CPU. And load the context of the next thread that will occupy the CPU. This is what is called a context switch.```
##### 4. Thread Deadlock
```'Thread deadlock' describes a situation where multiple threads are blocked, with one or all of them waiting for a resource to be released. Because the threads are blocked indefinitely, the program cannot terminate normally.```

***Four necessary conditions for deadlock:***

```a)Mutual exclusion: The resource can only be occupied by one thread at a time.```

```b)Hold and wait: A thread holds on to resources while waiting for others.```

```c)No preemption: Resources cannot be forcibly taken away from a thread that is holding them until it releases them.```

```d)Circular wait: Several threads form a circular chain waiting for resources.```

***How to prevent deadlock:***
```a)Break the "request and hold" condition: Request for all resources at once. ```

```b)Break the "non-preemption" condition: If a thread that occupies some resources can't acquire additional resources, it should release the resources it's holding. ```

```c)Break the "circular wait" condition: Use a certain order for acquiring resources, and release them in the reverse order.```