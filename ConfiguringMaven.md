# Configuring Maven #

Snapshots of JGit are available via the Google Code project area for use in [Maven 2](http://maven.apache.org/) projects. The update policy is to synchronize the snapshots a few times a month depending on the number of changes and whether notable changes have been made.

To use the snapshot repository from your Maven project, add the following element to the `<repositories>` section of either your pom.xml or settings.xml:
```
<repository>
    <id>jgit-maven-repository</id>
    <url>http://egit.googlecode.com/svn/maven/</url>
</repository>
```

Then add the element below to the `<dependencies>` section of your pom.xml:
```
<dependency>
    <groupId>org.eclipse.jgit</groupId>
    <artifactId>org.eclipse.jgit</artifactId>
    <version>0.5.1.51-g96b2e76</version>
</dependency>
```

To get a more specific build version number, see http://code.google.com/p/egit/source/browse/maven/org/eclipse/jgit/jgit-parent/maven-metadata.xml.