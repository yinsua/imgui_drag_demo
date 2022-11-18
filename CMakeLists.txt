cmake_minimum_required(VERSION 3.22)
project(imgui_drag_demo)

set(CMAKE_CXX_STANDARD 20)

set(IMGUI_DIR "C:/imgui")
include_directories(${IMGUI_DIR})
include_directories(${PROJECT_SOURCE_DIR})

file(GLOB SOURCE
        ${IMGUI_DIR}/*.cpp
        ${IMGUI_DIR}/*.h
        ${IMGUI_DIR}/backends/imgui_impl_glfw.*
        ${IMGUI_DIR}/backends/imgui_impl_opengl3.*
        ${IMGUI_DIR}/backends/imgui_impl_win32.*)

# glfw
set(glfw3_DIR "C:\\Program Files (x86)\\GLFW\\lib\\cmake\\glfw3")
find_package(glfw3 REQUIRED)
include_directories(${GLFW_INCLUDE_DIRS})
link_libraries(${GLFW_LIBRARY_DIRS})

# opengl
find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

# glew
set(glew_DIR "C:\\Program Files (x86)\\glew\\lib\\cmake\\glew")
find_package(GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})

add_executable(imgui_drag_demo main.cpp ${SOURCE})
target_link_libraries(imgui_drag_demo
        glfw
        ${OPENGL_LIBRARIES}
        GLEW::GLEW )