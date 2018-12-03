cmake_minimum_required(VERSION 2.6)

project(uuid)

add_subdirectory(src)

set(LIB_INSTALL_DIR lib CACHE STRING "Install location of libraries")
set(BIN_INSTALL_DIR bin CACHE STRING "Install location of executables")

 # Produce a pkg-config file
configure_file("uuid.pc.in" "uuid.pc" @ONLY)
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/uuid.pc"
            DESTINATION "${LIB_INSTALL_DIR}/pkgconfig")
