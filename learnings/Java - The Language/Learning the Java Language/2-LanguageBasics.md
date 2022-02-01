- [Variables](#variables)
  - [Types of variables](#types-of-variables)
- [Primitive Data Types](#primitive-data-types)
  - [Literals](#literals)
    - [Integer Literal](#integer-literal)
    - [Floating-point Literal](#floating-point-literal)
    - [Character and String Literals](#character-and-string-literals)
    - [Class literal](#class-literal)
- [Arrays](#arrays)
- [Adhoc](#adhoc)
- [Operators](#operators)
- [Control Flow Statements](#control-flow-statements)
  - [Branching statements](#branching-statements)

# Variables

- Can be unlimited length
- Unicode supported
- Must start with alpha, `_` or `$`. Subsequesnt characters can contain all of previous and digits as well.
- Space not allowed

## Types of variables 
- Instance Variables (Non-Static Fields)
- Class Variables (Static Fields)
- Local Variables
- Parameters

# Primitive Data Types

7 primitive types are
- byte - 8-bit signed 2's complement integer.
- short - 16-bit singed 2's complement.
- int - default and 32-bit signed 2's complement (also supports unsigned). `Integer` class supports unsigned 32-bit (starting Java 8); use the `*Unsigned` methods from class for the same.
- long - 64-bit signed 2's complement (also supports unsigned). Starting Java 8, Long has methods for unsigned arithematic operations.
- float - 32-bit single precision IEEE 754 floating point. 
  - For currency using `java.math.BigDecimal` instead.
- double - 64-bit single precision IEEE 754 floating point.
- boolean - represents 1-bit of information but size isn't preciously defined.
- char - 16-bit Unicode character. Range from `'\u0000'` to `'\uffff'` (65,535 inclusive).

## Literals

A *literal* is the source code representation of a fixed value; literals are represented directly in your code without requiring computation

### Integer Literal

- defaults to int. 
- use `L` (recommended) or `l` for Long literals
- Supported Number Systems 
  - Decimal (Base 10)
  - Hexadecimal (Base 16) - starts with `0x`; example - `int hexVal = 0x1a;` for 26
  - Binary (Base 2) - starts with `0b`; example - `int binVal = 0b11010;` for 26
- can use `_` as number separator for more code-readibility. Example `123_456_789` is similar to 123,456,789
  - can't be at beginning or end of number
  - can't be adjacent to decimal point in floating point literal
  - prior to `L` or `F` suffix
  - in position where a string of digits is expected
  - can't be in between radix prefix, example `int x4 = 0_x52;`

### Floating-point Literal

- type float if declared with `f` or `F`, defaults to double.
- use `_` for separator for readibility.
- can be expressed using `E` or `e` for scientific notations
  ```
  double d1 = 123.4;
  // same value as d1, but in scientific notation
  double d2 = 1.234e2;
  float f1  = 123.4f;
  ```

### Character and String Literals

- can contain UTC-16 chars. Can contain directly or escaped like, `'\u0108'`

### Class literal

- append `.class` to end. Example `String.class`

# Arrays

- container to hold fixed number of elements
- to copy arrays, use `System.arraycopy()` method or `java.util.Arrays.copyOfRange()` (latter doesn't require creating dest. array before copying.)

# Adhoc

- A type's (aka class's) fields, methods, and nested types are collectively called its **members**..

# Operators

* Unary `+` and `-`, i.e `x=+10` and `x=-10` assign `10` and `-10` to x respectively. 
* Postfix `++` and `--` has higher precedence than prefix
* `instanceof` is an operator.
* `null` is not instance of anything
* `<<` shifts bits to left with 0's filled to the right, thus multiply by 2.
* `>>` shits bits to the right and fills 1 to the left-most bits, signed divide by 2.
* `>>>` shits bits to the right and fills 0 to the left-most bits, ie it's unsigned divide by 2.
* Unary `~` is the Bit complement operator.  Thus it behaves as **complement, increment**
  
  Bit complement is calculated as described in the [Stack Overflow](https://stackoverflow.com/questions/791328/how-does-the-bitwise-complement-operator-tilde-work) question.

  Negative numbers are represented as 2's complement in the memory. 2's complement is obtained by inverting all bits and adding 1 to it. Thus -2 is represented in memory as (8-bit style) `1111 1110`. We get it as follows 
  ```
  0000 0010 // for 2
  1111 1101 // invert bits (aka the 1's complement)
  0000 0001 // add 1
  1111 1110 // answer
  ```

  Finding ~10
  ```
  // flip the bits of 10
  0000 1010 // for 10
  1111 0101 // this number is the value of ~10, ie complement of 10

  // now the above number is -ve no. as MSB (most significant bit) is 1.
  // Let's find it.
  // we get binary rep of a number by flipping bits and adding 1. 
  // thus to get the number back, we need to subtract 1 and flip bits. 
  // i.e. add -1 and flip bits. 

  // find binary rep of -1
  0000 0001 // for 1
  1111 1110 // 1's complement
  1111 1111 // add 1. This is -1

  // Add -1 to the bit rep of ~10
  1111 1111 // -1 
  1111 0101 // ~10, adding in next step
  1111 0100 // the last carry bit is lost cause of 8 bit, flip bits next
  0000 1011 // this is 11

  // Thus the bit representation of ~10 is the representation of -11
  // Hence ~10 => -11
  ```

# Control Flow Statements

* `if`
* `if... else`
* `switch` - holds for `char`, `byte`, `short`, `int`, `Integer`, `Character`, `Byte`, `Short`, Enum and String
  * Take note of fall-through in case of missing `break;`.
* `while`
* `do...while`
* `for`
* `for`-each - applicable for Collections and arrays only.

## Branching statements
* The `break` stetament has 2 types
  * unlabeled => The most common type we see in switch.
  * labeled => in the below example, `search` is a label for the outer `for` loop. As a result, when the break occurs, the flow is transferred to the statement following the statement that is labeled (the outer `for` in this case).
    ```java
    search:
    for (i = 0; i < arrayOfInts.length; i++) {
        for (j = 0; j < arrayOfInts[i].length;
              j++) {
            if (arrayOfInts[i][j] == searchfor) {
                foundIt = true;
                break search;
            }
        }
    }

    // after break, control comes here. Not at the beginning of the loop. 
    ```
* The `continue` also has labeled and unlabeled forms.
  * A labeled continue statement skips the current iteration of an outer loop marked with the given label.
  ```java
  test:
  for (int i = 0; i <= max; i++) { // iteration of this loop will be skipped on calling continue with the label
      int n = substring.length();
      int j = i;
      int k = 0;
      while (n-- != 0) {
          if (searchMe.charAt(j++) != substring.charAt(k++)) {
              continue test;
          }
      }
      foundIt = true;
          break test;
  }
  ```
* `return` statement - can return a value or no value.