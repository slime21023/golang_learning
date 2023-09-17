# Advanced Fuctions

In Go, functions are **first-class** values. This means that you can do with functions the same things you can do with all other values.
- assign functions to variables, pass them as arguments to other functions or even return functions from other functions.

```golang
func add(x, y int) int {
    return x + y
}

func mul(x, y int) int {
    return x * y
}

// Accept a function as a parameter
func aggregate(a, b, c int, arithmetic func(int, int) int) int {
    return arithmetic(arithmetic(a, b), c)
} 

func main() {
    fmt.Println(aggregate(2, 3, 4, add))
    fmt.Println(aggregate(2, 3, 4, mul))
}
```

```golang
func getPlusNum(num int) func(int) int {
    return func(x int) {
        return x + num
    }
}

plusOne := getPlusNum(1)
```

### `defer`

The `defer` keyword is a fairly unique feature of Go. It allows a function to be executed automatically *just before* its enclosing function returns.

Deferred functions are typically used to close database connections, file handlers, etc.

```golang
func CopyFile(dstName, srcName string) (written int64, err error) {
    // Open the source file
    src, err := os.Open(srcName)
    if err != nil {
        return
    }

    // Close the source file when the CopyFile function returns
    defer src.Close()

    // Create the destination file
    dst, err := os.Create(dstName)
    if err != nil {
        return
    }

    // Close the destination file when CopyFile function returns
    defer dst.Close()

    return io.Copy(dst, src)
}
```

### Closures

A closure is a function that references variables from outside its own function body. The function may access and *assign* to the referenced variables.

```golang
func concatter() func(string) string {
    doc := ""
    return func(word string) string {
        doc += word + " "
        return doc
    }
}

func main() {
    onePlus := concatter()
    onePlus("One")
    onePlus("plus")
    fmt.Println(onePlus("two")) 
}
```