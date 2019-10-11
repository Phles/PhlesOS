#
#	Makefile for downloading and installing the GCC/Binutils cross compiler toolset.  
#		Requires git, wget, and tar.
#		Package manager commands are written as macros
#		Package managers are only used for getting GCC and Binutils dependencies, which can be found here: https://wiki.osdev.org/GCC_Cross-Compiler
#

#Output directory for the cross compiler, must be absolute
PREFIX32="$(HOME)/Desktop/mount/PhlesOS/Compilers/bin32"
PREFIX64="$(HOME)/Desktop/mount/PhlesOS/Compilers/bin64"
#Architecture of the compiled platform
TARGET32="i386-elf"
TARGET64="x86_64-elf"

##########################################################################################################################################
#	Binutils																															 #
##########################################################################################################################################

#Build the binutils tools for this compiler. May take a very long time on the first build.
.binutils32: 
	mkdir ./binutils/build || true
	rm -rf ./binutils/build/*
	cd ./binutils/build/ && ../binutils-gdb/configure --target=$(TARGET32) --prefix="$(PREFIX32)" --with-sysroot --disable-nls --disable-werror
	cd ./binutils/build/ && make
	cd ./binutils/build/ && make install
.binutils64:
	mkdir ./binutils/build || true
	rm -rf ./binutils/build/*
	cd ./binutils/build/ && ../binutils-gdb/configure --target=$(TARGET64) --prefix="$(PREFIX64)" --with-sysroot --disable-nls --disable-werror
	cd ./binutils/build/ && make
	cd ./binutils/build/ && make install
#Build all binutils supported
binutils: .binutils32 .binutils64

#Binutils source via git repo. 
install-binutils:
	mkdir binutils || true
	cd ./binutils && git clone git://sourceware.org/git/binutils-gdb.git
update-binutils:
	cd ./binutils/binutils-gdb && git fetch origin master

##########################################################################################################################################
#	GCC   																															     #
##########################################################################################################################################
#Information about the GCC configuration
GCCVer=9.2.0
GCCBuildDir=./gcc/build
RedZonePath=gcc/config/i386

#x86-64 only, Modify the gcc configuration to have no red-zone: https://wiki.osdev.org/Libgcc_without_red_zone
remove-RedZone: 
	echo 'Not Implemented'
	#TODO, modify gcc configuration files
#Build GCC Cross Compiler. 
.gcc32:
	mkdir $(GCCBuildDir) || true
	rm -rf $(GCCBuildDir)/*
	cd $(GCCBuildDir) && ../gcc-$(GCCVer)/configure --target=$(TARGET32) --prefix="$(PREFIX32)" --disable-nls --enable-languages=c,c++ --without-headers
	cd $(GCCBuildDir) && make all-gcc
	cd $(GCCBuildDir) && make all-target-libgcc
	cd $(GCCBuildDir) && make install-gcc
	cd $(GCCBuildDir) && make install-target-libgcc
.gcc64:
	mkdir $(GCCBuildDir) || true
	rm -rf $(GCCBuildDir)/*
	cd $(GCCBuildDir) && ../gcc-$(GCCVer)/configure --target=$(TARGET64) --prefix="$(PREFIX64)" --disable-nls --enable-languages=c,c++ --without-headers
	cd $(GCCBuildDir) && make all-gcc
	cd $(GCCBuildDir) && make all-target-libgcc
	cd $(GCCBuildDir) && make install-gcc
	cd $(GCCBuildDir) && make install-target-libgcc

gcc: .gcc32 .gcc64
#GCC source via GNU's main mirror
install-gcc:
	mkdir gcc || true
	cd ./gcc && wget https://ftp.gnu.org/gnu/gcc/gcc-$(GCCVer)/gcc-$(GCCVer).tar.gz
	cd ./gcc && tar xvzf gcc-$(GCCVer).tar.gz

##########################################################################################################################################
#	Misc-Dependencies																													 #
##########################################################################################################################################

#Super-User Command Name
sudo=sudo
#Install command
install=apt install
#Install GCC and Binutils dependencies, links to information about each package are provided as available
install-dependencies:
	#Parser-generator https://www.gnu.org/software/bison/
	$(sudo) $(install) bison
	#Lexing tool for C/C++ https://github.com/westes/flex
	$(sudo) $(install) flex
	#Arithmetic library: https://gmplib.org/
	$(sudo) $(install) libgmp3-dev 	
	#Floating point for complex numbers: https://directory.fsf.org/wiki/Mpc
	$(sudo) $(install) libmpc-dev
	#Floating point precision C library: https://www.mpfr.org/
	$(sudo) $(install) libmpfr-dev
	#Documentation library https://www.gnu.org/software/texinfo/
	$(sudo) $(install) texinfo

#Install Everything
install: install-dependencies install-binutils install-gcc 
#Build everything for  32-bit and 64-bit machines specified by target variables. WARNING: this can take over an hour
all: install .binutils32 .binutils64 .gcc32 .gcc64
