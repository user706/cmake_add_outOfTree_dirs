cmake_minimum_required(VERSION 3.10)

project(example)

option(BUILD_SHARED_LIBS "build shared (dll) libs" OFF)
if (BUILD_SHARED_LIBS)
  set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
else()
  set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS OFF)
endif()

set(CMAKE_CXX_STANDARD    14 CACHE STRING "c++ standard")
set(CMAKE_CXX_EXTENSIONS OFF CACHE BOOL   "c++ extensions")

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

add_subdirectory(../../common/utils    # code which is NOT in a subdirectory, but "out-of-tree"
                 utils_binary_dir      # build dir
                )


add_executable(go main.cpp)
target_link_libraries(go sum)
