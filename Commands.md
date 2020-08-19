## gop

```bash
gop run         # Run a Go+ program
gop repl        # Run Go+ in REPL/Console mode
gop go [-test]  # Convert Go+ packages into Go packages. If -test specified, it tests related packages.
gop fmt         # Format Go+ packages
gop export      # Export Go packages for Go+ programs
```

#### gop run (ie. qrun)

Run &lt;gopSrcDir|gopSrcFile&gt; as a Go+ script.

```bash
Usage: gop run [-asm -quiet -debug -prof] <gopSrcDir|gopSrcFile>
  -asm
    	generates `asm` code of Go+ bytecode backend
  -debug
    	print debug information
  -prof
    	do profile and generate profile report
  -quiet
    	don't generate any compiling stage log
```

Here are some examples:

```bash
gop run <gopSrcDir|gopSrcFile>        # gop run <gopSrcDir | gopSrcFile>
gop run -asm <gopSrcDir|gopSrcFile>   # generates `asm` code of Go+ bytecode backend
gop run -quiet <gopSrcDir|gopSrcFile> # don't generate any compiling stage log
gop run -debug <gopSrcDir|gopSrcFile> # print debug information
gop run -prof <gopSrcDir|gopSrcFile>  # do profile and generate profile report
```

#### gop repl (ie. igop)

Run Go+ in REPL/Console mode.

```bash
Usage: gop repl
```

#### gop fmt (ie. qfmt)

Format Go+ packages.

```bash
Usage: gop fmt [-w] [path ...]
  -w	write result to (source) file instead of stdout
```


#### gop export (ie. qexp)

Generate a Go+ package that wraps a Go package automatically.

```bash
Usage: gop export [-outdir <outRootDir>] <goPkgPath>
  -outdir string
    	optional set export lib path, default is $GoPlusRoot/lib path.
```

#### gop go (ie. qgo)

Convert all Go+ packages under &lt;gopSrcDir&gt; into Go packages, recursively.

```bash
Usage: gop go [-test] <gopSrcDir>
  -test
    	test Go+ package
```

Here are some examples:

```bash
gop go <gopSrcDir> # gop go <gopSrcDir>
gop go -test <gopSrcDir>
```

Note:

* `gop go -test <gopSrcDir>` converts Go+ packages into Go packages, and for every package, it call `go run <gopPkgDir>/gop_autogen.go` and `gop run -quiet <gopPkgDir>` to compare their outputs. If their outputs aren't equal, the test case fails.
