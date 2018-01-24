# Basic Data Types

1. Go’s types fall into four categories: basic types, aggregate types, reference types, and interface types. 
2. Basic types include numbers, strings, and booleans. 
3. Aggregate types — arrays and structs form more complicated data types by combining values of several simpler ones.
4. Reference types are a diverse group that includes pointers, slices, maps, functions, and channels, but what they have in common is that they all refer to program variables or state indirectly, so that the effect of an operation applied to one reference is observed by all copies of that reference.

## Integers
1. Regardless of their size, `int`, `uint`, and `uintptr` are different types from their explicitly sized siblings. Thus `int` is not the same type as `int32`, even if the natural size of integers is 32 bits, and an explicit conversion is required to use an int value where an `int32` is needed, and vice versa.
2. The type `rune` is an synonym for `int32` and conventionally indicates that a value is a Unicode code point.
3. The type `byte` is an synonym for `uint8`, and emphasizes that the value is a piece of raw data rather than a small numeric quantity.
4. In Go, the sign of the remainder is always the same as the sign of the dividend, so `-5%3` and`-5%-3` are both `-2`
5. Thebehaviorof/ depends on whether its operands are integers, so 5.0/4.0 is 1.25, but 5/4 is 1 because integer division truncates the result toward zero.
4. If the result of an arithmetic operation, whether signed or unsigned, has more bits than can be represented in the result type, it is said to overflow. The high-order bits that do not fit are silently discarded.
5. The operator `^` is bitwise exclusive OR (XOR) when used as a binary operator, but when used as a unary prefix operator it is bitwise negation or complement; that is, it returns a value with each bit in its operand inverted.
6. The `&^` operator is bit clear (AND NOT): in the expression `z = x &^ y`, each bit of `z` is `0` if the corresponding bit of `y` is `1`; otherwise it equals the corresponding bit of `x`.
7. It uses Printf’s `%b` verb to print a number’s binary digits; 08 modifies %b (an adverb!) to pad the result with zeros to exactly 8 digits.
8. Left shifts fill the vacated bits with zeros, as do right shifts of unsigned numbers, but right shifts of signed numbers fill the vacated bits with copies of the sign bit. For this reason, it is important to use unsigned arithmetic when you’re treating an integer as a bit pattern.
9. unsigned numbers tend to be used only when their bitwise operators or peculiar arithmetic operators are required, as when implementing bit sets, parsing binary file formats, or for hashing and cryptography. They are typically not used for merely non-negative quantities.
10. Integer literals of any size and type can be written as ordinary decimal numbers, or as octal numbers if they begin with `0`, as in `0666`, or as hexadecimal if they begin with `0x` or `0X`, as in `0xdeadbeef`.
11. When printing numbers using the fmt package, we can control the radix and format with the `%d`, `%o`, and `%x` verbs
12. Rune literals are written as a character within single quotes.Runes are printed with `%c`, or with `%q` if quoting is desired.

## Floating-Point Numbers
1. A float32 provides approximately six decimal digits of precision, whereas a float64 provides about 15 digits. float64 should be preferred for most purposes because float32 computations accumulate error rapidly
2. Floating-point values are conveniently printed with Printf’s %g verb, which chooses the most compact representation that has adequate precision, but for tables of data, the %e (exponent) or %f (no exponent) forms may be more appropriate.
3. The function `math.IsNaN` tests whether its argument is a not-a-number value, and `math.NaN` returns such a value. 
4. Any comparison with NaN always yields false:

      ```
      nan := math.NaN()
      fmt.Println(nan == nan, nan < nan, nan > nan) // "false false false"
      ```
 
 ## Complex Numbers
 1. The built-in function `complex` creates a complex number from its real and imaginary components, and the built-in `real` and `imag` functions extract those components.
 2. If a floating-point literal or decimal integer literal is immediately followed by `i`, such as `3.141592i` or `2i`, it becomes an imaginary literal, denoting a complex number with a zero real component.
 3. Under the rules for constant arithmetic, complex constants can be added to other constants (integer or floating point, real or imaginary), allowing us to write complex numbers naturally, like `1+2i`, or equivalently, `2i+1`.
 
## Booleans
1. There is no implicit conversion from a boolean value to a numeric value like 0 or 1, or vice versa.

## Strings
1. The built-in `len` function returns the number of bytes (not runes) in a string, and the index operation `s[i]` retrieves the `i`-th byte of string `s`
2. Strings may be compared with comparison operators like `==` and `<`; the comparison is done byte by byte, so the result is the natural lexicographic ordering.
3. Since strings are immutable, constructions that try to modify a string’s data in place are not allowed. Immutability means that it is safe for two copies of a string to share the same underlying memory, making it cheap to copy strings of any length. Similarly, a string s and a substring like `s[7:]` may safely share the same data, so the substring operation is also cheap. No new memory is allocated in either case.
4. A raw string literal is written ``...``, using backquotes instead of double quotes. Within a raw string literal, no escape sequences are processed


