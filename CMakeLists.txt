CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
PROJECT(Noise)

SET(SOURCES
	cellular.c
	noise1234.c
	sdnoise1234.c
	simplexnoise1234.c
	srdnoise23.c
)

SET(HEADERS
	cellular.h
	noise1234.h
	sdnoise1234.h
	simplexnoise1234.h
	srdnoise23.h
)

IF(MSVC)
	# MSVC has C89 only, compile as C++
	SET_SOURCE_FILES_PROPERTIES(${SOURCES} PROPERTIES LANGUAGE CXX )
	ADD_DEFINITIONS(/wd4244)
	ADD_DEFINITIONS(-D_CRT_SECURE_NO_WARNINGS)
ENDIF(MSVC)

ADD_LIBRARY(noise STATIC ${SOURCES} ${HEADERS})