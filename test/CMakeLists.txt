
project(PROJECT_NAME_TEST)

file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
add_executable(PROJECT_NAME_TEST ${SOURCES})

enable_testing()
find_package(GTest)

#if (NOT ${PROJECT_NAME_SRC})
    #add_subdirectory("../src/")
#endif()

target_link_libraries(PROJECT_NAME_TEST PRIVATE PROJECT_NAME_SRC GTest::gtest)

add_custom_command(
    TARGET PROJECT_NAME_TEST POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory_if_different
            "${CMAKE_SOURCE_DIR}/res" "${CMAKE_CURRENT_BINARY_DIR}/res")

include(GoogleTest)
gtest_discover_tests(PROJECT_NAME_TEST)
