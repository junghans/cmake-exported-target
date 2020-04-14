cmake_minimum_required(VERSION 3.10)
project(simple C)
include(GNUInstallDirs)

set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR})

find_package(VORO REQUIRED)
add_library(public public.c)
target_link_libraries(public PUBLIC $<BUILD_INTERFACE:VORO::VORO> $<INSTALL_INTERFACE:${VORO_LIBRARY}>)

install(TARGETS public EXPORT Public_Targets LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR} ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR})
install(EXPORT Public_Targets FILE Public_Targets.cmake NAMESPACE Public:: DESTINATION ${CMAKE_INSTALL_LIBDIR}/cmake/Public)
