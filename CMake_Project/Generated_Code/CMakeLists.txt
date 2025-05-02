cmake_minimum_required(VERSION 3.22)

project(Generated_Code)
add_library(Generated_Code INTERFACE)

include(${CMAKE_CURRENT_SOURCE_DIR}/../Scripts/cmake_tools.cmake)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

add_head_path(Generated_Code Generated_Code)
add_src_path(Generated_Code c ${CMAKE_SOURCE_DIR}/Generated_Code)

target_link_directories(Generated_Code INTERFACE
)

target_link_libraries(Generated_Code INTERFACE
)



