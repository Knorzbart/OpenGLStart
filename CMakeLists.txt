cmake_minimum_required(VERSION 3.10)
project(OpenGLStart)

set(CMAKE_CXX_STANDARD 11)

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR} "C:/MinGW/include")
link_directories("C:/MinGW/lib")

add_executable(OpenGLStart src/main.cpp)
target_link_libraries(OpenGLStart ${OPENGL_LIBRARIES} glfw3 glew32)
