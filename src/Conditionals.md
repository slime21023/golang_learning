# Conditionals

### `if, else if, else`
```golang
if height > 6 {
    fmt.Println("You are super tall!")
} else if height > 4 {
    fmt.Println("You are tall enough!")
} else {
    fmt.Println("You are not tall enough!")
}
```

### `switch`
```golang
switch n {
case 1:
    fmt.Println("red")
case 2:
    fmt.Println("blue")
case 3:
    fmt.Println("green")
default:
    fmt.Println("black")
}
```

### `if ; CONDITIONAL {}`
```golang
if length := getLength(email); length < 1 {
    fmt.Println("Email is invalid")
}
```
