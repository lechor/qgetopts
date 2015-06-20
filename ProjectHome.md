Designed to be a generic, cross-platform library that can parse  command-line formats as generally as possible (similar to getopts on Linux, but easier to use & object-oriented).

The supported format is GNU
Command-line options are position independent but emitted in the same relative position (i.e. "-a -b foo -d -c boo" gets emmited as "-a", "-b", "-d", "-c", "foo", "boo" assuming none of the options accepted arguments).

Both long (multi-character options preceded by "--") and short mode (options preceded by "-" and 1 character long) are supported.

Command-line option arguments (arguments that are specific to long/short option) can be optional, any number from 1 to 2^31 - 1, or variable.  Arguments however must be given as a single command-line parameter (in the case of short options, the can be merged along with the short option as shown below).  The API takes care of splitting up the arguments for you.

Short option arguments can be given as "-aarg1,,arg3" (arg1, empty string, arg3 as arguments) or "-aarg1 arg2 arg3", or "-a" "arg1,arg2,arg3".  Separators for multi-argument options can be whatever you specify.

All remaining command-line parameters that are not options, or arguments to options, are retrieved separately and maintain their relative order (i.e. take the original parameters and remove all options & option arguments).

Optionally, it can serialize a pretty & complete help menu (and handle the help command line arguments for you) into a string or some kind of output stream.

The library is Qt based, but currently does expose a primitive standard C++ interface.  QtCore headers are needed for compilation, but not the Qt libraries (assuming it is statically linked).

Eventually this will be split into two libraries - CPPGetOpts which has all the logic in a cross-platform C++ library (with no external dependancies) and QGetOpts which will be the Qt wrapper interface.