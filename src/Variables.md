# Variables

### Golang Variables Type
- `bool`
- `string`
- `int int8 int16 int32 int64`
- `uint uint8 uint16 uint32 uint64`
- `byte` : for uint8
- `rune` : for int32, to represents a Unicode code point
- `float32 float64`
- `complex64 complex128`

```Golang
package main

import "fmt"

func main() {
    // initialize variables
    var num int
    var flo float64
    var isTrue bool
    var name string

    fmt.Printf(
        "%v %f %v %q\n",
        num, flo, isTrue, name
    )
}
```

### Variable Declaration

```Golang
var empty string // same as `empty := ""`
num := 10 // inferred to be an integer
temperature := 0.0 // inferred to be a floating
var isFunny = true // inferred to be a boolean
```

### Casting
```Golang
temperatureInt := 88
temperatureFloat := float64(temperatureInt)
```

### Const
- **Constants** must be known at compile time.
- **Constants** can be computed so long as the computation can happen at compile time.

```Golang
const num = 15
const numPlusOne = num +1
```