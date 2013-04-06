# Rules

The rules followed by Autovala are the following:

* All .vala files in the src/ folder belong to a binary called like the project name, and will be scanned to determine the packages needed to compile them. The .vala files in the subfolders are also added, unless there is another binary or library that already posesses that folder

* All .vala files in a folder posessed by a binary or library belong to it, and will be scanned to determine the packages needed to compile them. The .vala files in the subfolders are also added, unless there is another binary or library that already posesses that folder

* The sources will be scanned to find the version number in a specific format, allowing to keep it inside the sources and avoiding the need of editing the project file manually

* All .png or .svg in the folder data/icons/ (and subfolders) are considered icons, so Autovala will determine automatically the best-fitting standard icon size (in the case of .png; for .svg it will put them always in 'scalable') and install them in the corresponding folder: 'apps' by default, unless it's an .svg file with a filename ended in -symbolic.svg; in that case it will go to 'status'. The user can modify the final folder manually for the icons (s)he wishes.

* All .png, .jpg or .svg files in the folder data/pixmaps/ (and subfolders) are considered pixmaps, and will be installed in share/pixmaps/.

* All .po files in po/ folder will be considered as po files, and will be installed in the right locale. Also, will find the .vala and .ui files and add them as sources for internationalization process.

* Each .desktop file in data/ will be copied to share/desktop/

* Each .service file in data/ will be presumed to be a D-Bus service, and will be preprocessed to put the right binary folder ( bin/ or local/bin/ )

* Each .plug file in data/ will be presumed to be an ElementaryOS PLUG file

* Each .gschema.xml file in data/ will be presumed to be a GTK schema, so will be copied in the right place and force a recompile of the schemas (if needed)

* Each .ui file in data/interface/ will be presumed to be a Glade file, so will be copied to share/project_name/ and taken into account when generating the .po and .mo files for internationalization

* Each .sh file in data/ will be presumed to be a binary script, so will be copied to bin/

* All files and folders in data/local/ will be copied to share/project_name/ This is useful for application-specific data

* All files and folders in doc/ will be copied to share/doc/project_name/ This is useful for documentation

When Autovala searchs the packages, it uses only the versions available for the currently active version. Also, by default, it uses the most recent version. But if another version is selected manually, it will use that one instead.

**Example:** if you put "using Gtk;" in your code, by default Autovala will use the package gtk+-3.0 to compile it; but if you manually add the package gtk+-2.0 to that binary, Autovala will use Gtk2 instead of Gtk3.