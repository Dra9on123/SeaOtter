cmake_minimum_required(VERSION 3.20)
set(CMAKE_CXX_STANDARD 17)
project(SeaOtter)

add_subdirectory(thirdparty)

add_executable(SeaOtter
        src/main.cpp
)
target_compile_definitions(SeaOtter PRIVATE SDL_MAIN_HANDLED)
target_include_directories(SeaOtter PRIVATE ${SDL_INCLUDE_DIRS})

target_link_libraries(SeaOtter PRIVATE
        imguidocking
        SDL2-static
        OpenGL::GL
)
find_package(OpenGL REQUIRED)

