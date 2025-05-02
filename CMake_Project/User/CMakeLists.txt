cmake_minimum_required(VERSION 3.22)

project(User)
add_library(User INTERFACE)

include(${CMAKE_CURRENT_SOURCE_DIR}/../Scripts/cmake_tools.cmake)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

add_head_path(User User)
add_src_path(User c ${CMAKE_SOURCE_DIR}/User)

target_link_directories(User INTERFACE
)

target_link_libraries(User INTERFACE
)



