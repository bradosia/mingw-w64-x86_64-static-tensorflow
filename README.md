# tensorflow static libraries for MinGW64
Includes a static library linked test program in windows with MinGW64 compiler. All static libraries are prebuilt and included with the executable. 

Features demonstrated:


Compiler: 
* gcc (x86_64-posix-seh-rev0, Built by MinGW-W64 project) 8.1.0

IDE: 
* Eclipse IDE for C/C++ Developers
	* Version: 2019-12 (4.14.0)
	* Build id: 20191212-1212

Library: 
* tensorflow 1.15.0

## How static library was made
1. Download TensorFlow source from https://github.com/tensorflow/tensorflow/releases/tag/v1.15.0
2. Extract and place into directory /c/source/tensorflow-1.15.0
3. Download Bazel 0.26.1 from https://github.com/bazelbuild/bazel/releases?after=0.28.0
4. Rename to bazel.exe and place in /c/msys64/usr/bin
5. Using MSYS2 shell, attempt to build tensorflow with 

```shell
pacman -Su
pacman -Sy base-devel msys2-devel
pacman -Sy mingw-w64-x86_64-python3 mingw-w64-x86_64-python3-pip mingw-w64-x86_64-python3-numpy mingw-w64-x86_64-python3-scipy mingw-w64-x86_64-python3-matplotlib mingw-w64-x86_64-python3-pandas mingw-w64-x86_64-python3-Pillow
pacman -Sy mingw-w64-x86_64-cmake mingw-w64-x86_64-python2-numpy mingw-w64-x86_64-python2-protobuf mingw-w64-x86_64-python2-absl-py mingw-w64-x86_64-python2-mock mingw-w64-x86_64-python2-pbr mingw-w64-x86_64-python2-funcsigs mingw-w64-x86_64-python2-wheel mingw-w64-x86_64-python3-protobuf mingw-w64-x86_64-python3-absl-py mingw-w64-x86_64-python3-mock mingw-w64-x86_64-python3-pbr mingw-w64-x86_64-python3-funcsigs mingw-w64-x86_64-python3-wheel mingw-w64-x86_64-swig 

cd /c/source/tensorflow-1.15.0
./configure
/mingw64/bin/python.exe
/mingw64/lib/python3.8/site-packages

/c/msys2/mingw64/bin/python.exe
/c/msys2/mingw64/lib/python3.8/site-packages

C:/msys2/mingw64/bin/python.exe
C:/msys2/mingw64/lib/python3.8/site-packages

export MSYS_NO_PATHCONV=1
export MSYS2_ARG_CONV_EXCL="*"

bazel build --config=opt --action_env PYTHON_BIN_PATH=/c/mysys64/usr/bin/python.exe //tensorflow/tools/pip_package:build_pip_package 
bazel build --config=opt PYTHON_BIN_PATH=/mingw64/bin/python.exe //tensorflow/tools/pip_package:build_pip_package 
bazel build //tensorflow/tools/pip_package:build_pip_package 

bazel build --config=opt --cpu=linux --compiler=mingw-gcc //tensorflow/tools/pip_package:build_pip_package 
cd build
make
```

6. Tackle each error that comes up by installing required libraries
7. static libraries located at /c/mingw/xpdf-4.02/build/xpdf/libxpdf.a



tensorflow-2.1.0-rc2
cd /c/source/tensorflow-2.1.0-rc2
