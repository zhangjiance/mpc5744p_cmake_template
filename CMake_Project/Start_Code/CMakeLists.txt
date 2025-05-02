cmake_minimum_required(VERSION 3.22)

project(Start_Code)
add_library(Start_Code INTERFACE)

# Enable CMake support for ASM and C languages
enable_language(ASM)

target_compile_definitions(Start_Code INTERFACE 
)

add_head_path(Start_Code Start_Code)
add_src_path(Sources S ${CMAKE_SOURCE_DIR}/Project_Settings/Startup_Code)

target_link_directories(Start_Code INTERFACE
)

target_link_libraries(Start_Code INTERFACE
)



