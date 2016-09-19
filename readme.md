Factorial example with LLVM MCJIT using llvm-c library ported to LLVM 3.9.

Tested on Windows with Visual Studio 2015 64 bits.

# Building

First you need to build LLVM. See the official documentation:
http://llvm.org/releases/3.9.0/docs/CMake.html


Then in CMake, you need to set LLVM_DIR to lib/cmake/llvm directory of the install you made after compiling LLVM (either by setting it in cmake-gui or by passing it via -D to cmake on the command-line).

For example:

```
e:/prg/thirdparties/llvm/llvm-3.9-install/vs2015_64/Debug/lib/cmake/llvm
or
e:/prg/thirdparties/llvm/llvm-3.9-install/vs2015_64/Release/lib/cmake/llvm
```

See http://llvm.org/docs/CMake.html#embedding-llvm-in-your-project for more details.

# Windows specific

I haven't figured out yet how to generate a project that allow switching between Release & Debug build of LLVM depending on the configuration...

Work-around:
- generate a project that depends on LLVM debug install
- generate another project that depends on LLVM release install


Baptiste Lepilleur.
