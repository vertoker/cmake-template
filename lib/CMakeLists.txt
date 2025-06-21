
target_include_directories("${CMAKE_PROJECT_NAME}" PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/lib/") # lib

# Include folder in directory (etc. combine folders)

# Add Local libraries
#add_subdirectory("lib/glm")

# Add Package libraries (vcpkg)
#find_package(fmt CONFIG REQUIRED)

# Link Local Libraries
#target_link_libraries("${CMAKE_PROJECT_NAME}" PRIVATE glm glfw)

# Link Package Libraries (vcpkg)
#target_link_libraries(${CMAKE_PROJECT_NAME} PRIVATE fmt::fmt)
