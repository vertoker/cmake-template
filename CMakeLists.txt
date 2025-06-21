
cmake_minimum_required(VERSION 3.12) # cmake version here
project(PROJECT_NAME VERSION 0.1 LANGUAGES CXX) # Your project name here

execute_process(COMMAND ${CMAKE_COMMAND} --version)

# Options Zone
option(PROJECT_BUILD_APPDIR "Pack linux build" OFF)
option(PROJECT_BUILD_TESTS "Build tests" OFF)

# Variables Zone
set(CMAKE_CXX_STANDARD 17) # C++ version here
set(CMAKE_CXX_STANDARD_REQUIRED ON) # Mayde you doesn't need std
#set(CMAKE_INTERPROCEDURAL_OPTIMIZATION TRUE) # Link Time Optimization

#set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Release>:Release>")
#set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

# Build
add_subdirectory(src)
add_executable(${CMAKE_PROJECT_NAME} src/main.cpp)
target_link_libraries(PROJECT_NAME PRIVATE PROJECT_NAME_SRC)


# Disable console
if (DISABLE_CONSOLE)
	if(MSVC) # If using the VS compiler...
		set_target_properties("${CMAKE_PROJECT_NAME}" PROPERTIES LINK_FLAGS "/SUBSYSTEM:WINDOWS /ENTRY:mainCRTStartup")
	endif()
	# For others idk how to solve this, search through the internet or something
endif()

# Scripts execution

if (WIN32)
	#execute_process(COMMAND "${CMAKE_PROJECT_NAME}/scripts/compile-shaders.bat")
	execute_process(COMMAND "${CMAKE_PROJECT_NAME}/scripts/copy-resources.bat")
endif (WIN32)

if (UNIX)
	#execute_process(COMMAND sh "${CMAKE_CURRENT_SOURCE_DIR}/scripts/compile-shaders.sh")
	execute_process(COMMAND sh "${CMAKE_CURRENT_SOURCE_DIR}/scripts/copy-resources.sh")
endif (UNIX)
