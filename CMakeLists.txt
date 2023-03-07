cmake_minimum_required(VERSION 3.0)
project(tinycbor LANGUAGES C CXX VERSION 0.6.0)

set(INCLUDE_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cbor.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborinternal_p.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborjson.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/compilersupport_p.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/tinycbor-version.h
    ${CMAKE_CURRENT_SOURCE_DIR}/src/utf8_p.h
)

# ######### SERVER CBOR LIBRARY ##########
set(SERVER_CBOR_SRCS
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborencoder.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborencoder_close_container_checked.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborencoder_float.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborerrorstrings.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborparser.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborparser_dup_string.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborparser_float.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborpretty.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborpretty_stdio.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cbortojson.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/cborvalidation.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/open_memstream.c)
add_library(libtinycbor SHARED ${SERVER_CBOR_SRCS})
add_library(tinycbor STATIC ${SERVER_CBOR_SRCS})

set(CMAKE_INSTALL_CMAKEDIR "${CMAKE_CURRENT_SOURCE_DIR}/install")
install(TARGETS libtinycbor DESTINATION ${CMAKE_INSTALL_CMAKEDIR}/lib)
install(FILES ${INCLUDE_FILES} DESTINATION ${CMAKE_INSTALL_CMAKEDIR}/include)
