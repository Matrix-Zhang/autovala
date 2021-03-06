### CMakeLists automatically created with AutoVala
### Do not edit

project (autovala)
cmake_minimum_required (VERSION 2.6)
cmake_policy (VERSION 2.8)
list (APPEND CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake)
enable_testing ()
option(ICON_UPDATE "Update the icon cache after installing" ON)
option(BUILD_VALADOC "Build API documentation if Valadoc is available" OFF)
option(GTK_OLD "GTK_OLD" OFF)
option(DEBUG "DEBUG" OFF)

include(GNUInstallDirs)
if( ( ${CMAKE_INSTALL_PREFIX} MATCHES "^/usr/local" ) )
	# A workaround to ensure that works 'out of the box' in Debian-based systems
	set(CMAKE_INSTALL_LIBDIR lib)
endif()

set(HAVE_VALADOC OFF)
if(BUILD_VALADOC)
	find_package(Valadoc)
	if(VALADOC_FOUND)
		set(HAVE_VALADOC ON)
		include(Valadoc)
	else()
		message("Valadoc not found, will not build documentation")
	endif()
endif()

find_package(PkgConfig)

set(MODULES_TO_CHECK ${MODULES_TO_CHECK} gio-2.0)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} atk)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} cairo)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} gdk-3.0)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} gdk-pixbuf-2.0)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} gee-0.8)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} glib-2.0)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} gobject-2.0)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} gtk+-3.0)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} pango)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} pangocairo)
set(MODULES_TO_CHECK ${MODULES_TO_CHECK} x11)

pkg_check_modules(DEPS REQUIRED ${MODULES_TO_CHECK})

if ( NOT EXISTS "/usr/include/readline/readline.h" )
	message(FATAL_ERROR "Can't find the file /usr/include/readline/readline.h")
endif()

if ( NOT EXISTS "/usr/bin/pandoc" )
	message(FATAL_ERROR "Can't find the file /usr/bin/pandoc")
endif()

if ( NOT EXISTS "/usr/bin/curl" )
	message(FATAL_ERROR "Can't find the file /usr/bin/curl")
endif()

find_program ( WHERE_PANDOC pandoc )
if ( NOT WHERE_PANDOC )
	MESSAGE(FATAL_ERROR "Error! PANDOC is not installed.")
endif()

add_subdirectory(doc)
add_subdirectory(data/debian)
add_subdirectory(po)
add_subdirectory(data/pixmaps)
add_subdirectory(src/autovalaLib)
add_subdirectory(wiki)
add_subdirectory(data/cmake)
add_subdirectory(data/bash_completion)
add_subdirectory(data/interface)
add_subdirectory(src/autovalaPlugin)
add_subdirectory(src)

