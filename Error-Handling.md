We reinvent error handling specification in Go+. We call them `ErrWrap expressions`:

```go
expr! // panic if err
expr? // return if err
expr?:defval // use defval if err
```

How to use them? Here is an example:

```go
import (
	"strconv"
)

func add(x, y string) (int, error) {
	return strconv.Atoi(x)? + strconv.Atoi(y)?, nil
}

func addSafe(x, y string) int {
	return strconv.Atoi(x)?:0 + strconv.Atoi(y)?:0
}

println(`add("100", "23"):`, add("100", "23")!)

sum, err := add("10", "abc")
println(`add("10", "efg"):`, sum, err)

println(`addSafe("10", "efg"):`, addSafe("10", "abc"))
```

The output of this example is:

```
add("100", "23"): 123
add("10", "efg"): 0 strconv.Atoi: parsing "abc": invalid syntax

===> errors stack:
main.add("10", "abc")
	/Users/xsw/goplus/tutorial/15-ErrWrap/err_wrap.gop:6 strconv.Atoi(y)?

addSafe("10", "efg"): 10
```

Compared to corresponding Go code, It is clear and more readable.

And the most interesting thing is, the return error contains the full error stack. When we got an error, it is very easy to position what the root cause is.

How do these `ErrWrap expressions` work?

All `ErrWrap expressions` supposes that `expr` (in most case, it is a function call) has multiple values (val1, val2, ..., valN), and valN can be assigned to an error variable.

The expression `expr!` checks valN is nil or not. if not, it panics. The following is the corresponding Go code:

```go
val1, val2, ..., valN1, valN := expr
if valN != nil {
    panic(errors.NewFrame(valN, ...))
}
val1, val2, ..., valN1 // value of `expr!`
```

The expression `expr?` checks valN is nil or not. if not, it return the error. So it supposes the last output parameter of the function who uses `expr?` has an `error` type. The following is the corresponding Go code:

```go
val1, val2, ..., valN1, valN := expr
if valN != nil {
    _ret_err = errors.NewFrame(valN, ...)
    return
}
val1, val2, ..., valN1 // value of `expr?`
```

The expression `expr?:defval` checks valN is nil or not. if not, it uses `defval` as the value of `expr`. So it supposes `expr` has two values (val1, val2). The following is the corresponding Go code:

```go
val1, val2 := expr
if val2 != nil {
    val1 = defval
}
val1 // value of `expr?:defval`
```

Note:

* errors.NewFrame is defined in `"github.com/qiniu/x/errors"`. It will be automatically imported as necessary.
