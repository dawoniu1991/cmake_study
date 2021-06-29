# CMakeLists.txt
# CMake最低版本要求
cmake_minimum_required(VERSION 3.5)

# 项目名称
project(test_6)

if(WIN32)
	message(STATUS "Now is windows")
elseif(APPLE)
	message(STATUS "Now is Apple systens.")
elseif(UNIX)
	message(STATUS "Now is UNIX-like OS's.=====================================")
endif()

