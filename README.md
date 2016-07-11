Git Extras

==========

Git is amazing. Specifically, its ability to be extended is amazing. Essentially any "git <command>" can be made by naming a file "git-<command>" and placing it in your git-core folder. For example, once the "git-stash-list" file is in your git-core folder you can access it via "git stash-list". This repository is a set of extras that are intended to make Git more expressive.

Installation
------------

### 1. Find your git-core folder

    $ find /usr -name "git-core"

On OS X 10.6 and 10.8 using the MacPorts version of Git I found the directory at /opt/local/libexec/git-core. On OS X 10.7 I found it at /usr/libexec/git-core.

### 2. Copy the files to your git-core folder

    $ sudo cp git-* /usr/libexec/git-core/

### 3. Make those files executable

    $ sudo chmod 755 /usr/libexec/git-core/git-*

Thanks to Tim Cunningham for his post on how to "Create your own custom git command!":

http://cfmumbojumbo.com/cf/index.cfm/coding/create-your-own-custom-git-command/

Usage
-----

All git commands are just files named "git-<command>". So, for example, you can use the git-stash-list command by running:

    $ git stash-list

Also, for any of these commands you can get help information by adding a "-h" flag:

    $ git stash-list -h

### git-author-log

Shows the git log by order of AuthorDate instead of CommitDate.

    $ git author-log
    commit ba4c9256d4385ff47eef308734f9b6042d32541f
    Author: Person Name <person@me.com>
    Date: Mon, 29 Apr 2013 15:19:15 -0400

     A commit message.

    commit da774f5a0cbb32e4cc402f4493bbb4cbe324e526
    Author: Person Name <person@me.com>
    Date: Mon, 29 Apr 2013 13:13:43 -0400

     A commit message.

### git-branch-list

Lists remote and local branches. Remote tracking branches are in green, remote
branches that are not tracked are in white, and remote tracking branches whose
remote branch does not exist are in red. All local branches are marked green.

NOTE: this script does not discriminate between remotes.

    $ git branch-list
    Remote Branches
    ---------------
    develop
    master
    Local Branches
    --------------
    feature-test

### git-find-core

Finds the git-core directory and prints the path. If the path to git-core has
already been found and it is a valid path, it will print the path. Else, it
will find the git-core directory and set it in global config as core.path.

    $ git find-core
    /usr/libexec/git-core

### git-istage

Interactively stage files for committing.

For each prompt you may enter any of the following:

    y, Y, 1, yes) Stage the file
    n, N 0, no) Skip staging the file
    d, D, diff) Get the diff for the file
    e, E, edit) Edit the file (using $EDITOR)
    x, X, q, Q, exit, quit) Quit

Example:

    $ git istage
    Do you want to stage htdocs/index.php? 

### git-purge

Deletes a branch from both the local and remote origin.

WARNING: this action cannot (easily) be undone!

    $ git purge feature-test
    Deleted branch feature-test (was acb2455).
    To git@mysite.com:www.mistie.com.git
     - [deleted]         feature-test

### git-remote-purge

Prompts to delete all remote tracking branches that have been deleted remotely.

    $ git remote-purge

### git-stash-list

Lists each stash and its diff.

    $ git stash-list
    stash@{0}
     htdocs/index.php                                       |    2 +-
     htdocs/file1.txt                                       |  112 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++------------------------------------------------------
     htdocs/file2.txt                                       |   11 ++++++++++-
     3 files changed, 69 insertions(+), 56 deletions(-)

Contributing
------------

Please send any pull requests on GitHub to http://github.com/josephdpurcell/git-extras/.

