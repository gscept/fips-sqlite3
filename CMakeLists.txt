#-------------------------------------------------------------------------------
# Sqlite3
#-------------------------------------------------------------------------------
cmake_minimum_required(VERSION 3.0)

# include the fips main cmake file
get_filename_component(FIPS_ROOT_DIR "../fips" ABSOLUTE)
include("${FIPS_ROOT_DIR}/cmake/fips.cmake")

fips_setup()
    fips_project(fips-sqlite3)
	fips_begin_lib(sqlite3)
	
	IF(FIPS_GCC)
		add_compile_options("-fno-fast-math")
	ENDIF()

	IF(FIPS_LINUX)
		fips_deps(dl)
	ENDIF()

	fips_include_directories(.)
	fips_src(. GROUP "sqlite3" NO_RECURSE)
	fips_end_lib()
fips_finish()
