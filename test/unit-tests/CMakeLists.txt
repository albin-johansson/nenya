cmake_minimum_required(VERSION 3.17)

project(nenya-test-unit-tests CXX)

set(SOURCE_FILES
    nenya_test.cpp
    test_main.cpp)

add_executable(UnitTests ${SOURCE_FILES})
set_compiler_options(UnitTests)

message("Ceral: ${NENYA_LIBRARY_DIR}/cereal")

target_include_directories(UnitTests
    PUBLIC .
    PUBLIC ${NENYA_INCLUDE_DIR}
    SYSTEM PUBLIC ${NENYA_LIBRARY_DIR}/cereal
    SYSTEM PUBLIC ${gtest_SOURCE_DIR}/include
    SYSTEM PUBLIC ${gtest_SOURCE_DIR}
    SYSTEM PUBLIC ${gmock_SOURCE_DIR}/include
    SYSTEM PUBLIC ${gmock_SOURCE_DIR})

target_link_libraries(UnitTests PUBLIC gtest)

add_test(NAME UnitTests COMMAND UnitTests)
