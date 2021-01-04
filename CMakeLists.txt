########################################################################################################################
# To generate build files:
# cmake -B bin
#
# To build:
# cmake --build bin
########################################################################################################################

cmake_minimum_required(VERSION 3.15)
project(sandbox
    VERSION 1.0
    DESCRIPTION "C++ Sandbox"
    LANGUAGES CXX
)

# disable in-source builds
if (PROJECT_SOURCE_DIR STREQUAL PROJECT_BINARY_DIR)
    message(FATAL_ERROR
        "In source builds not supported, use `cmake -B bin` instead."
    )
endif()

# use C++17
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED true)

# compiler warnings
if (MSVC)
    add_compile_options(/W4)
else()
    add_compile_options(-Wall -Wextra)
endif()

# executable
add_executable(main
    src/main.cpp
)
