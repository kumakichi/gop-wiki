How do we convert ErrWrap expression?

## Case1: foo()!

```go
var1, var2, ..., varN := foo()!
```

Will be converted into the following code:

```go
_gop_1, _gop_2, ..., _gop_N, _gop_Np1 := foo()
if _gop_Np1 != nil {
   panic(errors.NewFrame(_gop_Np1, ...))
}
var1, var2, ..., varN := _gop_1, _gop_2, ..., _gop_N
```

## Case2: foo()?

```go
var1, var2, ..., varN := foo()?
```

Will be converted into the following code:

```go
_gop_1, _gop_2, ..., _gop_N, _gop_Np1 := foo()
if _gop_Np1 != nil {
   _ret_err = errors.NewFrame(_gop_Np1, ...)
   return
}
var1, var2, ..., varN := _gop_1, _gop_2, ..., _gop_N
```

## Case3: foo()?:defaultValue

```go
val := foo()?:defaultValue
```

Will be converted into the following code:

```go
_gop_1, _gop_2 := foo()
if _gop_2 != nil {
   _gop_1 = defaultValue
}
val := _gop_1
```
