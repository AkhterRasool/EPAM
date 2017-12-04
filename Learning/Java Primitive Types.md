# Java Primitive Types #

## 1. Introduction ##
Java is a statically-typed language. This means, one must declare a variable before it can be used. The data type, as the name says, represents the type of value or data stored in a variable. Data types also determine what kind of operations must be performed. They are neither objects nor do they contain states of other primitive data types.

Consider the following lines of code:

```java
int integer_variable = 2;
float float_variable = 2.21f;
char character_variable = 'c';
```

In the above code, we declare three variables of type `int`, `float` and `char` respectively. These data types only accept those values which are compatible with them.
In other words we cannot assign `2.21f` to `character_variable`, likewise `'c'` to `float_variable`. A compile-time error is generated if data types mismatch. However in some cases, we can bypass this by **casting** values to those data types which are compatible.

In Java, there are **8** primitive data types. Each of these types are explained in **Section 2**.

## 2. Primitive Types in Java ## 
The data types are explained as follows:
	
### 1. byte ###
This data type is 8-bit signed two's complement integer. Variables declared of this type occupy **1 byte** of memory.
The range of value is from `-128` (minimum) to `127` (maximum). This type is used to preserve memory occupied by variables.
In memory-critical situations `byte` is endorsed more than `short` or `int`.

### 2. short ###
This data type is 16-bit signed two's complement integer. Variables declared of thus type occupy **2 bytes** of memory.
The range of value is from `-2^15` (minimum) to `2^15 - 1` (maximum). This type is also used to preserve memory occupied by variables.
In memory-critical situations `short` is endorsed more than `int` or `long`.

### 3. int ###
This data type is 32-bit signed two's complement integer. Variables declared of this type occupy **4 bytes** of memory.
The range of value is from `-2^31` (minimum) to `2^31 - 1` (maximum). In Java, to represent unsigned `int` we can make use of **Integer (java.lang.Integer)** class.
For unsigned `int` the range is from `0` (minimum) to `2^64 - 1` (maximum).

### 4. long ###
This data type is 64-bit unsigned two's complement integer. Variables declared of this type occupy **8 bytes** of memory.
The range of value is from `-2^63` (minimum) to `2^63 - 1` (maximum). One should declare variables of type `long` to have variables holding larger values. 

>**Note:** `byte`, `short`, `int` and `long` are used to hold numerical values.

### 5. float ###
This data type is single-precision 32-bit IEEE 754 floating point. Variables declared of this type occupy **4 bytes** of memory.
The range of values of this type is from `1.4E-45` to `3.4028235E38`. One should declare variables of type `float` to conserve memory space rather than declaring them of type `double`.

### 6. double ###
This data type is single-precision 64-bit IEEE 754 floating point. Variables declared of this type occupy **8 bytes** of memory.
The range of values of this type is from `4.9E-324` to `1.7976931348623157E308`. By default, a floating point value is considered as `double` rather than `float`.
One should declare variables of type `double` if obtaining precision is important in comparision to `float`.

>**Note:** `float` and `double` are not used for precise value. Rather one should use **BigDecimal (java.math.BigDecimal)**.

### 7. char ###
This data type is a single 16-bit Unicode character. Variables declared of this type occupy **2 bytes** of memory.
The range of value is from `\u0000` (minimum) to `\uFFFF` (maximum). 

### 8. boolean ###
This data type holds either `true` or `false` as values. The size occupied is not defined. 
It keeps track of values resulting from `true` or `false` conditions.


The following table summarizes the above content:

| Data Type 	| Size (in bytes) | Range 	    			|
|:-------------:|:---------------:|:-----------------------------------:|
|byte       	|1                |-128 to 127      			|
|short      	|2                |-2^15 to 2^15 - 1			|
|int (signed)   |4                |-2^31 to 2^31 - 1			|
|int (unsigned) |4                |0 to 2^32 - 1    			|
|long (signed)  |8                |-2^63 to 2^63 - 1			|
|long (unsigned)|8		  |0 to 2^64 - 1    			|
|float      	|4                |1.4E-45 to 3.4028235E38      	|
|double     	|8                |4.9E-324 to 1.7976931348623157E308	| 
|char       	|2                |\u0000 to \uFFFF 			|
|boolean    	|No size          |true or false    			|


### String ###
Apart from these types, Java also supports another type `String`, which isn't actually a primitive data type but a class. `String` itself contains collection of characters. Often developers create a reference of `String` rather than having an array of character. `String` is immutable in nature which means it cannot be modified. Unlike primitive data types, these are objects themselves.

Example: 

```java

String string_reference = "Collection of characters";

```

Here, `"Collection of characters"` is an object which is referenced by `string_reference`.


## 3. Usage ##
As mentioned earlier, variables must be declared before use. 
When a variable is declared and NOT initialized, JVM automatically assigns default values to them. This means, we can now access those variables. However, we cannot obtain data other than their default values unless we initialize them to different values at the time of declaration or later elsewhere.

Variables as such, are **global** to their respective classes. They may or may not be declared as `static`.

**Local** variables on the other hand, remain local to a block which they're declared in. JVM will not assign default values to these variables. Therefore it's mandatory to assign values to these variables for them to be accessed. A compile-time error will be generated if left un-assigned.

Consider the following program:

```java

1 class PrimitiveTypes {
2 
3         static int global_to_class;
4 
5	  public static void main(String args[]) {
6 
7                 int local_variable = 1;
8 
9                 //int unassigned_variable;
10 
11                System.out.println(global_to_class); // Prints 0
12                System.out.println(local_variable);	// Prints 1
13 
14                //System.out.println(unassigned_variable);
15         }
16 }

```

Here, `local_variable` is assigned to 1 (value other than default value) and therefore can be accessed.

Un-Commenting the line 
```java
9	//int unassigned_variable;
```
won't generate a compile-time error since it's ~~defined~~ **declared** and **not accessed**.
However, un-commenting the line 
```java
14	//System.out.println(unassigned_variable);
```
would result in compile-time error since `unassigned_variable` is being accessed.

Do you think the following line of code would generate compile-time error ?
```java
11	System.out.println(global_to_class);
```
No, it would not, since `global_to_class` is global to it's class and is assigned default value by JVM.

Speaking of default values, the table below describes the default values of data types

|Data type  |Default Value|
|:---------:|:-----------:|
|byte	    |0		  |
|short	    |0		  |
|int	    |0		  |
|long	    |0L		  |
|float	    |0.0f	  |
|double	    |0.0d	  |
|char	    |'\u0000'	  |
|boolean    |false	  |
|String	    |null	  |


## 4. Literals ##
Literals are source code representation of values which variables hold. We shall now discuss literals about various data types.

###  Integer Literals ###
In the following lines of code 
```java
byte byte_variable = 17;
short short_variable = 200;
int integer_variable = 3125;
long long_variable = 412312L;
```
The values assigned are considered as literals.
For `int` a number system can be followed  
**1. Decimal**: It's the number system which we normally use from `0-9`. It's base is 10.  
**2. HexaDecimal**: It's base is 16. The digits consists from `0-9` and `A-F`.  
**3. Binary**: It's base is 2. The digit is either `0` or `1`.  

```java
int decimal_value = 4; //Decimal Number System
int hexadecimal_value = 0x1A // Hexadecimal Number System
int binary_value = 0b00101; // Binary Number System
```

### Floating Point Literals ###
These literals represent floating point values
```java
float float_variable = 3.14f;
double double_variable = 2.22d;
double scientific_notation = 3.415E2;
```

We all are familiar with `3.14f` and `2.22d`, but there's something new with `3.415E2`.
The **E** in `3.415E2` denotes scientific notation. The value which `scientific_notation` holds can also be same as `341.5`.

### Character Literals ###
```java
char a = 'a';
char b = 'b';
char exclamation_mark = '!';
char random_character = '\u000';
```
These are some examples of character literals. However there other characters known as **Escape Sequences** which provide a little more funcitonality.
Some of them are given as follows:  
**\b** : BackSlash  
**\n** : New line  
**\r** : Carriage Return  
**\f** : Form feed

### String Literals ###
Some examples of string literals can be as follows:
```java
String example1 = "Example1";
String example2 = "Example2";
String no_value = null;
```
The `null` value indicates that no value has been assigned. Whether `no_value` is assigned to `null` or not assigned at all, it one and the same.


Another type of literal is the **class** literal. It is formed by following a datatype by `.class`.  
For example: `String.class` is now a class literal.


## References ##
[Oracle Docs-Java Primitive types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)  
[DurgaSoft-Corejava-Basics-Data types in Java](https://www.youtube.com/watch?v=VzrZ9iWiOSM)

## Prepared By ##
Akhter Rasool < akhterrasool48@gmail.com >
