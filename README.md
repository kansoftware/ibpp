# IBPP
This is an update to C ++ 11 standards from the original IBPP project. IBPP, where the 'PP' stands for '++', is a C ++ client interface for Firebird SQL. This update was due to the fact that the last update to the official repository is in 2015.
Source code for QT was forking from https://github.com/saulozitos/IBPP-Library/tree/master.

This is a cmake version ready to use with ci/cd.


#usage
```bash
git clone https://github.com/kansoftware/ibpp.git
cd ibpp
mkdir ibpp
cd ibpp
cmake ..
cmake --build . -- -j `nproc`
cpack -G DEB
```

Enjoy!