cmake_minimum_required(VERSION 3.22)
project(module_compression_7z LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

add_subdirectory("../src/bit7z" extern/bit7z)
include_directories("../include/bit7z")

file(
    GLOB_RECURSE
    source_files
    ${CMAKE_SOURCE_DIR}/../../c++/*.cpp
    ${CMAKE_SOURCE_DIR}/../../c++/*.c
    ${CMAKE_SOURCE_DIR}/../../c++/*.hpp
    ${CMAKE_SOURCE_DIR}/../../c++/*.h
)

add_library(module_compression_7z SHARED ${source_files})

target_link_libraries(module_compression_7z PRIVATE bit7z)