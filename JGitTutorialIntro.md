# Taking JGit for a Spin #

Although you are probably interested in JGit because you want to integrate it into an existing application or create a tool, JGit is more than simply a Java library for working with git repository. So before diving into the different aspects of the library let's take JGit for a spin.

You are probably familiar with the git command line interface (CLI) that can be used from the shell or in scripts. JGit comes with its own small CLI, which, although not as feature-full as the git CLI, is a good way to showcase what JGIt can do. Furthermore, the programs serve as an excellent source of inspiration for how to accomplish different tasks.

## Building the JGit CLI ##

Assuming that you have the EGit git repository cloned and ready, build the `jgit` binary by running the `make_jgit.sh` script:
```
prompt$ ./make_jgit.sh
Entering org.spearce.jgit ...
Entering org.spearce.jgit.pgm ...

Version v0.3.1.737.gf5bc
Created jgit.jar.
Created jgit_src.zip.
Created jgit.
```
Check your build by running the "version" command:
```
prompt$ ./jgit version
jgit version v0.3.1.737.gf5bc
```
It should print the version that was printing during the build.

## Overview ##

When given the -h flag, commands provide a helpful message listing what flags they support.
```
prompt$ ./jgit version -h
jgit version [--help (-h)]

 --help (-h) : display this help text

```
Running `jgit` with no arguments lists all available commands.
```
prompt$ ./jgit 
jgit --git-dir GIT_DIR --help (-h) --show-stack-trace command [ARG ...]

The most commonly used commands are:
 branch   List, create, or delete branches
 fetch    Update remote refs from another repository
 log      View commit history
 push     Update remote repository from local refs
 rm       Stop tracking a file
 tag      Create a tag
 version  Display the version of jgit

```
The commands are modeled after their corresponding command in the git CLI. We will not cover all the commands here, but simply give some examples.

## Inspecting the Repository ##

Before inspecting the most recent commits, you probably want to know which branches the repository contains and what branch is currently checked out. Using the branch commands `-v` flag, you get a small summary of branches, their revision, and the first line of the revision's commit message.
```
prompt$ ./jgit branch -v
  jf/pathof 4735f32 More fixes from Shawn
* master    f5bc4f5 Enable commit for any resource in a Git-shared project
```
The log command, like [git-log(1)](http://www.kernel.org/pub/software/scm/git/docs/git-log.html), shows the commit log. For example,
```
prompt$ ./jgit log --author spearce --grep index master
commit e8634851f46e1b54db17a45a9008b6e6284f34ce
Author: Shawn O. Pearce <spearce@example.org>
Date:   Thu Aug 28 23:54:10 2008 -0600

    index-pack: Avoid disk corruption in objects appended to thin packs
    
    When we are appending onto a thin pack we need to make sure the whole
    object we wrote into the pack is what is there when we re-read the
    pack to compute the final footer.
...
```
Will show you all commits in the "master" branch, where the author name matches "spearce" and the commit messages contains the word index. More search criteria to filter the commit log, such as committer name, can be given.

## Revision Plotting ##

Finally, to show some of the graphical capabilities of JGit, we will end this small tour by launching the graphical log tool.
```
prompt$ ./jgit glog
```
This should give you a window with the revision graph plotted to the left and three columns containing the first line of the message, the author name, and the commit date.

![http://egit.googlecode.com/svn/wiki/images/JGitTutorialIntroGLog.png](http://egit.googlecode.com/svn/wiki/images/JGitTutorialIntroGLog.png)