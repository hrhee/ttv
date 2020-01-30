cmake_minimum_required(VERSION 3.10)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Download and unpack googletest at configure time
configure_file(CMakeLists.txt.in googletest-download/CMakeLists.txt)
execute_process(COMMAND ${CMAKE_COMMAND} -G "${CMAKE_GENERATOR}" .
  RESULT_VARIABLE result
  WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/googletest-download )
if(result)
  message(FATAL_ERROR "CMake step for googletest failed: ${result}")
endif()
execute_process(COMMAND ${CMAKE_COMMAND} --build .
  RESULT_VARIABLE result
  WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/googletest-download )
if(result)
  message(FATAL_ERROR "Build step for googletest failed: ${result}")
endif()

# Prevent overriding the parent project's compiler/linker
# settings on Windows
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)

# Add googletest directly to our build. This defines
# the gtest and gtest_main targets.
add_subdirectory(${CMAKE_CURRENT_BINARY_DIR}/googletest-src
                 ${CMAKE_CURRENT_BINARY_DIR}/googletest-build
                 EXCLUDE_FROM_ALL)

# The gtest/gtest_main targets carry header search path
# dependencies automatically when using CMake 2.8.11 or
# later. Otherwise we have to add them here ourselves.
if (CMAKE_VERSION VERSION_LESS 2.8.11)
  include_directories("${gtest_SOURCE_DIR}/include")
endif()

# add the executable
add_executable(gtest_tlib_layout src/gtest_tlib_layout.cpp)
target_link_libraries(gtest_tlib_layout gtest_main ttv)
add_test(NAME gtest_tlib_layout COMMAND gtest_tlib_layout)

add_executable(gtest_tlib_mtv src/gtest_tlib_mtv.cpp include/gtest_aux.h)
target_link_libraries(gtest_tlib_mtv gtest_main ttv)
add_test(NAME gtest_tlib_mtv COMMAND gtest_tlib_mtv)

add_executable(gtest_tlib_shape src/gtest_tlib_shape.cpp include/gtest_aux.h)
target_link_libraries(gtest_tlib_shape gtest_main ttv)
add_test(NAME  gtest_tlib_shape COMMAND gtest_tlib_shape)

add_executable(gtest_tlib_strides src/gtest_tlib_strides.cpp include/gtest_aux.h)
target_link_libraries(gtest_tlib_strides gtest_main ttv)
add_test(NAME  gtest_tlib_strides COMMAND gtest_tlib_strides)

add_executable(gtest_tlib_ttv src/gtest_tlib_ttv.cpp include/gtest_aux.h)
target_link_libraries(gtest_tlib_ttv gtest_main ttv)
add_test(NAME  gtest_tlib_ttv COMMAND gtest_tlib_ttv)

add_executable(gtest_tlib_workload src/gtest_tlib_workload.cpp include/gtest_aux.h)
target_link_libraries(gtest_tlib_workload gtest_main ttv)
add_test(NAME  gtest_tlib_workload COMMAND gtest_tlib_workload)

