# Channels & Concurrency

### What is Concurrency?

**Concurrency** is the ability to **perform multiple tasks** at the same time.
Typically, our code is executed one line at a time, one after the other; This is called *sequential execution* or *synchronous execution*.

### How does concurrency work in Go?

Go was designed to be concurrent, which is a trait *fairly* unique to Go. It excels at performing many tasks simultaneously safely using a simple syntax.

Concurrency is as simple as using the `go` keyword when calling a function:

```golang
go doSomething()
```

### Channels

Channels are a typed, thread-safe queue. Channels allow different goroutines to communicate with each other.

#### Create a channel
Like maps and slices, channels must be created *before* use. They also use the same `make` keyword:

```golang
ch := make(chan int)
```

#### Send data to a channel

```golang
ch <- 10
```

The `<-` operator is called the *channel operator*. Data flows in the direction of the arrow. This operation will *block* until another goroutine is ready to receive the value.

#### Receive data from a channel

```golang
v := <- ch
```

- This reads and removes a value from the channel and saves it into the variable `v`.
- This operator will *block* until there is a value in the channel to be read.

#### Blocking and deadlocks

A `deadlock` is when a group of goroutines are all blocking so none of them can continue. This is a common bug that you need to watch out for in concurrent programming.


### Buffered Channels

Channels can *optionally* be buffered.

#### Creating a channel with a buffer

You can provide a buffer length as the second argument to `make()` to create a buffered channel:

```golang
ch := make(chan int, 100)
```

Sending on a buffered channel only blocks when the buffer is full.
Receiving blocks only when the buffers is empty.

#### Closing Channels in Go

Channels can be explicitly closed by a sender.

```golang
ch := make(chan int)

// do something with the channel

close(ch)
```

#### Checking if a channel is closed

Similar to the `ok` value when accessing data in a `map`, receivers can check the `ok` value when receiving from a channel to test if a channel was closed.

```golang
v, ok := <- ch
```

ok is `false` if the channel is empty and closed.

### Don't send on a closed channel

Sending on a closed channel will cause a panic. A panic on the main goroutine will cause that goroutine to crash.

- Closing isn't necessary.
- There is nothing wrong with leaving channels open, they will still be garbage collected if they are unused.

### Read-only channels

A channel can be marked as read-only by casting it from a `chan` to a `<-chan` type.

```golang
func readCh(ch <-chan int) {
    // ch can only be read in this function
}

func main() {
    ch := make(chan int)
    readCh(ch)
}
```

### Write-only channels

The same goes for write-only channels, but the arrow's position moves.

```golang
func writeCh(ch chan<- int) {
    // ch can only be written in this function.
}
```