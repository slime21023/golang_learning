# Formatting

### fmt
- `fmt.Printf()` : Prints a formatted string to **standard out**
- `fmt.Sprintf()`: Returns the formatted string

### `%v` - Interpolate the default representation
```golang
fmt.Printf("I am %v years old", 10)
fmt.Printf("I am %v years old", "ten")
```

### `%s` - Interpolate a string
```golang
fmt.Printf("I am %s years old", "ten")
```

### `%d` - Interpolate an integer in decimal form
```golang
fmt.Printf("I am %d years old", 10)
```

### `%f` - Interpolate a decimal
```golang
fmt.Printf("I am %f years old", 10.523)

// The ".2" rounds the number to 2 decimal places
fmt.Printf("I am %.2f years old", 10.523)
```