We reinvent error handling specification in Go+. We call them `ErrWrap expression`:

```go
expr!
expr?
expr?:defval
```

All `ErrWrap expression` supposes that `expr` (in most case, it is a function call) has multiple values (val1, val2, ..., valN), and valN can be assigned to an error variable.

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

* errors.NewFrame is defined in "github.com/qiniu/x/errors". It will be automatically imported as necessary.
