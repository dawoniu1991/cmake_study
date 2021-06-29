cmake_minimum_required (VERSION 2.8)

project (demo)

set( SRC_LIST ./main.c 
	./testFunc1.c 
	./testFunc.c)

message(${SRC_LIST})
add_executable(main ${SRC_LIST})

