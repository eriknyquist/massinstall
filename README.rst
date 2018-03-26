massinstall
===========

This bash script simply reads file paths and modes from a text file,
and calls the UNIX "install" program for each one. I created it for use in
projects where multiple configuration files need to be copied from the source
tree onto the system as part of the installation process.

This script just saves me a bit of time in automating the process, if there are
a large number of files that need to be copied. Nothing fancy.


Installation
============

::

    install -m 777 massinstall /usr/bin/massinstall

Usage
=====

Pass in a configuration file when running ``massinstall``:

::

    massinstall files_to_install.conf

The configuration file should contain newline-seperated entries, where each
line looks like this:

::

    /src/path /dest/path [mode]

* ``/src/path``: path to the source file
* ``/dest/path``: the destination path
* ``mode``: optional file mode. If not specified, the file mode will be set to
  666 (read and write for all users).

Empty lines and lines beginnning with a '#' are ignored

Example configuration file
--------------------------

::

    file1.txt /etc/file1.txt
    file2 /bin/file2 777
