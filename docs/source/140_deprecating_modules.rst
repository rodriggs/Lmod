Deprecating Modules
===================

There may come a time when your site might want to mark a module for
deprecation.  If you track module usage, you can find the modules
that are rarely used, and you can find out which users are using the
modules. Once you have decided which modules are marked for removal,
you can make a message be printed when the module is loaded.

Suppose you want to mark a module for later removal.  You can setup a
message that is reported to the user *Every time the module is
loaded*.

For example::

    $ module load abc/1.2.3

    abc/1.2.3:
        This module is deprecated and will be removed from the system
        on June 19.   Please load abc/2.3.4 instead.


Note that this message is just text and in no way controls user access
to the module.  Your site will have to remove the module.  This nag
message is a way to let your users know that removal will happen ahead
of time.

Also note that a user only gets this message when loading the module.
There is no special marking in ``module avail`` or ``module spider``.




You can create a file called "admin.list" and place it in
"/path/to/lmod/etc/admin.list".  Note that typically the lmod script
will be in "/path/to/lmod/lmod/libexec/lmod". The etc directory is
independent to the version of Lmod.  You can see the location that
Lmod is looking for by executing::

    $ module --config

Look for "Admin File".  You can also set the "LMOD_ADMIN_FILE" to
point to the admin.list file.

The admin file consists of key-value pairs.  For example::

      moduleName/version:  message
      <blank line>

Or::

     Full_PATH_to_Modulefile: message
     <blank line>

The message can be as many lines as you like.  The message ends with a
blank line.   Below is an example::


      gcc/2.95:    This module is deprecated and will be removed from the system on Jan 1.  1999.
                   Please change you use of this compiler to a newer one.

      boost/1.54.0:
      We are having issues

      /opt/apps/modulefiles/Compiler/gcc/4.7.2/boost/1.55.0:
      We are having issues


Note that you don't include the .lua part when specifying the version
number.


