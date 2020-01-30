cmake_minimum_required(VERSION 3.10)

# set the project name and version
project(ttv)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(OpenMP)

if( OpenMP_FOUND )
  set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()

# add_compile_options(-Wall -Werror -Wextra -g)

# set_target_properties(ttv PROPERTIES LINKER_LANGUAGE CXX)

include_directories(
  "${PROJECT_SOURCE_DIR}/include"
  "${PROJECT_SOURCE_DIR}/include/tlib"
  "${PROJECT_SOURCE_DIR}/include/tlib/detail"
  "${PROJECT_SOURCE_DIR}/test/include"
)

add_subdirectory(include)
add_subdirectory(example) 

enable_testing() 
add_subdirectory(test)


