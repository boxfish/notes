# 2 Program Structure

## 2.1 Names
1. Go programmers use "camel case" when forming names by combining words
2. The letters of acronyms and initialisms like ASCII and HTML are always rendered in the same case. e.g. escapeHTML, not escapeHtml

## 2.2 Declarations
1. If an entity is declared within a function, it is local to that function. 
2. If declared outside of a function, however, it is visible in all files of the package to which it belongs. 
3. If the name begins with an upper-case letter, it is exported, which means that it is visible and accessible outside of its own package and may be referred to by other parts of the program.

## 2.3 Variables
1. `var name type = expression`: 
    * if the type is ommited, it is determined by the initializer expression.
    * if the expression is omitted, the initial value is the zero value for the type, which is 0 for numbers, false for booleans, "" for strings, and nil for interfaces and reference types (slice, pointer, map, channel, function). The zero value of an aggregate type like an array or a struct has the zero value of all of its elements or fields.
2. A short variable declaration acts like an assignment only to variables that were already declared in the same lexical block.
3. The expression `new(T)` creates an unnamed variable of type `T`, initializes it to the zero value of `T`, and returns its address, which is a value of type `*T`.
4. The lifetime of a package-level variable is the entire execution of the program. By contrast, local variables have dynamic lifetimes: a new instance is created each time the declaration statement is executed, and the variable lives on until it becomes unreachable.
5. The variable becomes unreachable if there is no path from any package-level variable or local variable of each currently active function to the varialbe in question, following pointers and other kinds of references.

## 2.4 Assignments
1. In tupple assignment, all of the right-hand side expressions are evaluated before any of the variables are updated.

      ```
         // swap
         x, y = y, x
         // GCD
         func gcd(x, y int) int {
            for y != 0 {
               x, y = y, x%y
            }
            return x
         }
         // Fibonacci
         func fib(n int) int {
            x, y := 0, 1
            for i := 0; i < n; i++ {
               x, y = y, x + y
            }
            return x
         }
      ```
2. There are three operators that sometimes return multipel results. We can assign unwarted values to the blank identifier.

      ```
         _, ok = m[key] // map lookup
         _, ok = x.(T)  // type assertion
         _, ok = <-ch   // channel receive
      ```
3. 
