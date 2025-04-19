set(SDL_STATIC ON CACHE BOOL "" FORCE)
set(SDL_SHARED OFF CACHE BOOL "" FORCE)
set(SDL_TEST OFF CACHE BOOL "" FORCE)

add_subdirectory(sdl2)

set(SDL_INCLUDE_DIRS
        ${CMAKE_CURRENT_SOURCE_DIR}/sdl2/include
        ${CMAKE_BINARY_DIR}/sdl2/include
)

file(GLOB IMGUI_SOURCES
        imguidocking/imgui.cpp
        imguidocking/imgui_draw.cpp
        imguidocking/imgui_tables.cpp
        imguidocking/imgui_widgets.cpp
        imguidocking/imgui_demo.cpp
        imguidocking/backends/imgui_impl_sdl2.cpp
        imguidocking/backends/imgui_impl_opengl3.cpp
)

add_library(imguidocking STATIC ${IMGUI_SOURCES})

target_include_directories(imguidocking PUBLIC
        imguidocking
        imguidocking/backends
        ${SDL_INCLUDE_DIRS}
)
