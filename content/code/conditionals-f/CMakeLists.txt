# set minimum cmake version
cmake_minimum_required(VERSION 3.13)

# project name and language
project(conditionals LANGUAGES Fortran)

# BUILD_SHARED_LIBS is a global flag offered by CMake
# to toggle the behavior of add_library
set(BUILD_SHARED_LIBS OFF)

if(BUILD_SHARED_LIBS)
  message(STATUS "Build shared library")
  add_library(message SHARED)
else()
  message(STATUS "Build static library")
  add_library(message STATIC)
endif()

target_sources(message
  PUBLIC
    message.f90
  )

add_executable(hello-world hello-world.f90)

target_link_libraries(hello-world PRIVATE message)
