# Program Structure

## Names
1. Go programmers use "camel case" when forming names by combining words
2. The letters of acronyms and initialisms like ASCII and HTML are always rendered in the same case. e.g. escapeHTML, not escapeHtml

## Declarations
1. If an entity is declared within a function, it is local to that function. 
2. If declared outside of a function, however, it is visible in all files of the package to which it belongs. 
3. If the name begins with an upper-case letter, it is exported, which means that it is visible and accessible outside of its own package and may be referred to by other parts of the program.

## Variables
1. `var name type = expression`: 
    * if the type is ommited, it is determined by the initializer expression.
    * if the expression is omitted, the initial value is the zero value for the type, which is 0 for numbers, false for booleans, "" for strings, and nil for interfaces and reference types (slice, pointer, map, channel, function). The zero value of an aggregate type like an array or a struct has the zero value of all of its elements or fields.
2. 
