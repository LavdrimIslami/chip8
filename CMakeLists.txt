cmake_minimum_required(VERSION 3.22)
project(Chip8)

set(CMAKE_CXX_STANDARD 14)

# Must set the path to the main.cpp, for example: scripts/main.cpp if it is inside a folder
add_executable(${PROJECT_NAME}
        scripts/main.c
        scripts/display.c
        scripts/display.h
        scripts/chip8.c
        scripts/chip8.h
        scripts/input.c
        scripts/input.h)

# --- SDL2 SETUP ---
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/modules)
set(SDL2_PATH "SDL2/x86_64-w64-mingw32")

find_package(SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIR})
target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARY} ${SDL2_IMAGE_LIBRARIES})