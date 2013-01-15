Git Extras
==========

Git is amazing. Specifically, its ability to be extended is amazing. Essentially any "git <command>" can be made by naming a file "git-<command>" and placing it in your git-core folder. For example, once the "git-stash-list" file is in your git-core folder you can access it via "git stash-list". This repository is a set of extras that are intended to make Git more expressive.

Installation
------------

1. Find your git-core folder:

$ find /usr -name "git-core"

On OS X 10.6 using the MacPorts version of Git I found the directory at /opt/local/libexec/git-core. On OS X 10.8 I found it at /usr/libexec/git-core.

2. Copy the files to your git-core folder:

$ sudo cp git-* /usr/libexec/git-core/

3. Make those files executable:

$ sudo chmod 755 /usr/libexec/git-core/git-*

Thanks to Tim Cunningham for his post on how to "Create your own custom git command!":

http://cfmumbojumbo.com/cf/index.cfm/coding/create-your-own-custom-git-command/

Contributing
------------

Please send any pull requests on GitHub to http://github.com/josephdpurcell/git-extras/.
