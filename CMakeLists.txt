project(binbloom)
cmake_minimum_required(VERSION 3.10)

add_executable(binbloom binbloom.c getopt.c)
target_include_directories(binbloom SYSTEM ${CMAKE_CURRENT_SOURCE_DIR})

if(NOT MSVC)
  target_compile_options(binbloom PUBLIC -Wall -Wextra -O3)
endif()

install(TARGETS binbloom DESTINATION "bin")
install(DIRECTORY IDA_script DESTINATION "share/binbloom")

#"make package" will trigger this
SET(CPACK_GENERATOR "DEB")
SET(CPACK_DEBIAN_PACKAGE_MAINTAINER "@PapaZours")
INCLUDE(CPack)
