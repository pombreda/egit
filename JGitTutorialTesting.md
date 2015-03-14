# Testing JGit #

If you intend to develop and extend JGit, you probably want to check that you didn't break anything. To accomplish this you can use JGit's test suite which is located in the `org.spearce.jgit.test` folder. It uses JUnit to test the different parts of the library and relies on various input files located in the folder.

## Coverage ##

While the test suite is a good way to figure out if something is broken, it doesn't cover all aspects of the library at the moment. So in addition to running the test suite you can increase the coverage by also running some of the commands in the JGit CLI. Apart from the CLI being closer to code you might use in your own application it also let's you test your changes in real-world repositories.