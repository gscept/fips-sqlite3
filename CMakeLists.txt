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
	
	IF(CMAKE_COMPILER_IS_GNUCC)
		add_compile_options("-fno-fast-math")
	ENDIF()

	IF(UNIX)
		SET(CMAKE_MODULE_LINKER_FLAGS "-ldl")
	ENDIF()

	fips_include_directories(.)
	fips_src(. GROUP "sqlite3" NO_RECURSE)
	fips_end_lib()
fips_finish()
