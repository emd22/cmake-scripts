cmake_minimum_required(VERSION 3.5)

set(PROG_NAME my_project)

project(${PROG_NAME} CXX)

file (GLOB_RECURSE SOURCES "*.cpp")
file (GLOB_RECURSE HEADERS "../include/${PROG_NAME}/*.hpp")
file (GLOB_RECURSE LIBS "../build/res/*.*")

set(GCC_COVERAGE_COMPILE_FLAGS "-g")

include_directories(
  ${CMAKE_CURRENT_LIST_DIR}/../include/${PROG_NAME}
)

add_definitions(${GCC_COVERAGE_COMPILE_FLAGS})
link_directories(${CMAKE_BINARY_DIR}/res)
add_executable(${PROG_NAME} ${SOURCES} ${HEADERS})
target_link_libraries(${PROG_NAME} ${LIBS})