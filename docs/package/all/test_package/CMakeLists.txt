cmake_minimum_required(VERSION 3.1)

project(test_package C) # if the project is pure C
project(test_package CXX) # if the project uses c++


include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)

conan_basic_setup(TARGETS)

find_package(package REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.c)
# don't link to ${CONAN_LIBS} or CONAN_PKG::package
target_link_libraries(${PROJECT_NAME} package::package)
