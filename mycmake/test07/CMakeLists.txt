cmake_minimum_required (VERSION 2.8)

project (demo)

set (EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
message(${EXECUTABLE_OUTPUT_PATH})
aux_source_directory (src SRC_LIST)

message(${SRC_LIST})
include_directories (include)

add_executable (main ${SRC_LIST})

