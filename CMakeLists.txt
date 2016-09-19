cmake_minimum_required(VERSION 3.4.3)
project(LLVM_C_Factorial)

# e:\prg\thirdparties\llvm\llvm-3.9-install\vs2015_64\Debug
find_package(LLVM REQUIRED CONFIG)

message(STATUS "Found LLVM ${LLVM_PACKAGE_VERSION}")
message(STATUS "Using LLVMConfig.cmake in: ${LLVM_DIR}")

# Set your project compile flags.
# E.g. if using the C++ header files
# you will need to enable C++11 support
# for your compiler.

include_directories(${LLVM_INCLUDE_DIRS})
add_definitions(${LLVM_DEFINITIONS})

set(LLVM_LINK_COMPONENTS
  Analysis
  BitReader
  Core
  ExecutionEngine
  InstCombine
  Interpreter
  MC
  MCDisassembler
  MCJIT
  Object
  OrcJIT
  RuntimeDyld
  ScalarOpts
  Support
  Target
  TransformUtils
  native 
  nativecodegen
)

# Find the libraries that correspond to the LLVM components
# that we wish to use
llvm_map_components_to_libnames(llvm_libs support core irreader ${LLVM_LINK_COMPONENTS})

# Now build our tools
add_executable(factorial main.c)

# Link against LLVM libraries
target_link_libraries(factorial  ${llvm_libs})
