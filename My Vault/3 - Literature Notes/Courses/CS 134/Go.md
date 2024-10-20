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
declaring arguments
```
x int, y int
x, y int
ptr *int
arr [3]int
```
## arithmetic
```
func add(x, y int) int {  // short for (x int, y int)
	z := x+y
	return z
}

func main() {
	fmt.Println(add(42, 13))
	
	x, y := 3, 4
	var f = math.Sqrt(float64(x*x + y*y))  //sqrt requires float input
	var z uint = uint(f)  // var zuint = f  returns error, MANUAL convert
	fmt.Println(x, y, z) //3,4,5
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
## naked return (shorthand)
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
var c, python, java bool  //all bools, default = false

func main() {
	var i int  //int default = 0
	fmt.Println(i, c, python, java) 
}

```
initialized: 
```
var i, j int = 1, 2  

func main() {
	var c, python, java = true, false, "no!"  //type optional w/ init
	fmt.Println(i, j, c, python, java)
}
```
quick initializing shorthand
```
var i, j int = 1, 2  // := not usable outside functions

func main() {
	k := 3
	c, python, java := true, false, "no!"
	fmt.Println(i, j, k, c, python, java)
}
```
## Types
example of () blocks for import and var
```
package main

import (
	"fmt"
	"math/cmplx"
)

var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
	s string
)

func main() {
	fmt.Printf("Type: %T Value: %v\n", ToBe, ToBe)
	fmt.Printf("Type: %T Value: %v\n", MaxInt, MaxInt)
	fmt.Printf("Type: %T Value: %v\n", z, z)
	fmt.Printf("Type: %T Value: %q\n", s, s)
}
_____________________________________________________________________
output:
Type: bool 			Value: false
Type: uint64 		Value: 18446744073709551615
Type: complex128 	Value: (2+3i)
Type: string 		Value: ""
```
all types in Go:
```
bool //default=false

string //default=""

int  int8  int16  int32  int64  //int = 64 bit on 64-bit system
uint uint8 uint16 uint32 uint64 uintptr 

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

## Type conversion
```
func main() {
	i := 42
	f := float64(i)
	u := uint(f)
	fmt.Println(x, y, z)
}
```
## Type inference
