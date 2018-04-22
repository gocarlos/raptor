# raptor/utils/CMakeLists.txt
#
# Original listfile by Daniel Richard G. <skunk@iSKUNK.ORG>
# This file is in the public domain.
#

INCLUDE_DIRECTORIES(BEFORE
	${CMAKE_SOURCE_DIR}/src
	${CMAKE_BINARY_DIR}/src
	${CMAKE_CURRENT_SOURCE_DIR}
)

IF(NOT HAVE_GETOPT AND NOT HAVE_GETOPT_LONG)
	SET(getopt_sources ${CMAKE_CURRENT_LIST_DIR}/getopt.c ${CMAKE_CURRENT_LIST_DIR}/raptor_getopt.h)
ENDIF(NOT HAVE_GETOPT AND NOT HAVE_GETOPT_LONG)

ADD_EXECUTABLE(rapper ${CMAKE_CURRENT_LIST_DIR}/rapper.c ${getopt_sources})
TARGET_LINK_LIBRARIES(rapper raptor2)
target_include_directories(rapper PRIVATE ${CMAKE_CURRENT_BINARY_DIR}/../src)

ADD_EXECUTABLE(rdfdiff ${CMAKE_CURRENT_LIST_DIR}/rdfdiff.c ${getopt_sources})
TARGET_LINK_LIBRARIES(rdfdiff raptor2)

INSTALL(FILES   rapper.1 DESTINATION ${CMAKE_INSTALL_MANDIR}/man1)
INSTALL(TARGETS rapper   DESTINATION ${CMAKE_INSTALL_BINDIR})

# end raptor/utils/CMakeLists.txt
