# Slices

Arrays are fixed in size. Once you make an array like `[10]int` you can't add an 11th element.
- A slice is a dynamically-sized, flexible view of the elements of an array.

```golang
primes := [6]int{2, 3, 5, 7, 11, 13}
mySlice := primes[1:4]
```

Slice syntax:
```golang
arrayName[lowIndex: highIndex]
arrayName[lowIndex:]
arrayName[:highIndex]
arrayName[:]
```

### `make`
Slices can be created with the built-in `make` function; this is how you create dynamically-sized arrays.

```golang
a := make([]int, 5)  // len(a)=5

b := make([]int, 0, 5) // len(b)=0, cap(b)=5

b = b[:cap(b)] // len(b)=5, cap(b)=5
b = b[1:]      // len(b)=4, cap(b)=4
```

### Variadic

A variadic function receives the variadic arguments as a slice.

```golang
func sum(nums ...int) int {
    num := 0

    // nums is just a slice
    for i := 0; i < len(nums); i++ {
        num = nums[i] + num
    }
    return num
}

func main() {
    total := sum(1, 2, 3)
    fmt.Println(total)
}
```

### `range`

Go provides syntatic sugar to iterate easily over elements of a slice:
```golang
for INDEX, ELEMENT := range SLICE {

}
```
example:
```golang
fruits := []string{"apple", "banana", "grape"}
for i, fruit := range fruits {
    fmt.Println(i, fruit)
}
```

