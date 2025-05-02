cmake_minimum_required(VERSION 3.22)

project(SDK)
add_library(SDK INTERFACE)
include(${CMAKE_CURRENT_SOURCE_DIR}/../Scripts/cmake_tools.cmake)

# Enable CMake support for ASM and C languages
enable_language(C ASM)

add_head_path(SDK SDK)

add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/devices/${CUSTOM_CMAKE_CHIP}/startup)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/devices)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/adc_sar)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/clock/MPC57xx)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/edma)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/etimer)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/flexcan)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/interrupt)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/linflexd)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/pins)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/power)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/power/MPC57xx)
add_src_path(SDK c ${CMAKE_SOURCE_DIR}/SDK/platform/drivers/src/pit)

add_src_path(SDK c  ${CMAKE_SOURCE_DIR}/SDK/rtos/FreeRTOS_PA/Source)
add_src_path(SDK s  ${CMAKE_SOURCE_DIR}/SDK/rtos/FreeRTOS_PA/Source/portable/GCC/PowerPC)
add_src_path(SDK c  ${CMAKE_SOURCE_DIR}/SDK/rtos/FreeRTOS_PA/Source/portable/GCC/PowerPC)
add_src_path(SDK c  ${CMAKE_SOURCE_DIR}/SDK/rtos/FreeRTOS_PA/Source/portable/MemMang)

add_src_path(SDK c  ${CMAKE_SOURCE_DIR}/SDK/rtos/osif)

target_link_directories(SDK INTERFACE
)

target_link_libraries(SDK INTERFACE
)


