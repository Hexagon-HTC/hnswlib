cmake_minimum_required (VERSION 2.6)
project(hnsw_lib
    LANGUAGES CXX)

add_library(hnswlib INTERFACE)

target_include_directories(hnswlib
  INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
      $<INSTALL_INTERFACE:include>)

file(GLOB_RECURSE INCLUDES
    ${CMAKE_SOURCE_DIR}/hnswlib/*.h 
)

install(TARGETS hnswlib EXPORT hnswlib)
install(FILES ${INCLUDES} DESTINATION include/hnswlib)
install(EXPORT hnswlib DESTINATION lib/cmake/hnswlib FILE hnswlib-config.cmake)
