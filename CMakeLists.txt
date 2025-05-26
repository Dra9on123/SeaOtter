cmake_minimum_required(VERSION 3.16)
project(SeaOtterApp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

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

add_executable(SeaOtterApp
        src/main.cpp
        ${IMGUI_SOURCES}
)
target_include_directories(SeaOtterApp PRIVATE
        ${IMGUI_DIR}
        ${IMGUI_DIR}/backends
)

find_package(OpenGL REQUIRED)
target_link_libraries(SeaOtterApp PRIVATE OpenGL::GL)
