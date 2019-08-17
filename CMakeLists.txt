project(nginx-custom-data NONE)
cmake_minimum_required(VERSION 2.8)

set(CPACK_PACKAGE_NAME "${CMAKE_PROJECT_NAME}")
set(CPACK_PACKAGE_VERSION "1.0.0")
set(CPACK_SOURCE_PACKAGE_FILE_NAME "${CMAKE_PROJECT_NAME}-${CPACK_PACKAGE_VERSION}")
set(CPACK_SOURCE_IGNORE_FILES "/build/;/.git/;~$;${CPACK_SOURCE_IGNORE_FILES}")
set(CPACK_SOURCE_GENERATOR "TXZ")
include(CPack)
add_custom_target(dist COMMAND ${CMAKE_MAKE_PROGRAM} package_source)

include(GNUInstallDirs)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/package.spec.in ${PROJECT_BINARY_DIR}/package.spec @ONLY)
add_custom_target(srpm COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/rpmbuild-wrapper.sh" "-w" "${PROJECT_BINARY_DIR}" "-S" "${PROJECT_BINARY_DIR}/${CPACK_SOURCE_PACKAGE_FILE_NAME}.tar.xz" "${PROJECT_BINARY_DIR}/package.spec")
add_dependencies(srpm dist)
