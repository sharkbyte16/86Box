#
# 86Box    A hypervisor and IBM PC system emulator that specializes in
#          running old operating systems and software designed for IBM
#          PC systems and compatibles from 1981 through fairly recent
#          system designs based on the PCI bus.
#
#          This file is part of the 86Box distribution.
#
#          CMake build script.
#
# Authors: David Hrdlička, <hrdlickadavid@outlook.com>
#
#          Copyright 2020-2021 David Hrdlička.
#          Copyright 2025 starfrost
#

add_library(vid OBJECT
    agpgart.c
    video.c
    vid_table.c
    # CGA 
    vid_cga.c
    vid_cga_comp.c
    vid_cga_compaq.c 
    vid_cga_compaq_plasma.c
    vid_cga_colorplus.c
    vid_cga_ncr.c
    vid_cga_olivetti.c
    vid_cga_toshiba_t1000.c 
    vid_cga_toshiba_t3100e.c 

    # PCJr/Tandy
    vid_pcjr.c
    vid_tandy.c

    vid_mda.c
    vid_hercules.c
    vid_hercules_plus.c
    vid_hercules_incolor.c
    vid_genius.c
    vid_pgc.c
    vid_im1024.c
    vid_sigma.c
    vid_wy700.c
    vid_ega.c
    vid_ega_render.c
    vid_svga.c
    vid_8514a.c
    vid_svga_render.c
    vid_ddc.c
    vid_vga.c
    vid_ati_eeprom.c
    vid_ati18800.c
    vid_ati28800.c
    vid_ati_mach8.c
    vid_ati_mach64.c
    vid_ati68875_ramdac.c
    vid_ati68860_ramdac.c
    vid_bt481_ramdac.c
    vid_bt48x_ramdac.c
    vid_chips_69000.c
    vid_av9194.c
    vid_icd2061.c
    vid_ics2494.c
    vid_ics2595.c
    vid_cl54xx.c
    vid_et3000.c
    vid_et4000.c
    vid_sc1148x_ramdac.c
    vid_sc1502x_ramdac.c
    vid_et4000w32.c
    vid_stg_ramdac.c
    vid_ht216.c
    vid_oak_oti.c
    vid_paradise.c
    vid_rtg310x.c
    vid_f82c425.c
    vid_ti_cf62011.c
    vid_tvga.c vid_tgui9440.c
    vid_tkd8001_ramdac.c
    vid_att20c49x_ramdac.c
    vid_s3.c vid_s3_virge.c
    vid_ibm_rgb528_ramdac.c
    vid_sdac_ramdac.c
    vid_mga.c
    vid_tvp3026_ramdac.c
    vid_att2xc498_ramdac.c
    vid_xga.c
    vid_bochs_vbe.c
    vid_ps55da2.c
    vid_jega.c
    nv/nv_rivatimer.c
)

if(G100)
    target_compile_definitions(vid PRIVATE USE_G100)
endif()

if(XL24)
    target_compile_definitions(vid PRIVATE USE_XL24)
endif()

add_library(voodoo OBJECT
    vid_voodoo.c
    vid_voodoo_banshee.c
    vid_voodoo_banshee_blitter.c
    vid_voodoo_blitter.c
    vid_voodoo_display.c
    vid_voodoo_fb.c
    vid_voodoo_fifo.c
    vid_voodoo_reg.c
    vid_voodoo_render.c
    vid_voodoo_setup.c
    vid_voodoo_texture.c
)

if(NOT MSVC AND (ARCH STREQUAL "i386" OR ARCH STREQUAL "x86_64"))
    target_compile_options(voodoo PRIVATE "-msse2")
endif()
