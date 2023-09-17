# Maps

Maps are similar to javascript objects, python dictionaries, and ruby hashes. Maps are a data structure that provides key value mapping.
- The zero value of a map is `nil`.

```golang
ages := make(map[string]int)
ages["John"] = 37
ages["Mary"] = 24
```
```golang
ages = map[string]int {
    "John": 37,
    "Mary": 24,
}
```

### Mutations

- Insert an element
    ```golang
    m[key] = elem
    ```

- Get an element
    ```golang
    elem = m[key]
    ```

- Delete an element
    ```golang
    delete(m, key)
    ```

- Check if a key exists
    ```golang
    elem, ok := m[key]
    ```