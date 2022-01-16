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