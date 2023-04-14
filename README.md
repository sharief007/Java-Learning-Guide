# Java-17
Java 17 Learning Guide


# Table of Contents

1. [Primitive Types](#primitive-types)
2. [Operators](#operators)
3. [Type Casting](#type-casting)
4. [Wrapper Classes](#wrapper-classes)
5. [String](#string)
    - [String Pool](#string-pool)
    - [String Operations](#string-operations)
    - [String Indexing](#string-indexing)
    - [String Builder](#string-builder)
6. [Switch Keyword](#switch-keyword)
    - [Control Flow](#control-flow)
    - [Switch Expressions](#switch-expression)
    - [Switch Statements](#switch-statement)
 

## Primitive Types

| Data Type | Size | Min Value | Max Value | Default | Comments |
| --- | --- | --- | --- | --- | --- |
| byte | 8 bits | -128 | 127 | 0 |  |
| short | 16 bits | -32,768 | 32,767 | 0 |  |
| int | 32 bits | - 2,147,483,648 (2^31) | 2,147,483,647 (2^31 -1) | 0 |  |
| long | 64 bits | -9,223,372,036,854,775,808 (-2^63) | 9,223,372,036,854,775,807 (2^63 -1) | 0L |  |
| float | 32 bits | 1.4E-45 | 3.4028235E+38 | 0.0F |  |
| double | 64 bits | 4.9E-324 | 1.7976931348623157E+308 | 0.0 |  |
| char | 16 bits | 0 | 65,535 | '\u0000' | [Java Unicodes](https://www.javatpoint.com/unicode-system-in-java) |
| boolean | 1 bit |  |  | false |  |

[Top 🔝](#table-of-contents)

## Operators

| Operator | Precedence |
| --- | --- |
| postfix increment and decrement | ++ -- |
| prefix increment and decrement, and unary | ++ -- + - ~ ! |
| multiplicative | * / % |
| addictive | + - |
| bit shift | << >> >>> |
| relational | < > <= >= instanceof |
| equality | == != |
| bitwise AND | & |
| bitwise exclusive OR | ^ |
| bitwise inclusive OR | \| |
| logical AND | && |
| logical OR | \|\| |
| ternary | ?: |
| assignment | = += -=*= /= %= &= ^= \|= <<= >>= >>>= |

[Top 🔝](#table-of-contents)

## Type Casting

- Smaller types automatically casted to bigger types. 
- byte -> short -> char -> int -> long -> float -> double
- Explicit type casting is required to assign bigger types to smaller ones.
- Beware of overflow while type casting.
- Result of arthmetic operations on types smaller than int is an int.

```java
byte a = 127, b = 5;

// ❌ compilation fails
byte c = a + b;
int d = a + b;  // d = 132

// ⚠️ e is -124 (type overflow, because 127 is the max byte value)
byte e = (byte) (a + b);

// ⚠️ f is 25 ( a/b is 25 because it is an int)
int f = a / b;

// ⚠️ g is 25.0F (result of a/b )
float g = a / b; 

// ⚠️ h is 25.0F (explicitly casted to float, but a/b is still 25)
float h = (float) (a/b);

// ✅ when either a or b
float i = (float) a / b;

// ⚠️ explicit casting is required, because b + 1 is an int
b = (byte) (b + 1);

b++;    // no casting is required for ++ and -- operators

char x = 'x'
char y = ++x;   // arithmetic operations work with char codes
```

## Wrapper classes


## String

- String is a class (not primitive). Its instance represent sequence of characters.
- String object can be instantiated by using *new* keyword. String objcet (It is the only java object which) allows simplified instantiation. It is the recommended way to instantiate a string in java.

```java
char[] text = {'H', 'E', 'L', 'L', 'O'};

String a = new String(text);
String b = new String("Hello");

// simplified instantiation
String c = "Hello";
```

### String Pool

- JVM optimise memory allocated to store String objects by maintaining a *single copy of each String literal* in the [String Pool memory Area](https://www.javatpoint.com/string-pool-in-java), *regardless of how many variables reference this copy*. This process is called interning.
- intern() method is used to get a copy of String literal. 

```java
// All variables point to same reference

String a = "hello";
String b = a;
String c = "hello";
```

![String Interning](./assets/string-pool-in-java.png)

### String operations


### String Indexing


### String Builder



## Switch Keyword

### Control Flow

``` text
switch( <expression> ) {
    case <label>: 
        // logic
    case <label>:
        // logic
    default:
        //logic
}
```

- Switch expression must be of the following types:
byte, short, int, char, String, enum
- Case labels must mactch expression type.
- Execution flow continues until the end of switch unless break is specified for the matching case.
- default case is executed if none of the cases matches the expression. default doesn't need to be the last statement. It is optional i.e, we can omit default case if not necessary.

```java
switch(month) {
    case 1: case 3: case 5: case 7: case 8: case 10: case 12:
        String days = "31 days";
        System.out.println(days);
    case 4: case 6: case 9: case 11:
        // ❌ This is not valid
        // String days = "30 days";  

        // ✅ This is valid
        days = "30 days";
        System.out.println(days);
    case 2:
        if(isLeapYear) {
            days = "29 days";
        } else {
           days = "28 days";
        }
        System.out.println(days);
}
```
- Scope of a varaible is at whole switch statement level, not at case level

### Switch Expression

- Prevents fall through
- Eliminates the need for break statements
- It contains lambda style syntax
- Many labels can be clubbed into a single case separated by commas
- Scope of a variable is the case where it is declared.

```java
switch(month) {
    case 1, 3, 5, 7, 10, 12 -> System.out.println("31 days");
    case 4, 6, 9, 11 -> System.out.println("30 days");
    case 2 -> {
        String days = "28 days";
        if(isLeapYear) {
            days = "29 days";
        } 
        System.out.println(days);
    }
    default -> {
        // ✅ Valid
        String days = "Invalid Month";
        System.out.println(days);
    }
}
```
### Switch Statement

- All cases must return a value. Switch statement ends with a *semicolon*
- For single lines, use lamda style syntax to return value
- For blocks, use *yield* keyword to return a value. yield works only in switch statements.
- Using yield as a varaible outside switch is allowed.

```java
int numberOfDays = switch(month) {
    case 1, 3, 5, 7, 10, 12 -> 31;
    case 4, 6, 9, 11 -> 30;
    case 2 -> {
        if(isLeapYear) {
            yield 29;
        } else {
            yield 28;
        }
    }
    default -> -1;
```