set(SRC
    clear.c
    compare.c
    copy.c
    gen_uuid.c
    isnull.c
    pack.c
    parse.c
    unpack.c
    unparse.c
    uuid_time.c
)

add_definitions(
    -DHAVE_INTTYPES_H
    -DHAVE_UNISTD_H
    -DHAVE_ERRNO_H
    -DHAVE_NETINET_IN_H
    -DHAVE_SYS_IOCTL_H
    -DHAVE_SYS_MMAN_H
    -DHAVE_SYS_MOUNT_H
    -DHAVE_SYS_PRCTL_H
    -DHAVE_SYS_RESOURCE_H
    -DHAVE_SYS_SELECT_H
    -DHAVE_SYS_STAT_H
    -DHAVE_SYS_TYPES_H
    -DHAVE_STDLIB_H
    -DHAVE_STRDUP
    -DHAVE_MMAP
    -DHAVE_UTIME_H
    -DHAVE_GETPAGESIZE
    -DHAVE_LSEEK64
    -DHAVE_LSEEK64_PROTOTYPE
    -DHAVE_EXT2_IOCTLS
    -DHAVE_LINUX_FD_H
    -DHAVE_TYPE_SSIZE_T
    -DHAVE_SYS_TIME_H
    -DHAVE_SYS_PARAM_H
    -DHAVE_SYSCONF
)

add_library(uuid STATIC ${SRC})

install(TARGETS uuid
    RUNTIME DESTINATION lib
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
    )
install(FILES uuid.h uuidd.h uuidP.h
    DESTINATION include/uuid
    )
 # Produce a pkg-config file
configure_file("${CMAKE_CURRENT_SOURCE_DIR}/../uuid.pc.in" "${CMAKE_CURRENT_SOURCE_DIR}/../uuid.pc" @ONLY)
install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/../uuid.pc"
            DESTINATION "lib/pkgconfig")
