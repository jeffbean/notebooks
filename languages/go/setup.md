# setup the env
download https://storage.googleapis.com/golang/go1.4.2.linux-amd64.tar.gz

untar into the /usr/local dir
`tar -C $HOME/.local/ -xzf go1.4.2.linux-amd64.tar.gz`

Setup ENV vars in `~/.zshrc` or whatever your shell uses.
```bash
export GOROOT=$HOME/.local/go
PATH=$PATH:$GOROOT/bin
export GOPATH=$HOME/go
```
Check that Go is installed correctly by building a simple program, as follows.

Create a file named hello.go and put the following program in it:
```go
package main

import "fmt"

func main() {
    fmt.Printf("hello, world\n")
}
```

Then run it with the go tool:

```
$ go run hello.go
hello, world
```

If you see the "hello, world" message then your Go installation is working.
