cmake_minimum_required(VERSION 3.1.0)

project(fmt-test)

add_subdirectory(../.. fmt)

add_executable(library-test "main.cc")
target_link_libraries(library-test fmt::fmt)
target_compile_options(library-test PRIVATE ${PEDANTIC_COMPILE_FLAGS})
target_include_directories(library-test PUBLIC SYSTEM .)

if (TARGET fmt::fmt-header-only)
  add_executable(header-only-test "main.cc")
  target_link_libraries(header-only-test fmt::fmt-header-only)
  target_compile_options(header-only-test PRIVATE ${PEDANTIC_COMPILE_FLAGS})
  target_include_directories(header-only-test PUBLIC SYSTEM .)
endif ()
