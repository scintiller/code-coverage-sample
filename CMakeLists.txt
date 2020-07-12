# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (foo)

# set compiler option
SET (CMAKE_CXX_COMPILER             "/usr/local/opt/llvm/bin/clang++")

if("${CMAKE_C_COMPILER_ID}" MATCHES "(Apple)?[Cc]lang" OR "${CMAKE_CXX_COMPILER_ID}" MATCHES "(Apple)?[Cc]lang")
  message("Building with llvm Code Coverage Tools")
#  if(NOT LLVM_COV_PATH)
#    message(FATAL_ERROR "llvm-cov not found! Aborting.")
#  endif()
endif()
add_executable(foo foo.cpp)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fprofile-instr-generate -fcoverage-mapping")

# add compile option
#add_compile_options(-DLLVM_BUILD_INSTRUMENTED_COVERAGE=On)
#set(-DLLVM_BUILD_INSTRUMENTED_COVERAGE=On)
# add link options
# add_link_options(-fprofile-instr-generate -fcoverage-mapping)


# 指定生成目标
