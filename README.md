# Java-17
Java 17 Learning Guide


# Table of Contents

1. [Primitive Types](#primitive-types)
2. [Operators](#operators)
3. [Type Casting](#type-casting)



## Primitive Types

| Data Type | Size | Min Value | Max Value | Default | Comments |
| --- | --- | --- | --- | --- | --- |
| byte | 8 bits | -128 | 127 | 0 |  |
| short | 16 bits | -32,768 | 32,767 | 0 |  |
| int | 32 bits | - 2,147,483,648 (2^31) | 2,147,483,647 (2^31 -1) | 0 |  |
| long | 64 bits | -9,223,372,036,854,775,808(-2^63) | 9,223,372,036,854,775,807(2^63 -1) | 0L |  |
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