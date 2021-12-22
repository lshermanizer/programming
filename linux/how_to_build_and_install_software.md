

Ref: https://sites.google.com/a/case.edu/hpcc/home/important-notes-for-new-users/software-installation-guide
Ref: https://sites.google.com/a/case.edu/hpcc/helpful-references/compiling--linking

### Compiling and linking
The process of converting source code, written in a language such as C, to a binary file ready to be executed is called **compiling**. 

GNU C Compiler = gcc






### Get the platform info

```
uname -a
```

output:
```
Linux hpc2 2.6.32-642.3.1.el6.x86_64 #1 SMP Sun Jun 26 18:16:44 EDT 2016 x86_64 x86_64 x86_64 GNU/Linux
```
This inidcates Intel Xeon 64 bit platform (architecture based on Intel 8086 CPU) for GNU/Linux Kernel version 2.6.32-642.3.1.el6.x86_64 (el6=>enterprise linux OS version 6)"

For more information: 
```
lscpu
```

Get the operating system (OS) info:
```
cat /etc/redhat-release
```

For shared memory system, check memory:
```
ipcs -l
```

### Software Package Dependencies or Pre-requisites

RPM = RPM Packet Manager (formerly the Red Hat Package Manager), tracks and manipulates applications installed on the system. 

First check the rpm list. For an example, let's search for "libpng" package installed as RPMs:
```
rpm -qa | grep libpng*
```

output:
```
libpng-1.2.49-2.el6_7.x86_64
libpng-devel-1.2.49-2.el6_7.x86_64
```

After the RPM dependency list, check the module list. 


### Installation from source code

Obtaining software directly from the source code generally requires Linux to configure so as to help the program to run on wide varieties of computers by matching the `libraries` on user’s computer. The configuration process creates `make` files for `compiling` the code, the executable of which will then be `installed` at the appropriate install directory. Finally, you can configure your .bashrc file.

In the installation directory, if you find `CMakeLists.txt`, then you need to install it using `cmake` utility. If you find `configure` file, then follow another process. During installation, the `default compilers and libraries` required for installation are used. Along with the compiler, Linker flags, you may need to provide the path to the binaries, include path, and libraries as required by your software or those you chose to use.

### Check what are the default Intel, GNU, and MPI compilers:
```
which gcc; which icc; which mpicc
```

output:
```
/usr/bin/gcc                                                    #GNU C Compiler
/usr/local/intel/2012/composerxe-2011.3.174/bin/intel64/icc     #INTEL C Compiler
/usr/local/openmpi/1.6.3/bin/mpicc                              #MPI C Compiler
```

Use `module` commmands to check if you havethe module:
```
module spider gcc
module avail mpi
module display openmpi   #see its compiler, include, and library paths
```

#### 1. Cmake installation
Essentially:
```
cmake -DCMAKE_INSTALL_PREFIX=/home/<caseID><path-to-install>; make; make install
```

Cmake is the cross platform build system. Build process is described in a simple text file CMakeLists.txt via special CMake commands. When invoked, CMake parses these text files and generate a native build chain for the desired platform and compiler. It provides options for user to customize the build process.

The options are presented in the form of variables which usually are of the form `PACKAGE_<SOME>_<OPTION>` and may contain anything from BOOLEAN to strings. For an example, to enable GROMACS package with MPI option, use `GMX_MPI=ON`. 

To change the content of the CMake Cache variable, use –D option after cmake command. To change the location of the install directory from default `/usr/local` to home directory, use `"DCMAKE_INSTALL_PREFIX=/home/<caseID><path-to-install>"`.

Make a build directory and cd to it. The compilers output are stored here which includes both object files as well as final executable and libraries. It also stores several other files including its cache. It is helpful to build with different build options:
```
mkdir build;cd build
```

Load the cmake modules:
```
Module load depends
Module load cmake
```

See the CMake Variable List:
```
cmake --help-variable-list
```

output:
```
CMAKE_INSTALL_PREFIX
CMAKE_LIBRARY_PATH
...
```

Run cmake command with appropriate options, e.g.:
```
cmake .. -DGMX_GPU=ON –DGMX_MPI=ON -DCMAKE_INSTALL_PREFIX=/home/<caseID><path-to-install>
```

If you need to assign multiple libraries, you can do it with `-D<X_LIBRARIES>='-L <path-to-library> -l<lib1> -l<lib2>'`

If you need to select compiler and library options, edit `CMakeLists.txt` file to apply those changes.

The error and output files are `CMakeError.log` and `Output.log` at `<build-dir>/CMakeFiles/`.

Makefile gets created at the source directory once the configuration gets through. Now, you can issue `make` command:
```
make
```

To install the binaries and libraries at the location prefixed by configure for the installed software, issue `make install` command:
```
make install
```




#### 2. Configure-make-make installation

Essentially:
```
./configure --prefix=/home/<CaseID>/<path-to-install-dir>; make; make install
```

More on `configure`:

By default, the installation directory is `/usr/local`, So, you NEED TO change the installation path to your home directory by using prefix option:
```
./configure  --prefix=/home/<CaseID>/<path-to-install-dir>
```

To see more options:
```
./configure --help
```

If you have option for shared libraries, use --enable-shared to create shared libraries:
```
./configure --enable-shared --prefix=/home/<CaseID>/<path-to-install-dir>
```

Save configure and make output using `tee` command:
```
./configure  --prefix=/home/<CaseID>/<path-to-install-dir> | tee <outputfile>
```

Makefile gets created at the source directory once the configuration gets through. Now, you can issue make command:
```
make
```

To install the binaries and libraries at the location prefixed by configure for the installed software, issue make install command:
```
make install
```

Some of them might have GPU and MPI options such as `–enable-mpi` and `–enable-gpu`.

#### 3. Makefile installation

Some installation may just have Makefile. So, you need to view the Makefile and make changes to the path of the environment variables properly in accordance with HPC environments. As an example, the entry below should be changed to your home directory as you don't have write permission in `/usr/*`.
```
# default installation directory 
INSTALLDIR=/usr/local/bin 
```
changed to:
```
# default installation directory 
INSTALLDIR=/home/<CaseID>/<path-to-installation>
```

Then make:
```
make
```
