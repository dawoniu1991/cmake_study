cmake_minimum_required (VERSION 2.8)

project (Demo1)
message("hello===")
message("res001===${PROJECT_SOURCE_DIR}")
message("res002=====${PROJECT_BINARY_DIR}")
add_executable(Demo main.cc)
