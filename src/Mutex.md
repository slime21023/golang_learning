# Mutex

Mutexes allow us to *lack* access to data.
This ensures that we can control which goroutines can access certain data at which time.

Go's standard library provides a build-in implementation of a mutex with the `sync.Mutex` type and its two methods:
- `Lock()`
- `Unlock()`

We can protect a block of code by surrounding it with a call to `Lock` and `Unlock` as shown on the `protected()` method below.

It's good practice to structure the protected code within a function so that `defer` can be used to ensure that we never forget to unlock the mutex.

```golang
func protected() {
    mux.Lock()
    defer mux.Unlock()
}
```

### Maps are not thread-safe

Maps are not safe for concurrent use! If you have multiple goroutines accessing the same map, and at least one of them is writing to the map, you must lock your maps with a mutex.

**Noted: WASM is single-threaded**

### RW Mutex

The standard library also exposes a `sync.RWMutex`.
The `sync.RWMutex` also has these methods:
- `RLock()`
- `RUnlock()`
- `Lock()`
- `Unlock()`

The `sync.RWMutex` can help with performance if we have a read-intensive process. Many goroutines can safely read from the map at the same time (multiple `Rlock()` calls can happen simultaneously). However, only one goroutine can hold a `Lock()` and all `RLock()`'s will also be excluded.

