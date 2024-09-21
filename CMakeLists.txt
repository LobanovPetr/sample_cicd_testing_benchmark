cmake_minimum_required(VERSION 3.14)

project(sample)

add_executable(
    summator
    main.cpp
    sum.cpp
    )

target_include_directories(summator PUBLIC include)

include(FetchContent)
FetchContent_Declare(
    googletest
    GIT_REPOSITORY https://github.com/google/googletest.git
    GIT_TAG v1.15.2
)
FetchContent_MakeAvailable(googletest)

enable_testing()
add_executable(tests test.cpp sum.cpp)
target_include_directories(tests PUBLIC include)
target_link_libraries(tests gtest_main)

include(GoogleTest)
gtest_discover_tests(tests)
