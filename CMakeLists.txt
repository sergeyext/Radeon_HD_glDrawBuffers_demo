cmake_minimum_required(VERSION 3.8)
project(Radeon_HD_glDrawBuffers_demo)

find_library(LIBGLFW NAMES libglfw libglfw3 glfw glfw3 PATHS ${PROJECT_SOURCE_DIR}/lib)
find_library(LIBOPENGL NAMES GL opengl32)
find_library(LIBGLEW NAMES GLEW glew32 libglew32 glew32s glew32sd PATHS ${PROJECT_SOURCE_DIR}/lib)
set(LINK_LIBS ${LIBGLFW} ${LIBOPENGL} ${LIBGLEW})

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "MSVC")
  include_directories(${PROJECT_SOURCE_DIR}/include)
  add_definitions(-DGLEW_STATIC)
endif()

add_executable(glDrawBuffers_demo main.cpp)
target_link_libraries(glDrawBuffers_demo ${LINK_LIBS})
