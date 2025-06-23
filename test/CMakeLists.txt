
project(PROJECT_NAME_TEST)

file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

find_package(GTest)

if (${SOURCES} AND ${GTest})
    
    add_executable(PROJECT_NAME_TEST ${SOURCES})

    if (PROJECT_NAME_SRC)
        target_link_libraries(PROJECT_NAME_TEST PRIVATE PROJECT_NAME_SRC GTest::gtest GTest::gtest_main)
    endif()

    add_custom_command(
        TARGET PROJECT_NAME_TEST
        POST_BUILD
        COMMAND ${CMAKE_COMMAND} -E copy_directory_if_different
                "${CMAKE_SOURCE_DIR}/resources" "{CMAKE_CURRENT_BINARY_DIR}/resources"
    )

    include(GoogleTest)
    gtest_discover_tests(PROJECT_NAME_TEST)
    
endif()