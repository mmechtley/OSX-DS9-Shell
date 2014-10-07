OSX-DS9-Shell
=============

Command-line interface for SAOImage DS9 native (.app) OSX build

Version 7.3 of SAOImage DS9 marks the return of a native (.app) build for Mac OSX. However, there is no simple way to call it from the command line in the same manner as the X11 version (as required by pyds9, for example). Calling the binary within the .app directly fails to find the associated resource files, and using the OSX **open** command provides no simple way to pass complex argument strings, such as the following, since **open** does not know about the current working directory.

    ds9 file1.fits -regions file1.reg -cmap heat file2.fits -regions file2.reg -cmap cool

This bash script is intended as a drop-in replacement for the shell-run binary (**ds9**, normally installed in /usr/local/bin) that allows the user to specify all the normal command-line options. It does this by inferring which arguments refer to files, converting them to absolute paths, and then calling SAOImage DS9.app via **open** with the specified arguments as a --args string.

Installation
------------
Copy the **ds9** bash script to any directory in your **PATH** environment variable, and chmod +x.
