cmake_minimum_required(VERSION 3.16)
project(SeaOtterApp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find OpenGL
find_package(OpenGL REQUIRED)

# Add submodules
# Disable AV1 and JXL to avoid NASM and libjxl requirements
set(SDL_IMAGE_AVIF OFF CACHE BOOL "" FORCE)
set(SDL_IMAGE_JXL OFF CACHE BOOL "" FORCE)

add_subdirectory(thirdparty/SDL)
add_subdirectory(thirdparty/SDL_image)


# ImGui source files
set(IMGUI_DIR thirdparty/imgui)
set(IMGUI_SOURCES
        ${IMGUI_DIR}/imgui.cpp
        ${IMGUI_DIR}/imgui_draw.cpp
        ${IMGUI_DIR}/imgui_tables.cpp
        ${IMGUI_DIR}/imgui_widgets.cpp
        ${IMGUI_DIR}/imgui_demo.cpp
        ${IMGUI_DIR}/backends/imgui_impl_sdl3.cpp
        ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
)

# Main executable
add_executable(SeaOtterApp
        src/main.cpp
        ${IMGUI_SOURCES}
)

# Include directories
target_include_directories(SeaOtterApp PRIVATE
        ${IMGUI_DIR}
        ${IMGUI_DIR}/backends
        thirdparty/SDL/include
        thirdparty/SDL_image/include
)

# Link libraries
target_link_libraries(SeaOtterApp PRIVATE
        SDL3-static           # or SDL3 if you're using shared
        SDL3_image-static     # or SDL3_image
        OpenGL::GL
)
