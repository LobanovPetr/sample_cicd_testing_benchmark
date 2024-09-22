add_executable(g_benchmark benchmark.cpp)
target_link_libraries(g_benchmark sum benchmark::benchmark)

# target_compile_options(g_benchmark PRIVATE -Wno-error)
# target_compile_options(g_benchmark PRIVATE -Wno-unused-parameter)

# set_target_properties(g_benchmark PROPERTIES
#    COMPILE_OPTIONS "-Wno-error"  # Или "-Wno-unused-parameter"
#)

