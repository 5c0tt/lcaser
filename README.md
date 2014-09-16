Last Modified 09/15/14 — 08:27:50 PM • Scott Haneda • [@cometbus](https://twitter.com/cometbus)

#`lcaser`

##Given a file path, will convert all file and directories lowercase
Script to change all files and directories at a given path to lowercase.
Many OS's are able to handle this as a one liner – for example:

    for f in *; do mv $f `echo $f | tr '[:upper:]' '[:lower:]'`; done

At least on Mac OS X, that will not work.  The correct usage of hard
and soft quote marks may help, though hidden dot files and the method
in which Mac OS X tries to push a file/directory into itself, caused
problems for me.  This is my attempt at fixing it.

##Trying to be more POSIX compliant, but I could never get these to work, see the issues if you want to take a stab at fixing these so they can be uncommented at the top of the file.
    #!/bin/bash
    # set -o nounset  # Referencing undefined variables (which default to "")
    # set -o errexit  # Ignoring failing commands
    # 05/29/14 — 11:38:02 AM Added above commands and changed to sh instead of
    # bash to be more POSIX'y


## Known Issues

#TODO — There are issues, the top arg dir is not altered, and I am only
#Getting one level deep on lowercasing.

Please feel free to offer suggestions, or pull the whole file and make fixes.  Supporting multiple files would be nice.  Right now, it takes drag and drop, and also has a Automator call that will show a notification center alert of what is going on.