project('libmemory',
	'c',
	default_options : ['c_std=c11'])

########################
# Identify Compiler(s) #
########################

native_compiler_id = meson.get_compiler('c', native : true).get_id()

if meson.is_cross_build()
	host_compiler_id = meson.get_compiler('c', native : false).get_id()
endif

######################################
# Import compiler flags and warnings #
######################################

# Get compiler flags, and handle host vs cross builds
if meson.is_cross_build()
	if host_compiler_id == 'clang'
		subdir('build/compiler/clang')
	elif host_compiler_id == 'gcc'
		subdir('build/compiler/gcc')
	endif
else
	if native_compiler_id == 'clang'
		subdir('build/compiler/clang')
	elif native_compiler_id == 'gcc'
		subdir('build/compiler/gcc')
	endif
endif

# compiler_args is defined in build/compiler/<target>/meson.build
# We are the standard library, don't complain about __
add_global_arguments([compiler_args], language: 'c')

subdir('build/ea-stdlib')

#########################
# Process Build Options #
#########################

if get_option('enable-werror') == true
	add_global_arguments('-Werror', language : 'c')
endif

if get_option('enable-pedantic-error') == true
	add_global_arguments('-pedantic-error', language : 'c')
endif

#######################
# Process source tree #
#######################

libmemory_includes = include_directories('include', 'dependencies/lib')

# Library build definition
subdir('src/')

# Test build definition
subdir('test/')