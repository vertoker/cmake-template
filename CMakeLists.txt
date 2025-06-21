
# Init

cmake_minimum_required(VERSION 3.12) # cmake version here
project(PROJECT_NAME VERSION 0.1 LANGUAGES CXX) # Your project name here

execute_process(COMMAND ${CMAKE_COMMAND} --version)

# Options
option(PROJECT_ASSEMBLE_APP "Assemble app directory" OFF)
option(PROJECT_BUILD_TESTS "Build tests" OFF)

# Variables
set(CMAKE_CXX_STANDARD 17) # C++ version here
set(CMAKE_CXX_STANDARD_REQUIRED ON) # Mayde you doesn't need std
#set(CMAKE_INTERPROCEDURAL_OPTIMIZATION TRUE) # Link Time Optimization

#set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Release>:Release>")
#set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")


# Build

add_executable(${CMAKE_PROJECT_NAME} "src/main.cpp")

add_subdirectory("src/")

if(PROJECT_ASSEMBLE_APP)
    include("${CMAKE_CURRENT_SOURCE_DIR}/dev/cmake/AssembleApp.cmake")
endif()

if (PROJECT_NAME_SRC) # if src is empty
	target_link_libraries(PROJECT_NAME PRIVATE PROJECT_NAME_SRC)
endif()


# Tests

if(PROJECT_BUILD_TESTS)
    enable_testing()
    add_subdirectory("test/")
endif()



# Disable console
if (DISABLE_CONSOLE)
	if(MSVC) # If using the VS compiler...
		set_target_properties("${CMAKE_PROJECT_NAME}" PROPERTIES LINK_FLAGS "/SUBSYSTEM:WINDOWS /ENTRY:mainCRTStartup")
	endif()
	# For others idk how to solve this, search through the internet or something
endif()

# Scripts execution

#[===[
if (WIN32)
	#execute_process(COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/scripts/compile-shaders.bat")
	execute_process(COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/scripts/copy-resources.bat")
endif()

if (UNIX)
	#execute_process(COMMAND sh "${CMAKE_CURRENT_SOURCE_DIR}/scripts/compile-shaders.sh")
	execute_process(COMMAND sh "${CMAKE_CURRENT_SOURCE_DIR}/scripts/copy-resources.sh")
endif()
]===]
