cmake_minimum_required(VERSION 2.6)
cmake_policy(SET CMP0003 NEW)

#####################################################################
# General project properties
#####################################################################

project(igraphpp C CXX)

#####################################################################
# Build options
#####################################################################

#####################################################################
# Version information
#####################################################################

#####################################################################
# Tweaking CMake
#####################################################################

#####################################################################
# Find dependencies
#####################################################################

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/etc/cmake;${CMAKE_MODULE_PATH})
find_package(igraph REQUIRED)

#####################################################################
# Compiler flags for different build configurations
#####################################################################

set(CMAKE_C_FLAGS   "${CMAKE_ARCH_FLAGS} -Wall")
set(CMAKE_CXX_FLAGS "${CMAKE_ARCH_FLAGS} -Wall")
set(CMAKE_C_FLAGS_DEBUG   "${CMAKE_ARCH_FLAGS} -O0 -ggdb")
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_ARCH_FLAGS} -O0 -ggdb")
set(CMAKE_C_FLAGS_RELEASE   "${CMAKE_ARCH_FLAGS} -O3 -DNDEBUG -Wall -s")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_ARCH_FLAGS} -O3 -DNDEBUG -Wall -s")
set(CMAKE_C_FLAGS_PROFILING "${CMAKE_ARCH_FLAGS} -pg")
set(CMAKE_CXX_FLAGS_PROFILING "${CMAKE_ARCH_FLAGS} -pg")

include_directories(${igraph_INCLUDE_DIRS}
                    ${CMAKE_CURRENT_SOURCE_DIR}/include
                    ${CMAKE_CURRENT_BINARY_DIR}/include)

#####################################################################
# Process subdirectories
#####################################################################

add_subdirectory(src)
