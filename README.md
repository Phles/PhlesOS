# Phles OS Project
PhlesOS is a project to build an open-source, developer-friendly operating system that gives users as much control as possible over their devices.
The project itself is broken into many submodules, each of which will warrant their own git repository.


In an effort to make porting this OS  as easy as possible, the main languages for each module (except the boot module) will be C/C++.
Although writing as little assembly as possible will result in a slower OS, the modular nature of this project should allow others to write more efficient modules for each individual architecture (e.g. MMU support for x86-64 systems instead of the default manually paged memory). The main, slower modules are intended to be a starting point for new developers.

## For Beginners: https://github.com/Phles/PhlesOSPlayground

PhlesOS Playground is a rudimentary OS intended for beginners to play around with. It is a testing ground for new features for PhlesOS and the first commit is based off a video in the README for that project.

## Licensing
While PhlesOS and its source code is licensed under a Zlib License, many of its dependencies and build tools use the GNU Public license. More information about the GNU Project and its licenses can be found here: https://www.gnu.org/ .
>[!WARNING]
 Because this project downloads the source code for GNU tools, it is important to remember that any external tools used for this OS falls under their own license terms and conditions. 
# Contribution
More information about contribution will be available soon. 
Contact phlesproject@gmail.com if interested.

# Modules
Other modules for this OS are coming soon.


