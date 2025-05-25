cmake_minimum_required(VERSION 3.20)
project(SeaOtter)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find SDL2 (requires SDL2 installed on your system)
find_package(SDL2 REQUIRED)
find_package(OpenGL REQUIRED)

include_directories(
        ${SDL2_INCLUDE_DIRS}
        ${OPENGL_INCLUDE_DIR}
        imgui
        imgui/backends
)

file(GLOB IMGUI_SOURCES
        imgui/*.cpp
        imgui/backends/imgui_impl_sdl.cpp
        imgui/backends/imgui_impl_opengl3.cpp
)

add_executable(${PROJECT_NAME} main.cpp ${IMGUI_SOURCES})

target_link_libraries(${PROJECT_NAME}
        ${SDL2_LIBRARIES}
        ${OPENGL_gl_LIBRARY}  # OpenGL library
)