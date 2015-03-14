## Acquire plugin ##

## Installation ##
  * Acquire Ganymed (Eclipse 3.4) or later or a distro based on a suffiently recent Eclipse.
  * Install from source using the instructions in the source repository
  * or install from the update site: http://www.jgit.org/update-site.

# Getting repositories into Eclipse #

## Git access in Eclipse ##
  * A toolbar / workbench menu is available if enabled in Window/Customize perspective. By default it is hidden.
  * The right-click/Team and Compare sumenus contains Git actions
  * Decorations can be enabled/customized in Window/Prefernces. Search for "git".
  * Quickdiff for Git can be enabled in Window/Preferences.

## Connecting to an existing git clone ##
  * If you already have projects in a git repo you can enable Git on the project using right-click/Team/Share. As of this writing you can only share one project at a time. Repeat to enable Git on multiple projects.

## Cloning an existing repo ##
  * File/Import/Git allows you to clone a remote repository, import it the Workbench and enable git on it.
  * You can only import it if it has the Eclipse project files ".project" in it. If not you can still clone using the import wizard, but you will need to use File/New/Project to create Eclipse projects.

## Create a new repo ##
  * Use the right-click/Team/Share a choose the "create new" option. By default the repository will be created in the parent directory. This allows you to add more Eclipse projects to the same repo. Most non-toy repositories will containt more than one Eclipse project.

# Sharing your repository with others #

## Push ##
  * right-click/Team/Push. The remote repo must exist before you can push into it.

## Fetch ##
  * right-click/Team/Fetch. Note that the Eclipse plugin currently has no Merge/Rebase built in. You need to use another implementation until Egit gains the capability.