cmake_minimum_required (VERSION 3.17)
project(CPP-PROJECT-BOOTSTRAP)

set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

option(BUILD_TEST "Build the unit tests" OFF)

enable_testing()

# we want to choice our own prefix to prevent naming issues
set(CMAKE_STATIC_LIBRARY_PREFIX "")

set(SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src")
set(INSTALL_BIN_DIR "${CMAKE_CURRENT_SOURCE_DIR}/dist/bin/${CMAKE_BUILD_TYPE}")
set(INSTALL_LIB_DIR "${CMAKE_CURRENT_SOURCE_DIR}/dist/lib/${CMAKE_BUILD_TYPE}")
set(INSTALL_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/dist/include")

add_subdirectory(externals)
add_subdirectory(src)

if(BUILD_TEST)
  add_subdirectory(test)
endif()
