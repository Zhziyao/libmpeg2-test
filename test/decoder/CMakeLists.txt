SET (CMAKE_C_FLAGS " -DPROFILE_ENABLE -DMD5_DISABLE -DARM -fPIC ")

SET (libmpeg2dec_top_srcdir ../..)

SET (mpeg2test_src_files
	main.c
)

INCLUDE_DIRECTORIES(
	${libmpeg2dec_top_srcdir}/decoder
	${libmpeg2dec_top_srcdir}/common
)

LINK_DIRECTORIES (
	${libmpeg2dec_top_srcdir}/lib
)

ADD_DEFINITIONS (${CMAKE_C_FLAGS})

ADD_EXECUTABLE (mpeg2test ${mpeg2test_src_files})

TARGET_LINK_LIBRARIES (mpeg2test mpeg2dec pthread)

SET (EXECUTABLE_OUTPUT_PATH ${libmpeg2dec_top_srcdir})