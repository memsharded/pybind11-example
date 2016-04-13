# pybind11-example
Getting started with Pybind11 C/C++ python bindings

Get this example repository and install pybind11 with [conan C/C++ package manager](https://conan.io)

```bash
$ git clone https://github.com/memsharded/pybind11-example.git
$ cd pybind11-example
$ mkdir build && cd build
$ conan install ..
```

Build the extension. The parameters must match your compiler and python installation. Note that the extension architecture must match your python one, so if you have python 32 bits, use "Visual Studio XX" and if you have python 64 bits, you may need "Visual Studio XX Win64". 

```bash

$ cmake .. -G "Visual Studio 14" -DPYTHON_INCLUDE_DIR="C:/Python27/include" -DPYTHON_LIBRARY="C:/Python27/libs/python27.lib"
$ cmake --build . --config Release
```

In linux, you could use the following commands to build it, and it may automatically find python, but please check the cmake output to ensure that it is finding your desired python distribution.

```bash

$ cmake .. -DCMAKE_BUILD_TYPE=Release
$ cmake --build .
```

The build is configured to create the ``example`` extension in the build directory, so you can directly try it out from there:

```bash
$ python
>>> import example
>>> example.add(2, 3)
5L
```
