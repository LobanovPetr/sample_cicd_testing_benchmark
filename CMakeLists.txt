cmake_minimum_required(VERSION 3.14)

project(sample)

set(SOURCES
    main.cpp
    sum.cpp)

set(HEADERS
    include/sum.h)

add_executable(
    summator
    ${SOURCES}
    ${HEADERS}
    )

target_include_directories(summator PUBLIC include)
