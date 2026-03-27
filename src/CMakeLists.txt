# Source files in src go here
# This is not recursive
# Subdirectories for the same target should be added with the add_subdirectory() command
# They should have their own CMakeLists.txt file with the command target_sources()
# Which will link additional sources to the existing target without creating a disparate one
# The subdirectory will also have its own include directory
# The CMakeLists.txt file should also have a target_include_directories() command like the one below
# However, if the content of the subdirectory is sufficiently large
# Consider making it its own target to avoid unnecessary recompilation
add_library(Custodes_SDC
        # list of cpp files follows
        main.cpp
)

# Header files go in include directory and are automatically discovered
target_include_directories(Custodes_SDC PUBLIC include)

# Compile definitions by build configuration
target_compile_definitions(
        Custodes_SDC PRIVATE

        # Debug
        $<$<CONFIG:Debug>:DEBUG_MODE=1>
        $<$<CONFIG:Debug>:ENABLE_ASSERTS>

        # Release
        $<$<CONFIG:Release>:RELEASE_MODE=1>
        $<$<CONFIG:Release>:NO_LOGGING>

        # MinSizeRel
        $<$<CONFIG:MinSizeRel>:OPTIMIZE_FOR_SIZE=1>

        # RelWithDebInfo
        $<$<CONFIG:RelWithDebInfo>:RELEASE_MODE=1>
        $<$<CONFIG:RelWithDebInfo>:ENABLE_PROFILING>
)

# Compile options by build configuration
target_compile_options(
        Custodes_SDC PRIVATE
        $<$<CONFIG:Debug>:-g -O0 -Wall>
        $<$<CONFIG:Release>:-O3 -march=native -DNDEBUG>
        $<$<CONFIG:MinSizeRel>:-Os -DNDEBUG>
        $<$<CONFIG:RelWithDebInfo>:-O2 -g>
)