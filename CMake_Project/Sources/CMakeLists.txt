cmake_minimum_required(VERSION 3.22)

project(Sources)
add_library(Sources INTERFACE)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

add_head_path(Sources Sources)
add_src_path(Sources c ${CMAKE_SOURCE_DIR}/Sources)

target_link_directories(Sources INTERFACE
)

target_link_libraries(Sources INTERFACE
)



