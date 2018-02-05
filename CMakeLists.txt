cmake_minimum_required(VERSION 3.2)
project(foo)

option(FOO_WITH_A "Use 'a' module" ON)

add_executable(foo foo.cpp)

if(FOO_WITH_A)
  find_package(a CONFIG REQUIRED)
  target_link_libraries(foo PUBLIC a::a)
  target_compile_definitions(foo PUBLIC FOO_WITH_A)
endif()

find_package(b CONFIG REQUIRED)
target_link_libraries(foo PUBLIC b::b)

enable_testing()
add_test(NAME foo COMMAND foo)
