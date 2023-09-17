# Generics

### Type Parameters

Generics allow us to use variables to refer to specific types. It allows us to write abstract functions that drastically reduce code duplication.

```golang
func splitAnySlice[T any] (s []T) ([]T, []T) {
    mid := len(s)/2
    return s[:mid], s[mid:]
}
```

```golang
firstInts, secondInts := splitAnySlice([]int{0, 1, 2, 3})
fmt.Println(firstInts, secondInts)
```

### Constraints

Sometimes you need the logic in your generic function to know *something* about the types it operates on. 
- The constraints are just interfaces that allow us to write generics that only operate within the constraints of a given interface type.
- The `any` constraints is the same as the empty interface because it means the type in question can be *anything*.

### Create a custom constraint
```golang
type stringer interface {
    String() string
}

func concat[T stringer](vals []T) string {
    result := ""
    for _, val := range vals{
        result += val.String()
    }
    return result
}
```

### Interface type lists
```golang
// Ordered is a type constraint that matches any ordered type.
// An ordered type is one that supports the <, <=, >, >= operators.
type Ordered interface {
    ~int | ~int8 | ~int16 | ~int32 | ~int64 |
    ~uint | ~uint8 | ~uint16 | ~uint32 | ~uint64 | ~uintptr |
    ~float32 | ~float64 | ~string 
}
```
