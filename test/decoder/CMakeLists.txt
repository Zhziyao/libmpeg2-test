PROJECT(libmpeg2dec)

SET (CMAKE_C_FLAGS " -DPROFILE_ENABLE -DMD5_DISABLE -DARM -fPIC ")

SET (mpeg2dec_top_srcdir ../..)

SET (libmpeg2decode_src_files
	main.c
)

INCLUDE_DIRECTORIES(
	${mpeg2dec_top_srcdir}/decoder
	${mpeg2dec_top_srcdir}/common
)

LINK_DIRECTORIES (
	${mpeg2dec_top_srcdir}/lib
)

ADD_DEFINITIONS (${CMAKE_C_FLAGS})

ADD_EXECUTABLE (mpeg2decode ${libmpeg2decode_src_files})

TARGET_LINK_LIBRARIES (mpeg2decode mpeg2dec pthread)

SET (EXECUTABLE_OUTPUT_PATH ${mpeg2dec_top_srcdir})