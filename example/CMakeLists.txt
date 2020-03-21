set_target_properties(ttv PROPERTIES LINKER_LANGUAGE CXX)

add_executable(interface1 interface1.cpp)
target_link_libraries(interface1 PRIVATE ttv)

add_executable(interface2 interface2.cpp)
target_link_libraries(interface2 PRIVATE ttv)

add_executable(interface3 interface3.cpp)
target_link_libraries(interface3 PRIVATE ttv)
