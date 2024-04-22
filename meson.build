# SPDX-License-Identifier: CC0-1.0

project('yavta', 'c',
    meson_version : '>= 0.40',
    version : '0.0.0',
    default_options : [
        'werror=true',
        'warning_level=2',
    ],
    license : 'GPL 2.0+')

#
# Configure the build environment
#
cc = meson.get_compiler('c')

cc_arguments = [
    '-Wshadow',
]

if cc.get_id() == 'clang'
    # Turn _FORTIFY_SOURCE by default on optimised builds (as it requires -O1
    # or higher). This is needed on clang only as gcc enables it by default.
    if get_option('optimization') != '0'
        cc_arguments += [
            '-D_FORTIFY_SOURCE=2',
        ]
    endif
endif

add_project_arguments(cc_arguments, language : 'c')

#
# yavta
#
yavta_dependencies = []

if not cc.has_function('clock_gettime')
    # On glibc older than 2.17, clock_gettime is provided by time.h and -lrt
    yavta_dependencies += [cc.find_library('rt')]
endif

yavta_sources = files([
    'yavta.c',
])

yavta  = executable('yavta', yavta_sources,
                    include_directories : include_directories('include'),
                    dependencies : yavta_dependencies,
		    link_args: ['-static','-static-libgcc'],
                    install : true)
