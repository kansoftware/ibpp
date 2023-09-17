# IBPP
This is an update to C ++ 11 standards from the original IBPP project. IBPP, where the 'PP' stands for '++', is a C ++ client interface for Firebird SQL. This update was due to the fact that the last update to the official repository is in 2015.
This source code for QT was forking from https://github.com/saulozitos/IBPP-Library/tree/master.

This is a cmake version ready to use with ci/cd.


# Usage

## Build

```bash
git clone https://github.com/kansoftware/ibpp.git
cd ibpp
mkdir build
cd build
cmake ..
cmake --build . -- -j `nproc`
cpack -G DEB
```

## Install package
```bash
sudo apt -f ibpp-0.0.1-Linux.deb
```

## Change cmake
Add the following lines to cmake:

```cmake
include_directories( /usr/include/kansoftware/)
link_directories( /usr/lib/kansoftware/)
target_link_libraries( #YOUR_TARGET_PROJECT# ibpp )
```

Enjoy!
