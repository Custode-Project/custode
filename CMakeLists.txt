cmake_minimum_required(VERSION 3.28)
project(
        Custodes_SDC
        VERSION 0.0.1
        DESCRIPTION "Custodes is a modern, blazingly-fast SDC library with sensible defaults built to last."
        LANGUAGES CXX
)

# Configure C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(PROJECT_SOURCE_DIR STREQUAL PROJECT_BINARY_DIR)
    message(FATAL_ERROR "In-source builds are not permitted.")
endif ()
add_subdirectory(src)
add_subdirectory(tools)