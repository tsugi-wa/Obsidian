# Intro
packages - ways to reference files. 
- package main: entry point file
- import math/rand: links "package rand" files 
```
package main

import (
	"fmt"
	"math"
)

func main() {
	fmt.Println("My favorite number is", rand.Intn(10))
}
```
- to export exported vars from packages, MUST be capital
```
fmt.Println(math.Pi)
```


# Functions
```
func add(x int, y int) int {
	return x + y
}

func main() {
	fmt.Println(add(42, 13))
}

```
# Variables
```
x int
x int, y int
x, y int
p *int
a [3]int
```