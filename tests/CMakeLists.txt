
project(PROJECT_NAME_TESTS)

file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
add_executable(PROJECT_NAME_TESTS ${SOURCES})

enable_testing()
find_package(GTest)

target_link_libraries(PROJECT_NAME_TESTS PRIVATE PROJECT_NAME_SRC GTest::gtest GTest::gtest_main)

#[===[
# TODO Fix res/ copying for Miltu-Config Generators
add_custom_command(
    TARGET PROJECT_NAME_TESTS POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory_if_different
            "${CMAKE_SOURCE_DIR}/res" "${CMAKE_CURRENT_BINARY_DIR}/res")
]===]

include(GoogleTest)
gtest_discover_tests(PROJECT_NAME_TESTS)
#add_test(AllTestsInMain main)
