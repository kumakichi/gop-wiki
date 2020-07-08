There are two ways to import a Go package in Go+ programs.

The first way is importing it directly, as a Go+ package (But this way is not implemented currently). The reason it works is because a Go package is also a legal Go+ package. It is very easy, but has some limits. It doesn't work if the Go package to be imported uses `cgo`.

The second way is static link it into the `gop` command (In alpha stage, we use the `qgo`, `qrun` commands).

```bash
cd $GoPlusRoot
qexp <goPkgPathToBeImported>
cd lib/default.go
vim lib/default.go
# add <goPkgPathToBeImported> and save
go install -v ./...
```

Now, you can import it in a Go+ program:

```go
import "<goPkgPathToBeImported>"

...
```
