# libmemory test build definition

libmemory_freelist_test_files = [
	'main.c',
	'support/memory.c',
	'src/aligned_malloc.c',
	'src/malloc_freelist.c'
]

libmemory_freelist_tests = executable('libmemory_freelist_test',
	libmemory_freelist_test_files,
	c_args: [stdlib_compiler_flags, '-Wno-vla', '-Wno-unused-parameter'],
	link_args: [stdlib_link_flags, '-lcmocka', '-lc'],
include_directories: [libmemory_includes],
	link_with: libmemory_freelist,
	native: true
)