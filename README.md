# Java-17
Java 17 Learning Guide


# Table of Contents

1. [Primitive Types](#primitive-types)
2. [Operators](#operators)



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