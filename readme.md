# OpenGLStart

This project is a basic OpenGL application that renders a colored triangle. It is set up to use MinGW, GLFW, and GLEW. Below are the steps to set up and run this project on a Windows machine.

## Prerequisites

1. **Visual Studio Code**: Download and install [Visual Studio Code](https://code.visualstudio.com/).
2. **MinGW-w64**: Download and install MinGW-w64. Ensure it is installed in `C:\MinGW`.
3. **CMake**: Download and install [CMake](https://cmake.org/download/).

## Setting Up MinGW

1. **Download MinGW-w64**: Download from the [MinGW-w64 SourceForge page](https://sourceforge.net/projects/mingw-w64/files/).
2. **Install MinGW-w64**: Install it to `C:\MinGW`.
3. **Add MinGW to PATH**:
   - Open "Environment Variables".
   - Edit the `Path` variable and add `C:\MinGW\bin`.

## Setting Up GLFW and GLEW

1. **Download GLFW**:
   - Download the precompiled binaries from [GLFW Download](https://www.glfw.org/download.html).
   - Extract the contents and copy `lib-vc2015/glfw3.lib` to `C:\MinGW\lib`.
   - Copy `include/GLFW` to `C:\MinGW\include`.

2. **Download GLEW**:
   - Download the latest binary release from [GLEW Download](http://glew.sourceforge.net/).
   - Extract the contents and copy `lib/Release/x64/glew32.lib` to `C:\MinGW\lib`.
   - Copy `include/GL` to `C:\MinGW\include`.

3. **Copy DLLs**:
   - Copy `bin/Release/x64/glew32.dll` from the GLEW binaries to `C:\Windows\System32`.

## Project Structure

The project directory structure should look like this:

OpenGLStart/
├── include/
│ ├── GL/
│ │ ├── glew.h
│ └── GLFW/
│ ├── glfw3.h
├── lib/
│ ├── glew32.lib
│ ├── glfw3.lib
├── src/
│ └── main.cpp
├── CMakeLists.txt
└── .vscode/
└── settings.json


## Configuration Files

### `CMakeLists.txt`

```cmake
cmake_minimum_required(VERSION 3.10)
project(OpenGLStart)

set(CMAKE_CXX_STANDARD 11)

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIR} "C:/MinGW/include")
link_directories("C:/MinGW/lib")

add_executable(OpenGLStart src/main.cpp)
target_link_libraries(OpenGLStart ${OPENGL_LIBRARIES} glfw3 glew32)

### `.vscode/settings.json`


{
  "cmake.generator": "MinGW Makefiles",
  "cmake.configureSettings": {
    "CMAKE_MAKE_PROGRAM": "C:/MinGW/bin/mingw32-make.exe",
    "CMAKE_C_COMPILER": "C:/MinGW/bin/gcc.exe",
    "CMAKE_CXX_COMPILER": "C:/MinGW/bin/g++.exe"
  }
}