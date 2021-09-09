ke_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(motor-control C CXX ASM)i
set(CMAKE_C_STNDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(motor-control
        motor-control.c
)

# Pull in our pico_stdlib which pulls in commonly used features
target_link_libraries(motor-control pico_stdlib hardware_uart)

# enable usb output, disable uart output
pico_enable_stdio_usb(motor-control 1)
pico_enable_stdio_uart(motor-control 0)

# create map/bin/hex file etc.
pico_add_extra_outputs(motor-control)
