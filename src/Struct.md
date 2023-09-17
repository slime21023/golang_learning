# Structs
Group different types of variables together

```golang
type Car struct {
    Make string
    Model string
    Height int
    Width int
}
```

### Nested Struct
```golang
type Car sturct {
    Make string
    Model string
    Height int
    Width int
    FrontWheel Wheel
    BackWheel Wheel
} 

type Wheel struct {
    Radius int
    Material string
}
```

The fields of a struct can be accessed using the `.` operator.
```golang
myCar := car{}
myCar.FrontWheel.Radius = 5
```

### Embedded Struct

```golang
type Address struct {
    City  string
    State string
}
  
type Person struct {
    Name    string
    Address //embedded struct
}

func main() {
    p := Person{
        Name: "John Doe",
        Address: Address{
            City:  "New York",
            State: "NY",
        },
    }
  
    fmt.Println("Name:", p.Name)
    // embedded fields promoted to the top-level
    fmt.Println("City:", p.City)
    fmt.Println("State:", p.State)
}
```

### Struct Method
```golang
type rect struct {
    width int
    height int
}

// area has a receiver of (r rect)
func (r rect) area() int {
    return r.width * r.height
}

r := rect{
    width: 5,
    height: 10,
}

fmt.Println(r.area())
```