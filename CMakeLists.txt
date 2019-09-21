cmake_minimum_required(VERSION 3.11)

project(jpeg-6b C)

set(JPEG-6B_SOURCES
    jcapimin.c
    jcapistd.c
    jccoefct.c
    jccolor.c
    jcdctmgr.c
    jchuff.c
    jcinit.c
    jcmainct.c
    jcmarker.c
    jcmaster.c
    jcomapi.c
    jcparam.c
    jcphuff.c
    jcprepct.c
    jcsample.c
    jctrans.c
    jdapimin.c
    jdapistd.c
    jdatadst.c
    jdatasrc.c
    jdcoefct.c
    jdcolor.c
    jddctmgr.c
    jdhuff.c
    jdinput.c
    jdmainct.c
    jdmarker.c
    jdmaster.c
    jdmerge.c
    jdphuff.c
    jdpostct.c
    jdsample.c
    jdtrans.c
    jerror.c
    jfdctflt.c
    jfdctfst.c
    jfdctint.c
    jidctflt.c
    jidctfst.c
    jidctint.c
    jidctred.c
    jmemmgr.c
    jmemnobs.c
    jquant1.c
    jquant2.c
    jutils.c
    )
if (${CMAKE_C_COMPILER_ID} STREQUAL MSVC)
	set(JPEG-6B_SOURCES ${JPEG-6B_SOURCES} jpeg-6b/jpeg-6b.def)
endif()

add_library(jpeg-6b MODULE ${JPEG-6B_SOURCES})

if (${CMAKE_C_COMPILER_ID} STREQUAL MSVC)
	configure_file(jconfig.vc jconfig.h)
else()
	message(FATAL_ERROR "Unknown compiler ${CMAKE_C_COMPILER_ID}")
endif()
target_include_directories(jpeg-6b PUBLIC $<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}>)

get_target_property(JPEG-6B_OUTPUT_DIRECTORY jpeg-6b LIBRARY_OUTPUT_DIRECTORY)
message(STATUS "jpeg-6b: LIBRARY_OUTPUT_DIRECTORY = ${JPEG-6B_OUTPUT_DIRECTORY}")
