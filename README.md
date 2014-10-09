OSX-DS9-Shell
=============

Command-line interface for SAOImage DS9 native (.app) OSX build

Version 7.3 of SAOImage DS9 marks the return of a native (.app) build for Mac OSX. However, there is no simple way to call it from the command line in the same manner as the X11 version (as below, and as required by pyds9, for example).

    ds9 file1.fits -regions file1.reg -cmap heat file2.fits -regions file2.reg -cmap cool

Symlinking the binary within the .app directly fails to find the associated resource files, and using the OSX **open** command provides no simple way to pass complex argument strings (beyond just file names), since **open** does not know about the current working directory. Aliasing may only work from login shells.

This bash script is intended as a drop-in replacement for the shell-run binary (**ds9**, normally installed in /usr/local/bin) that allows the user to specify all the normal command-line options.

Installation
------------
Copy the **ds9** bash script to any directory in your **PATH** environment variable, and chmod +x.

Issues
------
Some folks get the following warning message when starting DS9. 

    XPA unable to verify hostname, setting XPA_METHOD to LOCAL
This seems to happen more commonly to OSX users and probably involves the (I'm sure extremely fool-proof, sophisticated) method XPA uses to determine whether the computer can be reached over the network. It is harmless to almost all users because very few people use XPA to manipulate DS9 sessions over a network (local connections, e.g. from IRAF, will still work). See [this comment](https://github.com/mmechtley/OSX-DS9-Shell/pull/1#issuecomment-58487979) for a more detailed discussion and a list of workarounds that supress the warning (but don't fix the problem).
