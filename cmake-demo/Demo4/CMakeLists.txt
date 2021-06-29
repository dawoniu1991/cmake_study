# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (Demo4)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

# 是否使用自己的 MathFunctions 库
option (USE_MYMATH
	   "Use provided math implementation" ON)


message("hello")

message("CMAKE_INCLUDE_PATH=====${CMAKE_INCLUDE_PATH}")
message("ZMQ_INCLUDE_DIR=====${ZMQ_INCLUDE_DIR}")
find_path( ZMQ_INCLUDE_DIR MathFunctions.h  ${PROJECT_SOURCE_DIR} )
message("ZMQ_INCLUDE_DIR=end====${ZMQ_INCLUDE_DIR}")

message("res001==${PROJECT_SOURCE_DIR}")

message("res002===${PROJECT_BINARY_DIR}")
message("res003=====${USE_MYMATH}")
message("CMAKE_MODULE_PATH =====${CMAKE_MODULE_PATH}")
list(APPEND CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake/Modules)
message("CMAKE_MODULE_PATH end=====${CMAKE_MODULE_PATH}")
# 加入一个配置头文件，用于处理 CMake 对源码的设置
configure_file (
  "${PROJECT_SOURCE_DIR}/config.h.in"
  "${PROJECT_BINARY_DIR}/config.h"
  )


# 是否加入 MathFunctions 库
if (USE_MYMATH)
  message("abcd ====")
  message("res004==EXTRA_LIBS=====${EXTRA_LIBS}")
  include_directories ("${PROJECT_SOURCE_DIR}/math")
  add_subdirectory (math)
  set (EXTRA_LIBS ${EXTRA_LIBS} MathFunctions)
  message("res005===EXTRA_LIBS========${EXTRA_LIBS}")
endif (USE_MYMATH)

# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
aux_source_directory(. DIR_SRCS)

# 指定生成目标
add_executable (Demo ${DIR_SRCS})
target_link_libraries (Demo  ${EXTRA_LIBS})
