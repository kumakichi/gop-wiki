## qrun

```bash
Usage: qrun [-asm -quiet -debug -prof] <gopSrcDir|gopSrcFile>
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
qrun <gopSrcDir|gopSrcFile>        # gop run <gopSrcDir | gopSrcFile>
qrun -asm <gopSrcDir|gopSrcFile>   # generates `asm` code of Go+ bytecode backend
qrun -quiet <gopSrcDir|gopSrcFile> # don't generate any compiling stage log
qrun -debug <gopSrcDir|gopSrcFile> # print debug information
qrun -prof <gopSrcDir|gopSrcFile>  # do profile and generate profile report
```

## qgo

```bash
Usage: qgo [-test] <gopSrcDir>
  -test
    	test Go+ package
```

Here are some examples:

```bash
qgo <gopSrcDir> # gop go <gopSrcDir>
qgo -test <gopSrcDir>
```

Note:

* `qgo -test <gopSrcDir>` converts Go+ packages into Go packages, and for every package, it call `go run <gopPkgDir>/gop_autogen.go` and `qrun -quiet <gopPkgDir>` to compare their outputs. If their outputs aren't equal, the test case fails.