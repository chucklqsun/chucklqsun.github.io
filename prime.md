Algorithm:

1. Start with 2
2. all value %2!=0 are passed to3
3. get %2!=0, %3!=0 as prime, 5
4. get %2!=0, %3!=0, %5!=0 as prime, 7
5. ....
6. recursive to get next prime number
``` 
package main

import (
    "fmt"
    "os"
)

func task(c chan int, nest int) {
    p := <-c
    if p > 100000000 {
        os.Exit(0)
    }
    fmt.Println(nest, "outers", p)
    cn := make(chan int)
    go task(cn, p)
    for {
        i := <-c
        if i%p != 0 {
            cn <- i
        } else {

        }

    }
}

func main() {
    c := make(chan int)
    go task(c, 2)
    for i := 2; ; i++ {
        c <- i
    }
    fmt.Println("end")
}
```
Note: If you have anything issue or question, please leave me message in this repo
