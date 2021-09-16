# Basics

Hello World

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, World")
}
```

## Channels

Channels are a tool to create communication between gobroutines.

```go
msgChan := make(chan string)

// send
msgChan<- "hello"

// receive
msg := <-msgChan
```

### Select/Case

```go
select {
case msg := <-msgChan:
	fmt.Println(msg)
default:
	fmt.Println("nothing")
}
```

## Multithreading

- You can spawn as many Go routines as you want.
- Runing Go program creates as many system threads as logical processors.

## 