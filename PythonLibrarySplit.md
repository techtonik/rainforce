Code is here: https://bitbucket.org/techtonik/python-stdlib

# Introduction #

User experience of contributing to Python module from standard library is far from ideal. The process involves patching, improving docs, reporting bugs, sending modifications and reviewing existing issues.

Since its birth Python language was developed as monolithic code base with core interpreter and library coming together. No separation between both make standard library structure non-discoverable without manual at hand. It is hard to reliably find all source code, test cases and documentation with sources related to specific module. Patch contributions become harder, process can hardly be automated, which results in a loss of time and fun.

It is hard to follow the progress for specific modules, it is even hard to separate the whole flow of commits, issues and patches into a stdlib and core streams. Maybe people are not interested to submit their modules and support them in standard library, but most likely they just lose motivation to follow ineffective process that supports them.

There is no visibility into module development from outside. From inside you have no control over what's going on with you module issues, patches, commits, comments, docs, reviews etc. This lack of visibility also puts additional burden on tracker triagers, who have to reread all requests instead of limiting triaging to a subset of interested modules. An alternative would be to implement free-for-all edit and decentralized peer review process (like in Trac), but issues need to be referenced to modules anyway.

# Python Module Mapping #

To monitor commits in Python standard library on a module level, the source code of stdlib should be split into modules by grouping paths by module. Current filesystem layout of source code groups files per more generic type - docs, c sources, python sources. Module level grouping often requires files of all three types to come together. That's there should be additional mapping in repository.

To make the grouping process automated, the stdlib layout may require some convention about canonical layout of stdlib and corresponding module files. Right now this layout is Python source code tree.

Splitting code by modules is a first step. Next one may require splitting it into separate repositories and tagging them with Python release numbers (to make the size of clone smaller). Something should be done to branches for various Python versions (and not only for CPython).

The second step in this concept is to modify tools that monitor, develop, test and document stuff to understand modules concept.

# Source Code #

Source to split stdlib into modules, with some utils for tracker is at: https://bitbucket.org/techtonik/python-stdlib