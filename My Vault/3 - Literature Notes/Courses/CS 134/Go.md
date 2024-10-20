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
## add ints
```
func add(x, y int) int {  // short for (x int, y int)
	z := x+y
	return z
}

func main() {
	fmt.Println(add(42, 13))
}
```
## swap str
```
func swap(x, y string) (string, string) { # returns two str
	return y, x
}

func main() {
	a, b := swap("hello", "world")
	fmt.Println(a, b)
}
```
# naked return (shorthand)
```
func split(sum int) (x, y int) {
	x = sum * 4 / 9  // not := because already declared above as ret
	y = sum - x
	return  //returns x and y
}

func main() {
	fmt.Println(split(17))
}

```
# Variables
```
var x int
x int, y int
x, y int
ptr *int
arr [3]int
```