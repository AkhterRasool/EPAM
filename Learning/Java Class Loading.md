# Java Class Loading Mechanism #


# 1. Introduction #

Java is an Object oriented programming language. In Java, all code needs to be encapsulated in a class for execution. When a program’s source code is prepared, the Java compiler compiles the source code and creates a **.class** file which contains byte code. This .class file is sent as input to **Java Virtual Machine (JVM)** which translates it into machine code for execution. The JVM is responsible for loading the class and getting the program ready for execution.

Before we dive into how classes are loaded, we need to understand the components which drive the loading mechanism. 


# 2. Architecture of JVM #


## 2.1 Class Loading Sub System: ##


This component is mainly responsible for loading of .class files. All java classes, interfaces, enum etc, have their own .class files. When a .class file is received as input, this component performs three steps which are as follows:

### 2.1.1 Loading: ###
During loading, a **Class (java.lang.Class)** object is created for all .class files. Since Object is super class of all classes, an additional class object is also created for Object (java.lang.Object) class. 

Each of these Class (java.lang.Class) objects store information about each of these .class files. These Class (java.lang.Class) objects contain methods and variables of actual class, their parent class and are stored in method area of memory. These class objects help developers access members of classes and obtain their method prototypes.

There are three types of class loaders: Bootstrap Loader, Extension Loader and Application Loader which will be explained later.

### 2.1.2 Linking: ###

At this stage, the following steps are performed:

**1. Verfication:**
It ensures whether the byte code is formatted properly and correctly. It ensures security and safety.
If verification fails, a runtime-exception is generated.

**2. Preparation:**
During this step, all static variables are initialised to their default values. For example, default values for int and double are 0 and 0.0 respectively.

**3. Resolution:**
Source code is human-understandable. Computers cannot execute anything but machine code. Therefore, all class words are replaced by their corresponding references in memory to translate the code to machine code.

### 2.1.3 Initialization: ###
During this phase, all static fields of class are initialized to their original values.

## 2.2 Memory Areas: ##
There are five areas in this section:

### 2.2.1 Method area: ### 
These contain Class (java.lang.Class) objects (which contain information about classes).

### 2.2.2. Heap area: ###
The memory pool which contains actual objects.

### 2.2.3 Stack area: ###
For every thread of execution a stack exists. All these stacks reside in the stack area.

### 2.2.4 PC Registers: ###
Each register is for a thread of execution which contains the address of the next instruction.

### 2.2.5 Native method area: ###
It contains stacks for each thread of execution for native methods.
	

## 2.3 Execution Engine: ##

The Execution engine executes each and every line of the source program It is the central part of JVM.

It has the following components: 

### 2.3.1 Interpreter: ###
Executes source program line by line. Not recommended for repitition.

### 2.3.2 JIT Compiler: ###
It generates intermediate code, optimizes it and produces machine code.

### 2.3.3 Garbage Collector, Security Manager: ###
Garbage Collector (GC) collect unreferenced objects from heap memory whereas security manager manages security.


## 2.4 Java Native Interface (JNI): ##
Sometimes native libraries are required for execution. JNI helps in doing so.


## 2.5 Native Libraries: ##
This contains libraries written in native language which help boost performance in performance-critical situations.

# 3. Types of Class Loaders #
The three types of class loaders are explained briefly as follows:

## 3.1 BootStrap Loader: ##
This loader loads all jar files / classes from bootstrap path. The bootstrap path is "jdk/jre/". Prioirty is always given to this loader.

## 3.2 Extension Loader: ## 
This is sub-class of BootStrap Loader. It loads classes from "jdk/jre/lib/etc/" path.
The full class name is "sun.misc.Launcher$Extension.class". This is given second most priority of all loaders.

## 3.3 Application Loader: ##
This is given the least priority of all loaders. It loades classes from working directory. 


# 4. Java Class Loading Mechanism # 

As mentioned earlier, JVM converts byte code present in .class file into machine executable code. It uses **Delegate Hierarchy** algorithm to do so. When a .class file is received as input, JVM checks if the class is loaded or not. 
	If yes, it uses the loaded one otherwise it performs Loading **(2.1.1)**. In this process, all three class loaders **(3.)** receive delegate request from JVM. First, the class is checked in BootStrap Loader, if it doesn't exists it delegates the request to Extension Loader. If it doesn;t exists in Extension Loader, it requests Application Loader to load class.
	If no class is found by any of these loaders, a ClassNotFoundException is thrown. Otherwise the class is loaded followed by Linking **(2.1.2)** and Initialization **(2.1.3)**.

All necessary data are stored in memory areas of JVM which are explained in **2.2**.

Once the class is loaded, the execution engine, which is the central part of JVM, prepares itself to generate optimized machine code (done after generating intermediate code) and generates machine executable code.
	During this process, **Java Native Interface (JNI)** might provide native libraries to Execution engine for fulfilling needs especially in performace-critical sections.



## Reference ##
[Durgasoft Solutions-JVM Architecture](https://www.youtube.com/watch?v=cjC7_ir8Bno&list=PLd3UqWTnYXOkPLxxK5AV_PsJZh2AC5shI)

