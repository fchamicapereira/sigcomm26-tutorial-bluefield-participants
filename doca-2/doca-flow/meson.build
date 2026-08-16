# doca_flow_compat.h shims a few DOCA 2.9 API renames (doca_flow_resource_query_entry,
# doca_flow_shared_resource_set_cfg) back onto their pre-2.9 names, so the same sources build
# unchanged against every DOCA release this repo targets. Force-included ahead of every .c file's
# own #include <doca_flow.h>; the header is a no-op on 2.9+ (it is guarded on DOCA_VERSION_*).
flow_c_args = base_c_args + ['-include', meson.current_source_dir() / 'doca_flow_compat.h']

# -Wno-unused-variable: the exercise declares every struct you need and leaves the DOCA calls that
# use them to you, so before you start there are around twenty variables that are declared and never
# read. -Wunused-function is deliberately left ON -- its "defined but not used" lines name exactly
# the functions you have not wired up yet.
executable(DOCA_PREFIX + 'flow_ecn',
	['doca_flow_ecn.c'],
	c_args : flow_c_args + ['-Wno-unused-variable'],
	dependencies : app_dependencies,
	include_directories : app_inc_dirs,
	install: false)
