cmake_minimum_required(VERSION 3.15)
project(uprotocol-core-api)

find_package(Protobuf REQUIRED)

# proto generation
set(protobuf_MODULE_COMPATIBLE TRUE)

set (CMAKE_CURRENT_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/src/main/proto)

file(GLOB_RECURSE PROTO_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.proto)

include_directories(${protobuf_INCLUDE_DIRS})
include_directories(${CMAKE_BINARY_DIR})


#message(STATUS "CMAKE_CURRENT_SOURCE_DIR: ${CMAKE_CURRENT_SOURCE_DIR}")

protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS ${PROTO_FILES})

add_executable(MyTarget ${PROTO_SRCS} ${PROTO_HDRS} main.cpp)

