### Variable & operator

```go
x := 123.1 - 3i
y, z := 1, 123
s := "Hello"

println(s + " complex")
println(x - 1, y * z)

a, b := 2, 3
a++
b--
println(a, b)
```

### Condition

```go
x := 0
if t := false; t {
    x = 3
} else {
    x = 5
}

x = 0
switch s := "Hello"; s {
default:
    x = 7
case "world", "hi":
    x = 5
case "xsw":
    x = 3
}

v := "Hello"
switch {
case v == "xsw":
    x = 3
case v == "Hello", v == "world":
    x = 5
default:
    x = 7
}
```

### For loop

```go
fns := make([]func() int, 3)
sum := 0
for _, x := range [1, 3, 5, 7, 11, 13, 17] {
    if x > 3 {
        sum += x
    }
}
println("sum(5,7,11,13,17):", sum)

sum = 0
for i, x := range [3, 15, 777] {
    v := x
    fns[i] = func() int {
        return v
    }
}
println("values:", fns[0](), fns[1](), fns[2]())

sum = 0
arr := [1, 3, 5, 7, 11, 13, 17]
i := 10
for i = 0; i < len(arr); i++ {
    if arr[i] > 3 {
        sum += arr[i]
    }
}
println("sum(5,7,11,13,17):", sum)

sum = 0
x := 0
for _, x = range [1, 3, 5, 7, 11, 13, 17] {
	if x > 3 {
		sum += x
	}
}
println("x:", x, x == 17)
println("sum(5,7,11,13,17):", sum)
```

### Flow control

* fallthrough

TODO:

* break
* continue
* goto


### Import go package

```go
import (
    "fmt"
    "strings"
)

x := strings.NewReplacer("?", "!").Replace("hello, world???")
fmt.Println("x:", x)
```

### Func & closure

```go
import (
    "fmt"
    "strings"
)

func foo(x string) string {
    return strings.NewReplacer("?", "!").Replace(x)
}

func printf(format string, args ...interface{}) (n int, err error) {
    n, err = fmt.Printf(format, args...)
    return
}

func bar(f func(string, ...interface{}) (int, error)) {
    f("Hello, %v!\n", "qlang")
}

x := "qlang"
fooVar := func(prompt string) (n int, err error) {
    n, err = fmt.Println(prompt + x)
    return
}

printfVar := func(format string, args ...interface{}) (n int, err error) {
    n, err = fmt.Printf(format, args...)
    return
}

barVar := func(f func(string, ...interface{}) (int, error)) {
    f("Hello, %v!\n", "qlang")
}

bar(printf)
barVar(printfVar)
```

### String, map, array & slice

```go
x := []float64{1, 3.4, 5}
y := map[string]float64{"Hello": 1, "xsw": 3.4}

a := [...]float64{1, 3.4, 5}
b := [...]float64{1, 3: 3.4, 5}
c := []float64{2: 1.2, 3, 6: 4.5}

x[1], y["xsw"] = 1.7, 2.8
println(`x[1]:`, x[1], `y["xsw"]:`, y["xsw"])

title := "Hello,world!" + "2020-05-27"
println(title[:len(title)-len("2006-01-02")], len(a), a[1:])
```

### Builtin & typecast

```go
a := make([]int, uint64(2))
a = append(a, 1, 2, 3)
println(a, "len:", len(a), "cap:", cap(a))

b := make([]int, 0, uint16(4))
c := [1, 2, 3]
b = append(b, c...)
println(b, "len:", len(b), "cap:", cap(b))
```
