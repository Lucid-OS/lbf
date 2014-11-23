### Information on the metadata checkdeps creates.

#### What each of the files do:

##### Origin Files.

Name | Description
---- | ----
origin | Keeps track of all packages that have already been checked. This list includes packages that have no PKGBUILD file itself.
suborigin | Keeps track of all packages to be checked. This is the global check file.
origin_list | This is used to create the recursive capabilities of the origin system. These files are created for each search list needed. Each step of recursion will have its own orgin_list file. The starting search parameter will have an origin_list file and every dependency will have its own origin_list file.
origin_list_old | Once an origin list has been scanned and checked the origin_list is renamed to origin_list_old. This prevents checking of packages that have already been checked.
origin_"search name" | "Search name" will be the search parameter you send at checkdeps using the -n flag. This keeps track of all dependencies created within a single search, What originated the search for this package and the repository name of where this package is located.

##### Metadata files created by checkdeps.

Name | Description
---- | ----
deps | Dependencies of the package.
makedeps | Make dependencies of the package.
checkdeps | Check dependencies of the package.
provides | Packages the PKGBUILD provides that will not have their own PKGBUILD file.
treeloc | The location in the checkdeps tree. This can be used to find the package information in the created tree.
spawned_from | What originated the search on this package.
repo | The repository name and location of the PKGBUILD file.

#### How the origin system works.

##### Stage 1.

In this stage preliminary data is obtained that allows us to start scanning PKGBUILD files.

1. The initial scan of the pkg or group is created and placed in an array list.
2. The working directory for the search is created.
3. Each entry is checked against the origin file to make sure it has not already gone through the scanning process.
4. Each entry is checked against the suborigin file so we do not add entries to the suborigin file twice.
5. We check to see if there is an origin_list_old file. If there is we do not do a search for this.
6. If the entry needs to be processed it is added to the suborigin file and the appropriate origin_list file.
7. We now have an origin_list file to work from.


##### Stage 2.

In this stage we have the data required to scan and gather more information about each PKGBUILD file.

The origin_list file created in Stage 1 is read and goes through the following process:

1. A directory is created with the name of the program in the appropriate location.
2. The PKGBUILD for the package is scanned.
3. As dependencies are checked they are written to the suborigin and origin_list file.
4. The dependency information is written to the corresponding deps, checkdeps or makedeps file.
5. The repo information is written to the repo file.
6. The location within the checkdeps tree are written to the treeloc file.
7. The information of what originated the program search is written to the spawned_from file.
8. What the package provides is written to the provides file.
9. The origin_"search name" file is written to include all searches on this particular search.
10. The origin file is written with the package name that was processed.
11. The next package from the Stage 1 is processed, Repeating Stage 2. When there are no more entries in the origin_list file we move onto Stage 3.


##### Stage 3.

Essentially Stage 3 consist of a recursive action upon Stage 2. We now have many origin_list files and each one of them is processed as described in Stage 2. The recursion only stops when there are no more origin_list files to process.

[Back to lbf documentation.](../index.html) | [Back to checkdeps index.](index.html)
---- | ----
