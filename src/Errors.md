# Errors

Go programs express errors with `error` values.
An **Error** is any type that implements the built-in **error interface**:

```golang
type error interface {
    Error() string
}
```

A function that can return an `error` should handle errors by testing whether the error is `nil`.

```golang
i, err := strconv.Atoi("42b")
if err != nil {
    fmt.Println("couldn't convert:", err)
    return
}
```

### Custom Error
Build the custom types that implement the `error` interface.

```golang
type userError struct {
    name string
}

func (e userError) Error() string {
    return fmt.Sprintf("%v has a problem", e.name)
}
```

It can then be used as an error:

```golang
func sendSMS(msg, userName string) error {
    if !canSendToUser(userName) {
        return userError{name: userName}
    }
}
```

### The Error Package
`errors.New()` function:
```golang
var err error = errors.New("something went wrong")
```