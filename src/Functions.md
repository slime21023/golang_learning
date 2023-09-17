# Functions

Functions in Go can take zero or more argements.

```golang
func sub(x int, y int) int {
    return x-y
}

func add(x, y int) int {
    return x + y
}

func swap(x, y string) (string, string) {
	return y, x
}
```

### Passing variables by value
```golang
func main(){
    x := 5
    increment(x)

    fmt.Println(x)
    // still prints 5
    // because the function received a copy of x
}

func increment(x int) {
    x++
}
```

### Ignoring return values
```golang
func swap(x, y string) (string, string) {
	return y, x
}

// ignore a value
x, _ := swap("one", "two")
```

### Named return values
```golang
func getCoords() (x, y int) {
    // x and y are initialized with zero values
    return // automatically returns x and y
}
```