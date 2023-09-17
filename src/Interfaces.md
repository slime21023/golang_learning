# Interfaces

Interfaces are collections of methods signatures.

A type "implements" an interface
- if it has all of the methods of the given interface defined on it.

```golang
type shape interface {
    area() float64
    perimeter() float64
}

type rect struct {
    width, height float64
}

func (r rect) area() float64 {
    return r.width * r.height
}

func (r rect) perimeter() float64 {
    return 2*r.width + 2*height
}

type circle struct {
    radius float64
}

func (c circle) area() float64 {
    return math.Pi * c.radius * c.radius
}

func (c circle) perimeter() float64 {
    return 2* math.Pi * c.radius
}
```

### Name Interface Arguments
```golang
type Copier interface {
    Copy(source string, destination string) (isCopied int)
}
// origin: 
// type Copier interface { 
//     Copy(string, string) int
// }
```

### Type Assertions
Golang provides a simple way of checking if an interface value is of a specific type. 
- generally used to make sure that an interface value satisfies another interface 
- find the concrete type of the interface.

```golang
func main() {
	var i interface{} = "hello"

	s := i.(string)
	fmt.Println(s)

	s, ok := i.(string)
	fmt.Println(s, ok)

	f, ok := i.(float64)
	fmt.Println(f, ok)

	f = i.(float64) // panic
	fmt.Println(f)
}
```

### Type Switches
A `type switch` makes it easy to do several type assertions in a series.

```golang
func printNumericValue(num interface{}) {
    switch v := num.(type) {
    case int:
        fmt.Printf("%T\n", v)
    case string:
        fmt.Printf("%T\n", v)
    default:
        fmt.Printf("%T\n", v)
    }
}
```

### Clean Interfaces
1. Keep Interface small
```golang
type File interface {
    io.Closer
    io.Reader
    io.Seeker
    Readdir(count int) ([]os.FileInfo, error)
    Stat() (os.FileInfo, error)
}
```

2. Interface should have no knowledge of satisfying types
3. Interface are not classes