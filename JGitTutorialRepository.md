#summary How to access the basic parts of a git repository.

# The Repository #

All git related work happens in the context of a repository. The repository is where git stores all its data, whether it is the content being tracked or the various "meta-data" containing state information. In JGit, a repository is represented by the Repository class. This class serves as the main entry-point for accessing the different resources provided by the repository on disk.

## Loading a Repository ##

To instantiate a repository, a `java.io.File` object representing the absolute path of the repository must be given. For non-bare repositories, this means that the `.git` directory should also be included, as in the code below.
```
try {
        File gitDir = new File("/path/to/repo/.git");
        Repository repo = new Repository(gitDir);
        // ... use the repository ...
        repo.close();
} catch (IOException ex) {
        // The repository exists, but is inaccessible!
}
```
Once you do not need the repository anymore, it is good practice to "close" it. This way, the resources it is using can more easily be reclaimed by the garbage collector.

## Creating a New Repository ##

If you want to create a completely new repository, the Repository class can also help you. Using the `create()` method it will initialize an empty repository for you on disk using the path given via the File object.
```
try {
        File gitDir = new File("/path/to/new-repo/.git");
        Repository repo = new Repository(gitDir);
        repo.create();
        // ... use the new repository ...
} catch (IllegalStateException ise) {
        // The repository already exists!
} catch (IOException ioe) {
        // Failed to create the repository!
}
```
When creating repositories with JGit, no default hooks files will be installed.

**Note:** If creation of the new repository fails, the directories and files already created on disk are left untouched!

## Repository References ##

Once the Repository has been instantiated, information about branches and other repository references are available. As a first example let's print the name of the current branch:
```
String head = repo.getFullBranch();
if (head.startsWith("refs/heads/")) {
        // Print branch name with "refs/heads/" stripped.
        System.out.println("Current branch is " + repo.getBranch());
}
```

As the name suggests repository references are "symbolic" links into the tracked content, and so often you are not interested in the actual reference, but in the what is being referenced. A first step to get there is to resolve the reference of interest. In the following example, we want to extend the previous example to also list the revision ID of the current branch.
```
try {
        // The following could also have been done using repo.resolve("HEAD")
        ObjectId id = repo.resolve(repo.getFullBranch());
        System.out.println("Branch " + repo.getBranch() + " points to " + id.name());
} catch (IOException ioe) {
        // Failed to resolve.
}
```

The `resolve()` method supports most of the revision expressions supported by git and can serve as an easy way to obtain the ID of the parent of a commit, or the tree ID of a commit.
```
try {
        ObjectId parent = repo.resolve("HEAD^");
        ObjectId tree = repo.resolve("HEAD^{tree}");
        System.out.println("HEAD has parent " + parent.name() + " and tree " + tree.name());
} catch (RevisionSyntaxException rse) {
        // Syntax error in the revision expression, e.g. HEAD~foo. or HEAD^{foo}
} catch (IncorrectObjectTypeException rse) {
        // Type expression applied to incorrect type, e.g. using ^{tree} on blob ID.
}
```

As a final note, all repository references are available as a map via the `getAllRefs()` method. The mapping is to instances of the Ref class, which allows easy access to both the reference name and ID.

## The Configuration File ##

Each git repository contains a configuration file. Initially, it only contains information about what repository format is being used, however, chances are that you eventually want to query options or maybe even store your own settings. Once the repository has been loaded the associated configuration can be file is available via `getConfig()`.
```
RepositoryConfig config = repo.getConfig();
String name = config.getString("user", null, "name");
String email = config.getString("user", null, "email");
if (name == null || email == null) {
	System.out.println("User identity is unknown!");
} else {
	System.out.println("User identity is " + name + " <" + email + ">");
}
```
The configuration file is divided into sections. In the above example, we ask for the "name" and "email" variables for the "user" section. Git also supports subsections, which is primarily used for branch and remote settings. When the subsection is not used `null` is passed.
```
RepositoryConfig config = repo.getConfig();
String url = config.getString("remote", "origin", "url");
if (url != null) {
	System.out.println("Origin comes from " + url);
}
```