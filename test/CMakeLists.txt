
project(PROJECT_NAME_TEST)

file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

find_package(GTest)

add_executable(PROJECT_NAME_TEST ${SOURCES})

target_link_libraries(PROJECT_NAME_TEST PRIVATE VoxelEngineSrc GTest::gtest_main)

# HACK: copy res to test/ folder for fixing problem compatibility MultiConfig
# and non MultiConfig builds. Delete in future and use only root res folder Also
# this resolve problem with ctests, because it set cwd to
# ${CMAKE_CURRENT_BINARY_DIR}
add_custom_command(
    TARGET PROJECT_NAME_TEST
    POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory_if_different
            "${CMAKE_SOURCE_DIR}/resources" "{CMAKE_CURRENT_BINARY_DIR}/resources"
)

include(GoogleTest)
gtest_discover_tests(PROJECT_NAME_TEST)