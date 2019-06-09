# Detectorbank!

C++/Python software to detect note events using Hopf Bifurcations.

This repo conatins both the DetectorBank and a NoteDetector.
The NoteDetector comprises an OnsetDetector and a PitchTracker;
however, the PitchTracker is currently not implemented.

The full documentation can be found [here](https://keziah55.github.io/DetectorBank/).

## Requirements

On a Debian system, the following packages should be installed:

* python3-dev
* swig (to build python3 bindings)
* build-essential
* autoconf-archive
* libtool
* libcereal-dev
* librapidxml-dev
* libfftw3-dev
* doxygen (for the documentation)
* python3 (for the documentation as well as the SWIG bindings)
* graphviz (for enhanced documentation)
* texlive-latex-base (for the documentation)
* python3-tap (for the unit tests)


## Installation

You need to install apt install autoconf-archive for lovely
extra macros if you want this to build on debian.

Set up the build system if required

        autoreconf --install --verbose

(or -iv).

We recommend you build the software to and install it from
a new directory.

        mkdir -p build
        cd build
        ../configure
        make

Optionally build and run the unit tests

        make check

The results of the checks are written in test/test-suite.log

        sudo make install
        
Perhaps also test that the library's been installed properly by asking
for the compilation flags

        ( cd ; pkg-config detectorbank --cflags --libs )

Documentation is built in the doxygen-doc subdirectory and installed
in $(docdir)/html. The default top page for the documentation is:

        /usr/local/share/doc/detectorbank/html/index.html

If you don't want/need Python3 bindings generated by SWIG, you can
pass the --without-swig to the configure command. Note that Python3
is still required to build the library.

You can build for debugging by defining the C preprocesor macro DEBUG when
compiling. For example:

        ../configure CPPFLAGS=-DDEBUG=2

in the example above.

DEBUG levels (can be |ed):

    1: Report thread start and end + general usage
    2: Write description of detector normalisation to /tmp/z.dat
       for search normalisation of stdout for chirp normalisation
    4: Log SlidingBuffer memory debugging info (LONG!)

Note that stuff gets printed when DEBUG == 0 (or simply exists).
For no debugging output, don't define it at all.
