cmake_minimum_required(VERSION 3.20)
project(SeaOtter)
set(CMAKE_CXX_STANDARD 17)

add_subdirectory(thirdparty)
find_package(OpenGL REQUIRED)

add_executable(SeaOtter
        src/main.cpp
)

target_compile_definitions(SeaOtter PRIVATE SDL_MAIN_HANDLED)

# SDL includes (passed through from thirdparty)
target_include_directories(SeaOtter PRIVATE
        ${CMAKE_SOURCE_DIR}/thirdparty/sdl2/include
        ${CMAKE_BINARY_DIR}/thirdparty/sdl2/include
        ${CMAKE_SOURCE_DIR}/thirdparty/sdlimage
)

target_link_libraries(SeaOtter PRIVATE
        imguidocking
        SDL2-static
        SDL2_image-static
        OpenGL::GL
)
