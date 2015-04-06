## Rationale ##

Abundance of version control systems increases barriers for open source collaboration. Faced with the problem to learn all of them, developers tried to create tools to [convert between repositories](http://mercurial.selenic.com/wiki/RepositoryConversion) or add support to work directly with alien repos with their VCS of choice. This requires exporting and converting changeset information.

Unfortunately, some VCS provide access to necessary data about their changeset only through low level API. For example, for successful SVN -> HG conversion you need to install SVN bindings for Python, and it can be [hard to get these in place](http://techtonik.rainforce.org/2010/09/hgsubversion-installing-on-windows.html) for particular platforms (e.g. Mercurial MSI installation on Windows).

Changesets exported from VCS often do not provide sufficient information about changes being made ('hg diff --git' won't contain contents of copied or moved files, `hg diff` does not export info about parent revision [2](2.md), `svn diff` and standard unified diff format do not show where the file was copied from, etc). VCS usually provide dynamically typed commands to inspect uncommitted changes, but no full info is contained in a single changeset export format.

The above points provide many pitfalls for [code review](http://code.google.com/p/rietveld/) systems, which should extract as much information as possible about changeset, either committed or uncommited.

Extensible Changeset Format solves the problem of incomplete information and allows to include new, yet unknown properties that may be vital for some VCS. Other VCS can ignore this.

The essential part of the format is that it cares about **2 dimensions** of changeset data. 1D is file line modifications (traditional unified diff) and 2D is filesystem treee structure modification (file movements, renames, copies, creation of directories and separate properties for them). It also allows to manage changes to additional `properties` to both structure elements.

Information in Extensible Changeset format contains data about filesystem tree modifications not tied to any particular VCS (set of common properties). It also contains VCS specific information about changeset (meta data changes) in forward and backward compatible way. Tools supporting this format may explicitly ignore properties they don't understand (and add support for them incrementally). Defined sets of properties give VCS authors ability to create interoperable instruments on early stage of development.

## Details ##

### Contents ###
**Changeset** is an atomic modification to filesystem tree. It contains **data** about actual modifications of filesystem tree (set of operations in appropriate order) as well as **meta-data** related to VCS that manages this modification (revision number, parents, author, repository id, root path, etc).

### Ideas ###
**Header**. The summary header should contain information about tree transformations without details. The will allow to express this information in YAML (or any other format) without parsing the contents. Such headers can be useful to analyze changes _between_ changesets without fully parsing the changeset data.

**Operations analysis**. The complexity of the format and implementations depends if operations in changeset are order independent, if they are atomic (can not be interrupted in the middle), symmetric (can be rollbacked safely).

### Use Cases ###
  * 001  - file added
  * 002  - file modified
  * 003  - file removed
  * 004  - file renamed
  * 005  - file moved

### Format ###
Although the first thing that comes to mind after the word "eXtensible" is XML, the format should be plain simple to be easily mapped to JSON or similar representation (i.e. flat XML, without attributes).

In XML it is logical to use namespaces for separation of data sets, but to keep format dead simple (and translatable into JSON and back), it may be easier to separate elements from namespaces with underscore (no minus, because you won't be able to map the name of field into the name of object property as-is).

<a href='Hidden comment: 
speaking about atomic modification to filesystem tree, unfortunately, not many filesystems support atomic renames
'></a>

## References ##
  1. [Proposal to Subversion developers](http://svn.haxx.se/dev/archive-2010-08/0691.shtml)
  1. [Mercurial diff should include the number of parent revision](http://bz.selenic.com/show_bug.cgi?id=1268)
  1. [Mercurial HG19 Bunder Format](http://mercurial.selenic.com/wiki/BundleFormat2)