cmake_minimum_required(VERSION 3.20)

project(BlueRemoteFirmware)

add_custom_target(Firmware ALL
    COMMAND pio -c clion run
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
)

set(DIRS include lib src)
foreach (DIR ${DIRS})
    file(GLOB_RECURSE SOURCES "${DIR}/*.h" "${DIR}/*.cpp")
    target_sources(Firmware PRIVATE ${SOURCES})
endforeach()
