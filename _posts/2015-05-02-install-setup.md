---
layout: page
title: "Install & Setup"
category: doc
date: 2015-05-02 12:02:34

---

## Status

Currently testing with node v7.5.0 and V8 5.4.500.48.

```bash
 npm install
```

If your native hdf5 libraries aren't at the default 
you can set the path with --hdf5_home_linux switch on this project as well as 
dependent projects.

```bash
 npm install hdf5 --hdf5_home_linux=<your native hdf path>
```
For mac and windows the switches are --hdf5_home_mac & --hdf5_home_win

## Dependencies

+ [HDF5 C Library](http://www.hdfgroup.org/downloads/index.html) v5-1.10.0-patch1
        (Prior v5-1.8.x's untested yet should work)


## Compiling

The code requires a gcc compiler supporting C++11 for linux, MacOSX & Windows.  The binding.gyp defines the cflags with -std=c++11.


### In a working copy of git

```bash
export NODE_PATH=/home/user/NodeProjects/hdf5.node/build/Release:$NODE_PATH
npm install  --hdf5_home_linux=<your native hdf path>

```

NODE_PATH is still used for the mocha tests.

## Environment Variables

The path to the HDF5 shared objects must be added to the runtime library search path. 

for linux example:

```bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:<PATH-TO-YOUR-HDF5>/hdf5/lib
```

for Mac OSX example:

```bash
export DYLD_LIBRARY_PATH=$DYLD_LIBRARY_PATH:<PATH-TO-YOUR-HDF5>/hdf5/lib
```

for Windows example:

```bash
set PATH=$PATH;<PATH-TO-YOUR-HDF5>/hdf5/bin
```

If you want one of the third party filters available put its install path on HDF5_PLUGIN_PATH

```bash
export HDF5_PLUGIN_PATH=/home/user/NodeProjects/HDF5Plugin
```

## Running Test

The tests are based on co-mocha

```bash
mocha --require should  --require co-mocha
```

