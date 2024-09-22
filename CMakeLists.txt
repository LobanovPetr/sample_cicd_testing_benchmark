cmake_minimum_required(VERSION 3.14)

project(sample)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS ON)

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

FetchContent_Declare(
    googlebenchmark
    GIT_REPOSITORY https://github.com/google/benchmark.git
    GIT_TAG v1.7.0
)

FetchContent_MakeAvailable(
    googletest
    googlebenchmark
)

###### Testing
enable_testing()
add_executable(tests test.cpp sum.cpp)
target_include_directories(tests PUBLIC include)
target_link_libraries(tests gtest_main)

include(GoogleTest)
gtest_discover_tests(tests)

###### Benchmarking
add_executable(g_benchmark benchmark.cpp sum.cpp)
target_compile_options(g_benchmark PRIVATE -Wno-error)
target_compile_options(g_benchmark PRIVATE -Wno-unused-parameter)
set_target_properties(g_benchmark PROPERTIES
    COMPILE_OPTIONS "-Wno-error"  # Или "-Wno-unused-parameter"
)
target_include_directories(g_benchmark PUBLIC include)
target_link_libraries(g_benchmark benchmark::benchmark)
