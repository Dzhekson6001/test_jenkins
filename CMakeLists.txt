cmake_minimum_required(VERSION 2.8)

SET(CMAKE_INSTALL_PREFIX ${CMAKE_SOURCE_DIR}/bin/${CMAKE_SYSTEM})
SET(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/Modules" ${CMAKE_MODULE_PATH})

SET( BIN MainProject )
SET( PROJECT_ROOT "${CMAKE_SOURCE_DIR}/" )

IF(UNIX AND NOT APPLE)
    SET(LINUX ON)
ENDIF(UNIX AND NOT APPLE)

IF(WIN32)
	MESSAGE(SEND_ERROR "WINDOWS is unsupported yet ;)")
ENDIF(WIN32)

#--------------------------------------------------------------------
# Set source files.
#--------------------------------------------------------------------
AUX_SOURCE_DIRECTORY( ${PROJECT_ROOT} URL_CLASSES )

SET(PROJECT_SOURCES
    ${URL_CLASSES}
)


#--------------------------------------------------------------------
# Compile
#--------------------------------------------------------------------
SET (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -o0 -g3 -std=c++11")

INCLUDE_DIRECTORIES(
    ${PROJECT_ROOT}
)


ADD_EXECUTABLE( ${BIN} ${PROJECT_SOURCES} )
