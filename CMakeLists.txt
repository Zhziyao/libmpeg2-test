cmake_minimum_required (VERSION 2.8.4)

PROJECT(libmpeg2dec)

FILE (MAKE_DIRECTORY lib bin)

ADD_SUBDIRECTORY (decoder)

ADD_SUBDIRECTORY (test/decoder)