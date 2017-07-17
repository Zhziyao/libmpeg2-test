PROJECT(libmpeg2dec)

SET (CMAKE_C_FLAGS " -D_LIB -DMULTICORE -fPIC -O3 -DANDROID -Werror -DX86 -DDISABLE_AVX2 -msse4.2 -mno-avx -DDEFAULT_ARCH=D_ARCH_X86_SSE42 ") 

SET (libmpeg2dec_top_srcdir ..)

SET (mpeg2dec_src_files
	../common/impeg2_buf_mgr.c
	../common/impeg2_disp_mgr.c
	../common/impeg2_format_conv.c
	../common/impeg2_globals.c
	../common/impeg2_idct.c
	../common/impeg2_inter_pred.c
	../common/impeg2_job_queue.c
	../common/impeg2_mem_func.c
	../common/ithread.c
	../common/icv_sad.c
	../common/icv_variance.c
	../common/ideint.c
	../common/ideint_cac.c
	../common/ideint_debug.c
	../common/ideint_function_selector_generic.c
	../common/ideint_utils.c
	impeg2d_api_main.c
	impeg2d_bitstream.c
	impeg2d_debug.c
	impeg2d_dec_hdr.c
	impeg2d_decoder.c
	impeg2d_d_pic.c
	impeg2d_function_selector_generic.c
	impeg2d_globals.c
	impeg2d_i_pic.c
	impeg2d_mc.c
	impeg2d_mv_dec.c
	impeg2d_pic_proc.c
	impeg2d_pnb_pic.c
	impeg2d_vld.c
	impeg2d_vld_tables.c
	impeg2d_deinterlace.c

	x86/impeg2d_function_selector.c
	x86/impeg2d_function_selector_avx2.c
	x86/impeg2d_function_selector_ssse3.c
	x86/impeg2d_function_selector_sse42.c
	../common/x86/ideint_function_selector.c
	../common/x86/ideint_function_selector_ssse3.c
	../common/x86/ideint_function_selector_sse42.c
	../common/x86/icv_variance_ssse3.c
	../common/x86/icv_sad_ssse3.c
	../common/x86/ideint_cac_ssse3.c
	../common/x86/ideint_spatial_filter_ssse3.c
	../common/x86/impeg2_idct_recon_sse42_intr.c
	../common/x86/impeg2_inter_pred_sse42_intr.c
	../common/x86/impeg2_mem_func_sse42_intr.c
)

INCLUDE_DIRECTORIES(
	${libmpeg2dec_top_srcdir}/decoder
	${libmpeg2dec_top_srcdir}/common
	${libmpeg2dec_top_srcdir}/common/x86
)

ADD_DEFINITIONS (${CMAKE_C_FLAGS})

ADD_LIBRARY (mpeg2dec STATIC ${mpeg2dec_src_files})

SET(LIBRARY_OUTPUT_PATH ${libmpeg2dec_top_srcdir}/lib)