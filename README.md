# AUTOVALA #

## WHAT IS IT? ##

Autovala is a program and a library designed to help in the creation of
projects with Vala and CMake.

The idea is quite simple: CMake is very powerful, but writting the CMakeLists
files is boring and repetitive. Why not let the computer create them, by
guessing what to do with each file? And if, at the end, there are mistakes,
let the user fix them in an easy way, and generate the final CMakeLists files.

This is what Autovala does. This process is done in three steps:

  * First, Autovala checks all the folders and files, and writes a project
    file with the type of each file
  * It also peeks the source files to determine which Vala packages they need,
    and generate automagically that list
  * After that (and after allowing the user to check, if (s)he wishes, the
    project file), it uses that project file to generate the needed CMakeLists
    files


## USING AUTOVALA ##


The DOC folder contains the Wiki dumped in HTML format. Just open the
**index.html** file with your browser, or go to the **Wiki section** in GitHub,
and enjoy.


## History of versions ##

* version 0.25.0 (2013-11-16)
    * Added support for creating and installing man pages
    * Added manpages for Autovala
* version 0.24.0 (2013-10-20)
	* Added conditional compilation and conditional installation support
* version 0.23.0 (2013-10-14)
	* Added bash_completion support
* version 0.22.0 (2013-10-14)
	* Autovala and gedit plugin are now different projects, allowing to compile only the former
	* Now supports several namespaces in the same .vapi file
* version 0.21.0 (2013-09-14)
    * Allows to specify GIO, GIO-unix, GObject and GModule packages for compilation
* version 0.20.0 (2013-05-19)
    * When initializating a new project, it will copy the needed CMAKE scripts for Vala and create an empty source file
    * Now the CUSTOM command accepts both files and folders
    * Now only adds CUSTOM_VAPIS_LIST command when there are a custom VAPI list
    * Now forbides to set files in the main directory (all files/folders must be inside a folder in the main directory). This is a must to avoid failures.
* version 0.19.0 (2013-04-30)
    * Now the plugin deletes the content of the *install* folder, but not the folder itself
* version 0.18.0 (2013-04-30)
    * Allows to delete the INSTALL folder from Gedit
    * Allows to delete the INSTALL folder, update the .avprj file, run cmake and launch make in a single step from Gedit
* version 0.17.0 (2013-04-28)
    * Fixed bug in plugin when updating the whole project
* version 0.16.0 (2013-04-28)
    * Added plugin for Gedit
* version 0.15.0 (2013-04-26)
    * Allows to specify manually the destination directory for binaries and libraries (useful for plugins)
    * Allows to install files in a manually specified destination directory
    * Autodetects autorun *.desktop* files and install them in the right place
* version 0.14.0 (2013-04-21)
    * Now the autovala library can use its own translated messages instead the ones from the main app (useful when embedding autovala in other programs)
* version 0.13.0 (2013-04-11)
    * In libraries, includes the *librarynamespaceConstant* namespace to allow to get access to build data without clash (only when the library has a namespace)
    * Added *clear* command, to remove the automatic parts in the *.avprj* file
* version 0.12.0 (2013-04-09)
    * When checking VAPI files, now will give priority to the version number inside it (gir_version), and only when there is no such number will use the one in the filename
* version 0.11.0 (2013-04-07)
    * Includes the *Constant* namespace in the executables (but not in libraries to avoid clash)
    * Enabled gettext to allow to translate the messages in Autovala
    * Translation to spanish
    * Fixed messages
    * Fixed a bug in Constants that prevented defining the VERSION field
    * New format for the version string inside source code, that allows to set it in libraries without clash
* version 0.10.0 (2013-04-07)
    * Allows to link an executable with a library from the same project
    * Now Autovala itself is a shared library, and the command line binary uses it
    * Fixed several bugs in the .pc generation
    * Fixed the installation paths for include files
* version 0.9.0 (2013-04-06)
    * Fixed a bug in the .pc generation
* version 0.8.0 (2013-04-06)
    * Automatically generates the .pc file for libraries
    * Fixed a bug with CMake when creating more than one binary and/or library
* version 0.7.0 (2013-04-05)
    * Now honors the IGNORE command with VAPI files and source folders
* version 0.6.0 (2013-04-05)
    * Added support for CUSTOM VAPI files
    * Installs Valadoc file sin a better place
    * Added instructions in HTML format, extracted from GitHub's wiki
* version 0.5.0 (2013-04-01)
    * Adds all source files at SRC and their subdirectories
* version 0.4.0 (2013-03-31)
    * Fixed a bug when PKG_CONFIG_PATH is empty
* version 0.3.0 (2013-03-30)
    * Added support for source files that are not in the same folder than the binary they belong to
    * Added documentation about DOC command
    * Valadoc support
* version 0.2.0 (2013-03-30)
    * Now recognizes the DOC folder
    * Now also search libraries in PKG_CONFIG_PATH
* version 0.1.0 (2013-03-29)
    * First public version


## CONTACTING THE AUTHOR ##

Sergio Costas Rodriguez
(Raster Software Vigo)

raster@rastersoft.com

http://www.rastersoft.com

GIT: git://github.com/rastersoft/autovala.git
