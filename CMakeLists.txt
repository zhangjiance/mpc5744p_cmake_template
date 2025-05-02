cmake_minimum_required(VERSION 3.22)

# Setup compiler settings
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS ON)

set(CUSTOM_CMAKE_CHIP "MPC5744P")


# Define the build type
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Debug")
endif()

# Set the project name
set(CMAKE_PROJECT_NAME freertos_mpc5744p)

# Include toolchain file
include("CMake_Project/powerpc-eabivle_e200z4.cmake")

# Enable compile command to ease indexing with e.g. clangd
set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

# Core project settings
project(${CMAKE_PROJECT_NAME})
message("Build type: " ${CMAKE_BUILD_TYPE})

# Create an executable object type
add_executable(${CMAKE_PROJECT_NAME}
)

add_subdirectory(CMake_Project/Generated_Code)
add_subdirectory(CMake_Project/SDK)
add_subdirectory(CMake_Project/Sources)
add_subdirectory(CMake_Project/Start_Code)

# Link directories setup
target_link_directories(${CMAKE_PROJECT_NAME} PRIVATE
    # Add user defined library search paths
)

# Add sources to executable
target_sources(${CMAKE_PROJECT_NAME} PRIVATE
    # Add user sources here
)

# Add include paths
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE
)

# Add project symbols (macros)
target_compile_definitions(${CMAKE_PROJECT_NAME} PRIVATE
    START_FROM_FLASH
    CPU_MPC5744P
    TURN_ON_CPU0
    USING_OS_FREERTOS
    DEV_ERROR_DETECT
)

# Add linked libraries
target_link_libraries(${CMAKE_PROJECT_NAME}
    Generated_Code
    SDK
    Sources
    Start_Code
)

set(HEX_FILE "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_PROJECT_NAME}.hex")
set(BIN_FILE "${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_PROJECT_NAME}.bin")

add_custom_command(
    TARGET ${CMAKE_PROJECT_NAME}
    POST_BUILD               
    COMMAND ${CMAKE_OBJCOPY} -O ihex $<TARGET_FILE:${CMAKE_PROJECT_NAME}> ${HEX_FILE}
    COMMENT "Generating HEX file: ${HEX_FILE}"
    VERBATIM
)

add_custom_command(
    TARGET ${CMAKE_PROJECT_NAME}
    POST_BUILD
    COMMAND ${CMAKE_OBJCOPY} -O binary $<TARGET_FILE:${CMAKE_PROJECT_NAME}> ${BIN_FILE}
    COMMENT "Generating BIN file: ${BIN_FILE}"
    VERBATIM
)

