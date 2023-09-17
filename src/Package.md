# Package
A package is a container that contains various functions to perform specific tasks.

While working on big projects, we have to deal with a large amount of code, and writing everything together in the same file will make our code look messy. 

### Package Naming

A Go package has both a name and a path. The package name is specified in the package statement of its source files; client code uses it as the prefix for the package’s exported names.

Client code uses the package path when importing the package.

```golang
import (
    "context"                // package context
    "fmt"                    // package fmt
    "golang.org/x/time/rate" // package rate
    "os/exec"                // package exec
)
```

### One Package / Directory

A directory of Go code have **at most** one package.
- All `.go` files in a single directory must all belong to the same package.

### Modules

Go programs are organized into *packages*. A Package is a directory of Go code that's all compiled together. Functions, types, variables, and constants defined in one source file are visible to **all other source files within the same package(directory)**.

A *repository* contains one or more *modules*. A module is a collection of Go packages that are released together.

### Go Repository

A Go repository typically contains only one module, located at the root of the repository.

A file named `go.mod` at the root of a project declares the module.
It contains:
- The module path
- The version of the Go language that the project requires
- Optionally any external package dependencies you project has

### Create a module
```bash
mkdir hellogo
cd hellogo
```

Inside the directory declare the module's name:
```bash
go mod init {REMOTE}/{USERNAME}/hellogo
```

Where `{REMOTE}` is your preferred remote source provider (i.e. `github.com`) and `{USERNAME}` is your Git username. If you don't use a remote provider yet, just use `example.com/username/hellogo`
