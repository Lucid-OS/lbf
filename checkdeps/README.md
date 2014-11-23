### What does checkdeps do?

The checkdeps script will recursively find package dependencies, make dependencies and check dependencies. It is purely an informational tool for sorting git repositories that contain PKGBUILD files.

checkdeps is currently incomplete, It does create and provide a lot of useful data though.

### How does it work?
* [Checkdeps origin system information.](info.html)

### What is the plan with checkdeps?

Fix some regressions.
* While programming checkdeps I started the logic on a single program, Then I made it able to search entire package groups at a time.
* This required another file to be created that is not created when the program does its work on a single file. This is fairly easy to fix I just have not gotten around to it.

Update the program to be able to search entire repositories at a time. This will essentially use similar logic to checking the groups. But again will be slightly different since I am not getting the information from pacman but will rather be creating the list from already existing files within the filesystem.

[Back to lbf documentation.](../index.html) |
---- | ----
