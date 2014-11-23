### What is the Linux Build Framework?

The Linux Build Framework is a set of bash scripts that help with a variety of Linux distribution creation tasks.

I will hereby refer to the Linux Build Framework as lbf for short.

### What does the framework do?

* lbf is a framework that helps developers build linux distributions.

### What is included in lbf?

* In the current state lbf is in heavy development and is currently experimental.

Here is a list of programs and or future functionality that will be provided by lbf:

name | state | description
---- | ---- | ----
[checklinks](checklinks/index.html) | semi-complete | Checks the links within a PKGBUILD and verifies that the programs exist.
[checkdeps](checkdeps/index.html) | semi-complete | Recursively checks dependencies of packages, groups of packages or entire repositories.
`cleanbuildroot` | old | Removes the chroot build directory and creates a new one.
`lbf` | old | Leftover from the old lucid-build branch. The logic will be examined and used at a later time.
`repomod` | Work in Progress | This script will modify the repository structure within the git repositories.
