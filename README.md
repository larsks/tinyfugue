# TinyFugue

This repository contains a version of TinyFugue that I have modified to compile under modern Linux distributions. Please report any problems with this version of TinyFugue to <https://github.com/larsks/tinyfugure/issues>.

The original project can be found at <http://tinyfugue.sourceforge.net/>.

This repository is based on version 5.0b8.

## License

TinyFugue is Copyright (C) 1993, 1994, 1995, 1996, 1997, 1998, 1999, 2002, 2003, 2004, 2005, 2006-2007 Ken Keys.

TinyFugue is Copyright (C) 2019 Lars Kellogg-Stedman.

PCRE regexp package is Copyright 1997-1999 University of Cambridge.  See src/pcre-2.08/LICENCE for details.

---

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.

---


## INSTALLING TINYFUGUE

TinyFugue can be installed and run on UNIX-like systems, Mac OS X, OS/2,
and Win32.  For instructions, see the README file in the appropriate
directory.  For information on unofficial versions of TF for other
operating systems, see the TF web page at http://tinyfugue.sourceforge.net/.

Note that the .tar.gz and .tar.Z distributions contain LF line delimiters,
intended for UNIX, and the .zip distribution contains CR LF delimiters,
intended for OS/2.  It is possible to convert line delimiters, but it's
easier to just get a distribution that already has the correct delimiters.


### "Make" options

Options are not available on all systems.  To use an option, give it as
an argument to the installation program (e.g., "make clean").

   all		Compile, but do not install (the "install" option should be
        run later to install the files).
   install	Compile (if you haven't already) and install.  The default
        installation locations depend on the operating system.
   clean		Remove object files and other junk from source directory.
   uninstall	Remove tf executable, help files, and library from their
        installed locations.


### Public Installation

Some features of TF can be disabled for secure public installation, by
using one of these /restrict commands in %{TFLIBDIR}/local.tf:

    /restrict SHELL  Prevents all access to shell or external commands.
                     Disables TF builtins "/sh" and "/quote !", and
                     uncompression during /load and /help.

    /restrict FILE   Prevents reading and writing of files.  Disables
                     TF builtins "/load", "/save", "/saveworld", "/log",
                     and "/quote '", and sockmload feature.
                     Implies /restrict shell.

    /restrict WORLD  Prevents the user from defining new worlds and
                     connecting to undefined worlds.  TF builtins
                     /addworld and the "/world <host> <port>" semantics
                     are disabled.  Implies /restrict file.


### Terminal Handling

If the default terminal handling option does not work, tf can be
configured to use vt100 codes or nothing at all.  See the README
file in the subdirectory corresponding to your operating system.


### Compression

If you are short on disk space, you can compress the helpfile and
library files (except stdlib.tf).  Make sure the COMPRESS_SUFFIX
and COMPRESS_READ macros are set correctly; set them in the
%{TFLIBDIR}/local.tf file if needed.  Note that compresion can not
be used if /restrict is used.


### Firewalls

TF can be made to connect through a generic proxy server by setting
the %proxy_host variable at runtime.  See "/help proxy".

Also see the README file in the subdirectory corresponding to your
operating system to see if tf has transparent firewall support on your
system.


### Last Resort

If you have an installation problem or other system-specific problem that is
not described in this README or the README in the subdirectory for your system,
contact the person who supports TF on your system.  If you have a problem that
is not system-related, you may open an issue at
<https://github.com/larsks/tinyfugue>.  Please provide the following
information:

- The version of TF (type "/version" in tf).
- The operating system version (on unix, type "uname -a" in the shell).
- If tf won't compile, send the output of configure and make (in plaintext
    form, please).
- If you have a bug or core, give ALL error messages from tf.
- If you have a bug or core, describe what you did or what happened
    before the problem, and if the problem is repeatable.
- If you have a core file, do NOT send it.
