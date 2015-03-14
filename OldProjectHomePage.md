This project has [moved to Eclipse.org](http://www.eclipse.org/egit/)

EGit relies upon JGit for the bulk of its implementation.

JGit is a 100% pure Java implementation of Git.  JGit is a BSD-licensed reusable library that carries no Eclipse dependencies, and very few (if any) dependencies beyond the Java 5 standard library.  To make it clear: JGit does _not_ in any way depend on the Eclipse plugin. They just happen to live in the same repository for the time being.

The plugin only works on Eclipse 3.4 (Ganymede) or newer. Eclipse 3.3 (Europa) is not
supported anymore. Since the plugin is still very much work-in-progress we want to
take advantage of new platforms features to facilitate progress.


---

**IMPORTANT when upgrading**

The plugin has been renamed since it is now an Eclipse project in the incubation stage.
The rename will cause some inconvenience.

When upgrading to the org.eclipse.egit plugin you basically haver these  options:

  * Alternative A
> Disconnect all projects from the Git team provider
> Uninstall the org.spearce.egit feature
> Install the org.eclipse.egit feature
> Share the projects again
  * Alternative B:
> Unistall the org.spearce.egit.feature
> Install the org.eclipse.egit feature
> Delete any Egit-shared projects (keep content on disk)
> Re-import projects
> Re-share projects
  * Alternative C:
> Continue using the org.spearce.egit plugin for existing workspaces.
> Unpack a new Eclipse and install the org.eclipse.egit plugin in the new Eclipse
> and use it for new workspaces.

We do not support a smoother switch because we deemed the effort necessary was not worth it. Please, bear with us.

See the sidebar for locations


---


## Reporting bugs ##

Make sure you can verify a bug against the <b>latest integration build</b> before submitting a bug report. Reports referring to (very) old versions (at the time of the report) are absolutely useless and will mercilessly be closed as invalid. If the current integration build is unusable, try a release or stable build <b>if</b> it is recent (like a few months old at most).

**Move to eclipse.org**

The plugin has been accepted as an Eclipse plugin. Please report new EGit bugs to http://bugs.eclipse.org. EGit resides under the Technology project. Bug that you
know related to JGit only can still be reported here.

## Git Repository ##

The JGit and EGit code are maintained in two Git repositories: _See [EGit Contributor Guide](http://wiki.eclipse.org/EGit/Contributor_Guide) for current repositories_

  * git clone ~~git://repo.or.cz/jgit.git~~
  * git clone ~~git://repo.or.cz/egit.git~~

or

  * git clone ~~http://repo.or.cz/r/jgit.git~~
  * git clone ~~http://repo.or.cz/r/egit.git~~


The current sources and project history can also be browsed online: ~~[JGit](http://repo.or.cz/w/jgit.git)~~, ~~[EGit](http://repo.or.cz/w/egit.git)~~.

## Eclipse update site ##

The Eclipse Git Team provider can be installed via an update site. Point the update
mechanism to ~~http://www.jgit.org/updates~~. The pre-incubation updates are still available
from the old url ~~http://www.jgit.org/update-site~~.

## New Contributors ##

Want to get involved?  Check our "low hanging fruit" list of open issues, doing one or two can help you get introduced to the JGit library:

  * ~~[Low hanging fruit](http://code.google.com/p/egit/issues/list?q=Difficulty-Low&colspec=ID+Type+Status+Priority+Component+Difficulty+Summary)~~

See ~~[SUBMITTING\_PATCHES](http://repo.or.cz/w/egit.git?a=blob;f=SUBMITTING_PATCHES;hb=HEAD)~~ in the repository for instructions on how to submit patches.