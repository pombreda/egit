# JGit Tutorial #

If you are new to JGit this tutorial will help you get started with using JGit. It will cover some of the basic tasks of working with git repositories, such as walking the revision history and inspecting trees, and provide hints to how you should design your program to best make use of JGit.

During the tutorial you will be presented with code that deals with solving one particular problem. We hope that you will be able to adapt this sample code to suit your own needs. All the code used in this tutorial is available under the same license as JGit.

_Note: This tutorial is currently a work in progress. So for the time being most of the pages are either empty or simple stubs. Contributions and ideas on how to improve this tutorial are very welcome._

## Design Philosophy ##

  * Abstractions?
  * Speed?
  * Extensible

### The Basic Object Model ###

If you are already familiar with how git stores data in the repository, JGit's approach to representing repository objects should come quite natural to you. As we shall see, there are various different frameworks for accessing the objects in the repository. One is very light weight and suitable for revision walking, and the other is richer in features and targeted for more specific work flows where you, for example, need to be able to modify the in-memory representation of an object. This design choice has been made to provide the developer with the choice between the best possible performance and or convenience depending on what task needs to be solved.

An important feature of git repositories is the ability to easily address any content by an ID. In JGit, this is modeled using the ObjectId class, which serves as the unifying way to address the objects in the repository. It is also the base class for some of the light weight types representing repository objects.

## Error Handling ##

Many operations in the library may require some sort of IO operations, such as loading an object or pack file into memory. As a result, calls that touch a code path using IO access can throw exceptions. Throughout the examples in this tutorial, we will try to document how to interpret the meaning of the exceptions that can be encountered.

There are currently no best practices for error handling and diagnosing why the error occurred. However, keep in mind that choosing to ignore exceptions may lead to data loss. For an overview of JGit specific errors take a look at `org.spearce.jgit.errors`.

## Limitations ##

JGit is still under development and so naturally there are features that are not yet supported. For example, JGit does not have its own diff engine for generating patches. You will also not find a way to automatically run the hooks installed in a repository. In general, however, all the features for accessing the content of git repositories are fully supported. During the tutorial limitations will be listed if they are deemed important.