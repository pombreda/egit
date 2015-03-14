# Update Mylyn #

Make sure you have Mylyn 3.0.1 or later.  You can add the update sites if necessary:

from http://www.eclipse.org/mylyn/downloads/

  * http://download.eclipse.org/tools/mylyn/update/e3.4
  * http://download.eclipse.org/tools/mylyn/update/incubator

If the update sites do not show up when adding them, you already have mylin installed. It may be the wrong version so select "Manage Sites" and check the new update site so it will actually be searched for newer versions of Mylyn.

Install the **Web Templates (Generic Web Connector)** plugin so Eclipse can scrape the code.google.com website interface for you.

# Configure Mylyn #

You can follow the instructions [on Alex Ruiz's weblog](http://www.jroller.com/alexRuiz/entry/using_mylyn_with_google_code) to configure Mylyn.  This is basically what I did:

  * Window->Show View->Mylyn->Task Repositories
  * Add Task Repository
  * Web Template (Advanced)

  * In "Server" field select **Eclipse Outliner (Google Code)**
  * Change "Server" to http://code.google.com/p/egit/issues
  * Change "Label" to EGit
  * Keep "Anonymous Access"

  * Expand the "Advanced Configuration" section.
  * Change "Query Request URL" to
```
${serverUrl}/csv?can=1&colspec=ID+Status+Type+Owner+Summary
```
  * Change "Query Pattern" to
```
"({Id}[0-9]+?)","({Status}.+?)","({Type}.+?)","({Owner}.+?)","({Description}.+?)"\n
```