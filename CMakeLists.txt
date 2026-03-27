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

# Create .gitignore in build dir on initial configuration
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/.gitignore" "/*")

# Forbid in-source builds
if(PROJECT_SOURCE_DIR STREQUAL PROJECT_BINARY_DIR)
    message(FATAL_ERROR "In-source builds are not permitted.")
endif ()

# Check for and enable Interprocedural Optimization
include(CheckIPOSupported)
check_ipo_supported(RESULT ipo_supported)
set(CMAKE_INTERPROCEDURAL_OPTIMIZATION ${ipo_supported})
if (ipo_supported)
    message("IPO enabled")
endif ()

# Set output directories
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/$<CONFIGURATION>")

# Add subdirectories
add_subdirectory(src)
add_subdirectory(tools)