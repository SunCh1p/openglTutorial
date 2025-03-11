cmake_minimum_required(VERSION 3.10.0)
project(openglTutorial VERSION 0.1.0 LANGUAGES C CXX)
cmake_policy(SET CMP0072 NEW)

find_package(OpenGL REQUIRED)

set(SOURCES
  src/main.cpp
  src/glad.c
)

set(GLFW_ROOT ${CMAKE_SOURCE_DIR}/external/glfw)

#add glfw subdirectory to the build
#add_subdirectory(external/glfw)

#define glfw as an imported static library
add_library(glfw STATIC IMPORTED)
set_target_properties(glfw PROPERTIES 
  IMPORTED_LOCATION "${GLFW_ROOT}/build/src/libglfw3.a"
  INTERFACE_INCLUDE_DIRECTORIES "${GLFW_ROOT}/include"
)

add_executable(openglTutorial ${SOURCES})

# Add the include directory for glad.h and glfw
target_include_directories(openglTutorial PRIVATE ${CMAKE_SOURCE_DIR}/include ${GLFW_ROOT}/include)
target_link_libraries(openglTutorial glfw OpenGL::GL)

