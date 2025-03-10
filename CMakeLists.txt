cmake_minimum_required(VERSION 3.10.0)
project(openglTutorial VERSION 0.1.0 LANGUAGES C CXX)
cmake_policy(SET CMP0072 NEW)

find_package(OpenGL REQUIRED)

set(SOURCES
  src/main.cpp
  src/glad.c
)

add_executable(openglTutorial ${SOURCES})

# Add the include directory for glad.h
target_include_directories(openglTutorial PRIVATE ${CMAKE_SOURCE_DIR}/include)

target_link_libraries(openglTutorial glfw OpenGL::GL)

