# Java Primitive Types #

## 1. Introduction ##
Java is a statically-typed language. This means, one must declare a variable before it can be used. The data type, as the name says, represents the type of value or data stored in a variable. Neither it is an object nor does it contains states of other primitive data types.

For instance, 

```java
int integer_variable = 2;
float float_variable = 2.21f;
char character_variable = 'c';
```

In the above code, we declare three variables of type `int`, `float` and `char` respectively. These data types only accept those values which are compatible with them.
In other words we cannot assign `2.21f` to `character_variable` likewise `'c'` to `float_variable`. A compile error is generated if data types mismatch. However in some cases, we can bypass this by casting values to those data types which are compatible.

In Java, there are **8** primitive data types. Each of these types are explained in **Section 2**.

## 2. Primitive Types in Java ## 
The data types are explained as follows:
	
### 1. byte ###
This data type is 8-bit signed two's complement integer. Variables declared of this type occupy **1 byte** of memory.
The range of value is from -128 (minimum) to 127 (maximum). This type is used to preserve memory occupied by variables.
In memory-critical situations `byte` is endorsed more than `short` or `int`.

### 2. short ###
This data type is 16-bit signed two's complement integer. Variables declared of thus type occupy **2 bytes** of memory.
The range of value is from -2^15 (minimum) to 2^15 - 1 (maximum). This type is also used to preserve memory occupied by variables.
In memory-critical situations `short` is endorsed more that `int` or `long`.

### 3. int ###
This data type is 32-bit signed two's complement integer. Variables declared of this type occupy **4 bytes** of memory.
The range of value is from -2^31 (minimum) to 2^31 - 1 (maximum). In Java, to represent unsigned `int` we can make use of **Integer (java.lang.Integer)** class.
For unsigned `int` the range is from 0 (minimum) to 2^64 - 1 (maximum).

### 4. long ###
This data type is 64-bit unsigned two's complement integer. Variables declared of this type occupy **8 bytes** of memory.
The range of value is from -2^63 (minimum) to 2^63 - 1(maximum). We should declare variables of type `long` when we require them to hold large values.

>**Note:** `byte`, `short`, `int` and `long` are used to hold numerical values.

## 5. float ###
This data type is single-precision 32-bit IEEE 754 floating point. Variables declared of this type occupy **4 bytes** of memory.
The range of values of this type is not known as of now. One should declare variables of type `float` to conserve memory space rather than declaring them of type `double`.

### 6. double ###
This data type is single-precision 64-bit IEEE 754 floating point. Variables declared of this type occupy **8 bytes** of memory.
The range of values of this type is not known as of now. By default a floating point value is considered as `double` rather than `float`.
One should declare variables of type `double` if obtaining precision is important in comparision to `float`.

>**Note:** `float` and `double` are not used for precise value. Rather one should use **BigDecimal java.math.BigDecimal**.

### 7. char ###
This data type is a single 16-bit Unicode character. Variables declared of this type occupy **2 bytes** of memory.
The range of value is from '\u0000' (minimum) to '\uFFFF' (maximum). 

### 8. boolean ###
This data type holds either `true` or `false` as value. The size occupied is not defined. 
It keeps track of values resulting from `true` or `false` conditions. 

## References ##
[Oracle Docs-Java Primitive types](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)
[DurgaSoft-Corejava-Basics-Data types in Java](https://www.youtube.com/watch?v=VzrZ9iWiOSM)

## Prepared By ##
Akhter Rasool < akhterrasool48@gmail.com >
