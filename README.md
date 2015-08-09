08.08.2015 — 07:44:09 PM -0700  
Scott Haneda [@scotthaneda](https://twitter.com/scotthaneda)

#lcaser

##Given a file path, will convert all file and directories lowercase; recursively.
A script to change all files and directories at a given path to lowercase.
Many OS's are able to handle this as a one liner using a regex – for example:

    for f in *; do mv $f `echo $f | tr '[:upper:]' '[:lower:]'`; done

On Mac OS X, that will not work, and other OS's may also share issues.  The correct usage of hard and soft quote marks may help, though hidden dot files and the method
in which Mac OS X tries to push a file/directory into itself, caused
problems for me.  This is my attempt at fixing it.

##A history lesson and a warning…
In OS X and OS 9, which is where I first discovered it, you could perform something alone the lines of:

	cp directory/images directory/images
	
Essentially copying a directory onto itself.  At this point, the `cp` command should bail, but it doesn't.  And I have found apps that allow it, and apps that don't.  For example, on OS 9 there is no shell/terminal, so it is hard to perform something like this. The UI and what it allows you to do restrict this from happening.

Shove a http server on OS 9 and a scripting language, and you get your OS exposed to be able to issue such a command.  The scripting language should protect you from this.  When the OS does not, it gets a lot lower level, more close to the drive, the kernel, the CPU, etc.  You end up corrupting the Master Boot Record, and causing all kinds of problems to the computer.  I have so far been able to recover from it with Disk Repair tools like Norton Utilities on OS 9.

Norton Utilities is actually a good app up to a few version prior to the last releases on OS 9.  After that, it is a junk app and no need given how OS X works.  Yet they still sell it to all those switchers who have it engrained in themselves that they need A/V.  Then again, I got malware installed on my personal laptop.  This means I had to admin password to get it to work.  Unless it was a Chrome extension in the browser, in which case, I need to track down how all this happened and report it.  I'm not sure I have it entirely cleaned up.  This was a more sophisticated malware, using launchd to run items on a schedule, hiding real binary apps compiled for OS X.  No obfuscation on the code, so I just need to look at it and see.

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