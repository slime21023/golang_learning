# Pointers

A pointer is a variable that stores the *memory address* of another variable.

The `*` syntax defines a pointer:

```golang
var p *int
```

The `&` operator generates a pointer to its operand. Get the address of a variable.
```golang
myString := "hello"
var myString = &myString
```

### Why are pointers useful?

Pointers allow us to manipulate data in memory directly, without making copies or duplicating data.

### Access the value by address

The `*` dereferences a pointer to gain access to the value
```golang
fmt.Println(*myStringPtr) // read myString through the pointer
*myStringPtr = "world"    // set myString through the pointer
```

Unlike C, Go has no **pointer arithmetic**.

### Pointer Receiver

A receiver type on a method can be a pointer.

```golang
type car struct {
    color string
}

func (c *car) setColor(color string) {
    c.color = color
}

func main() {
    c := car{
        color: "white"
    }
    c.setColor("blue")
    fmt.Println(c.color)
}
```