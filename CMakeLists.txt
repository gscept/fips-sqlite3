#-------------------------------------------------------------------------------
# Sqlite3
#-------------------------------------------------------------------------------
cmake_minimum_required(VERSION 3.21)

if (NOT FIPS_IMPORT)
# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")
	project(fips-sqlite3)
	fips_setup()
endif()	

	fips_begin_lib(sqlite3)
	
IF(FIPS_LINUX)
	target_compile_options(sqlite3 PRIVATE "-fno-fast-math")
	ENDIF()

	IF(FIPS_LINUX)
		fips_deps(dl)
	ENDIF()

target_include_directories(sqlite3 PRIVATE .)
	fips_src(. GROUP "sqlite3" NO_RECURSE)
	fips_end_lib()
