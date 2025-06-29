
# Init

cmake_minimum_required(VERSION 3.10) # cmake version here
project(PROJECT_NAME VERSION 0.1 LANGUAGES CXX) # Your project name here

execute_process(COMMAND ${CMAKE_COMMAND} --version)

# Options
option(PROJECT_ASSEMBLE_BUILD "Assemble app in build directory" OFF)
option(PROJECT_BUILD_TESTS "Build tests" OFF)

# Variables
set(CMAKE_CXX_STANDARD 17) # C++ version here
set(CMAKE_CXX_STANDARD_REQUIRED ON) # Maybe you doesn't need std
set(CMAKE_INTERPROCEDURAL_OPTIMIZATION TRUE) # LTO
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Build

add_executable(PROJECT_NAME "src/main.cpp")
add_subdirectory("src/")

if(PROJECT_ASSEMBLE_BUILD)
    include("${CMAKE_CURRENT_SOURCE_DIR}/dev/cmake/AssembleApp.cmake")
endif()

if (PROJECT_NAME_SRC) # if src is empty
	target_link_libraries(PROJECT_NAME PUBLIC PROJECT_NAME_SRC)
endif()

# Dependencies
find_package(fmt CONFIG REQUIRED)
target_link_libraries(PROJECT_NAME PUBLIC fmt::fmt)

# Tests
if(PROJECT_BUILD_TESTS)
    add_subdirectory("tests/")
endif()
