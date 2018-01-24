# Composite Types
1. Arrays and structs are aggregate types; their values are concatenations of other values in memory. Arrays are homogeneous and structs are heterogeneous.
2. Both arrays and structs are fixed size. In contrast, slices and maps are dynamic data structures that grow as values are added.

## Arrays
1. We can use an array literal to initialize an array with a list of values. if an ellipsis `...` appears in place of the length, the array length is deter- mined by the number of initializers.

    ```
    var q [3]int = [3]int{1, 2, 3}
    q := [...]int{1, 2, 3}  // same as above
    q := []int{1, 2, 3} // q is a slice in this case!
    ```
  
2. It is possible to specify a list of index and value pairs in array literal. In this form, indices can appear in any order and some may be omitted; as before, unspecified values take on the zero value for the element type. 

    ```
    type Currency int
    const (
      USD Currency = iota
      EUR
      GBP
      RMB
    )
    symbol := [...]string{USD: "$", EUR: "9", GBP: "!", RMB: """}
    
     r := [...]int{99: -1}      // this defines an array of 100 int
    ```
    
3. If an array’s element type is comparable then the array type is comparable too, so we may directly compare two arrays of that type using the `==` operator, which reports whether all corresponding elements are equal. 

4. When a function is called, a copy of each argument value is assigned to the corresponding parameter variable, so the function receives a copy, not the original. Passing large arrays in this way can be inefficient, and any changes that the function makes to array elements affect only the copy, not the original. This behavior is different from languages that implicitly pass arrays by reference. So use slices for function paramerters.
