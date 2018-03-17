cmake_minimum_required(VERSION 3.5)

set(LIB_NAME my_lib)

project(${LIB_NAME})

file (GLOB_RECURSE SOURCES "*.cpp")
file (GLOB_RECURSE HEADERS "../include/${LIB_NAME}/*.hpp")

set(GCC_COVERAGE_COMPILE_FLAGS "-g")

include_directories(
  ${CMAKE_CURRENT_LIST_DIR}/../include/${LIB_NAME}
)

add_definitions(${GCC_COVERAGE_COMPILE_FLAGS})
add_library(${LIB_NAME} SHARED ${SOURCES})
install(TARGETS toot DESTINATION ${LIB_NAME}/${LIB_NAME})
install(FILES ${HEADERS} DESTINATION include/${LIB_NAME})