cmake_minimum_required(VERSION 3.5)

project(rxcpp_vendor)

find_package(catkin REQUIRED)

include(ExternalProject)
ExternalProject_Add(rxcpp-6c283f36
  SOURCE_DIR rxcpp_src
  URL https://github.com/ReactiveX/RxCpp/archive/v4.1.0.tar.gz
  URL_MD5 6c283f36ce251f45146f7099aa9ef19a
  # arbitrary
  TIMEOUT 60
  # we copy the headers out of the extracted source directly, so
  # no need to configure, build or install anything.
  CONFIGURE_COMMAND ""
  BUILD_COMMAND ""
  INSTALL_COMMAND ""
)

catkin_package(CFG_EXTRAS rxcpp_vendor-extras.cmake)

install(
  DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/rxcpp_src/Rx/v2/src/rxcpp
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}/include
)
