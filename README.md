# Mallie ray tracer

https://lighttransport.github.io/mallie

![Example](https://github.com/lighttransport/mallie/blob/master/mallie.jpg?raw=true)

Mallie is bootstrap for ray tracing study and research. Its already used in some ray tracing research.
You can easily extend/implement ray tracing algorithm.
Mallie is written in portable C/C++ and depends on few third party libraries.

## Features

* Binned SAH BVH builder(robust and works well up to 10M triangles).
* Intel's Embree support for fast ray tracing.
  * 2 ~ 3 times faster than reference implementation of mallie's Binned SAH BVH.
* wavefront .obj loader(tinyobjloader)
* MagicaVoxel .vox loader
* Very simple path tracer example.
* Portable C++(at least it should be compiled with gcc/clang/VisualStudio, and run on MacOSX/Linux/Windows, x86/ARM)
* JSON configuration and JavaScript script engine(duktape)
* OpenEXR loader(tinyexr)
* OpenEXR writer(miniexr)

## Building

### Requirements

* C++ compiler
* GCC (If you want OpenMP support)
* SDL2.0(optional)
* ptex(optional)
* Embree raytracing kernel(optional)
  * http://embree.github.io

#### Setup

Download embree and put it into `deps` directory(optional)

Build ptex(optional)

    $ cd deps/ptex-master
    $ make

Build SDL2(optional)

    # linux
    $ ./scripts/build_deplibs_linux.sh

    # MacOSX
    $ ./scripts/build_deplibs_macosx.sh

#### MacOSX

Edit scripts/setup_macosx.sh, then,

    $ ./scripts/setup_macosx.sh
    $ export CC=gcc48 # optional
    $ export CXX=g++48 # optional
    $ make
 
#### Linux

Edit scripts/setup_linux.sh, then,

    $ ./scripts/setup_linux.sh
    $ export CC=gcc48 # optional
    $ export CXX=g++48 # optional
    $ make

#### Windows

Edit vcbuild.bat, then,

    > vcbuild.bat

Solition file will be generated.
Tested on VS2013.

#### Bootstrap options for premake4

    --with-sdl        : Enable SDL(GUI)
    --with-openmp     : Enable OpenMP
    --with-embree     : Enable Embree

### Usage

Edit config.json, then

    $ ./bin/mallie

GUI mode

* mouse left : rotate
* shift + mouse left : translate
* ctrl(or tab) + mouse left : dolly
* 'q' : quit.
* 'c' : Dump camera data to camera.dat (eye, lookat, up, quaternion)
* 's' : Save framebuffer as .exr image.

## Quick start to hacking

See `render.cc::Render()`.

## Author(s)

* Light Transport Entertainment, Inc.

## License

Mallie is licensed under 3-clause BSD. See `LICENSES.3rdpaty.txt` for components used in Mallie.

EoL.
