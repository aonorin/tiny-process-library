cmake_minimum_required(VERSION 2.8)

project(tiny-process-library)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall")

set(source_files examples.cpp process.cc)

#If compiled using MSYS2, use sh to run commands
if(MSYS)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -DMSYS_PROCESS_USE_SH")
  list(APPEND source_files process_win.cc)
else()
  list(APPEND source_files process_unix.cc)
endif()

add_executable(examples ${source_files})