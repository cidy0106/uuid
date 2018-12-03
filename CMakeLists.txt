cmake_minimum_required(VERSION 2.6)

project(uuid)

add_subdirectory(src)

 # Produce a pkg-config file
configure_file("uuid.pc.in" "uuid.pc" @ONLY)
install(FILES "${CMAKE_CURRENT_BINARY_DIR}/uuid.pc"
            DESTINATION "${CMAKE_INSTALL_PREFIX}/pkgconfig")
