cmake_minimum_required (VERSION 3.5)
include (GNUInstallDirs)
project (Demo1)
message ("Generating build procedure for ${PROJECT_NAME} ...")

set (VERSION_MAJOR 1)
set (VERSION_MINOR 0)

file (GLOB HEADERS [a-zA-Z0-9_]*.h)
file (GLOB SOURCES [a-zA-Z0-9_]*.cpp)

set (GCC_COVERAGE_COMPILE_FLAGS "${GCC_COVERAGE_COMPILE_FLAGS} -g -O0")
include_directories (${PROJECT_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR})

add_library (${PROJECT_NAME} STATIC ${SOURCES} ${HEADERS})
set_target_properties (
   ${PROJECT_NAME}
   PROPERTIES OUTPUT_NAME ${PROJECT_NAME}
)
set_target_properties (
   ${PROJECT_NAME}
   PROPERTIES
   VERSION ${VERSION_MAJOR}.${VERSION_MINOR}
   SOVERSION ${VERSION_MAJOR}
)
