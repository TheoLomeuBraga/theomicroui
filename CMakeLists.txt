cmake_minimum_required(VERSION 2.8)
project(Minimalistic_ECS_Test C)

#sdl
set(SDL_STATIC ON)
add_subdirectory(libs/SDL)

set(CMAKE_EXE_LINKER_FLAGS "-static-libgcc -static-libstdc++")
include_directories(src demo libs/SDL/include)
add_executable(demo src/microui.c demo/main.c demo/renderer.c)

find_package(OpenGL REQUIRED)
target_link_libraries(demo SDL3::SDL3-static ${OPENGL_LIBRARIES})
link_libraries(demo SDL3::SDL3-static)
