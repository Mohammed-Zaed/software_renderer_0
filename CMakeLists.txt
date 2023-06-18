cmake_minimum_required(VERSION 3.26)
project(software_renderer C)
set(CMAKE_C_STANDARD 99)

# Build vendor code
# Build SDL Static 
add_subdirectory(vendor/SDL)
#set(SDL_SHARED TRUE CACHE BOOL "Build a SDL shared library (if available)")
set(SDL_STATIC TRUE CACHE BOOL "Build a SDL static library (if available)")
# set_property(DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/_deps/sdl-src" PROPERTY EXCLUDE_FROM_ALL TRUE)

set(source_files 
    src/main.c
)

add_executable(software_renderer ${source_files}) 

target_include_directories(software_renderer
                                PRIVATE "vendor/SDL/include"
)
target_link_libraries(software_renderer 
                        PRIVATE SDL2::SDL2
                    )

target_compile_options(software_renderer PRIVATE -Wall -Wextra)
