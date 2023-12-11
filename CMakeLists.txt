cmake_minimum_required(VERSION 3.28)

project(imguitest)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "-Wall -Wextra ")

find_package(glfw3 3.3 REQUIRED)
find_package(OpenGL REQUIRED)

set(
  IMGUILIB 
  ./deps/libs/imgui.cpp
  ./deps/libs/imgui_demo.cpp 
  ./deps/libs/imgui_draw.cpp 
  ./deps/libs/imgui_tables.cpp
  ./deps/libs/imgui_widgets.cpp
  ./deps/libs/imgui_impl_glfw.cpp
  ./deps/libs/imgui_impl_opengl3.cpp
  )

add_executable(app main.cpp glad.c ${IMGUILIB})


target_include_directories(app PUBLIC ./deps)
target_include_directories(app PUBLIC ./deps/imgui)

target_link_libraries(app glfw OpenGL::GL)
