# `RGESolver`
A `C++` library to perform renormalization group evolution of SMEFT coefficients, both numerically and with the leading-log approximation. 
  The general flavour case at dimension-six level is considered. Operators that violate lepton and/or baryon number conservation are not considered.
  
`RGESolver` is a free software under the copyright of the GNU General Public License.
## Dependencies
* `BOOST`  : BOOST is a C++ library which can be obtained from the [`BOOST` website](https://www.boost.org/) or from Linux package managers or Mac ports. RGESolver only requires the BOOST headers, not the full libraries, so a header-only installation is sufficient.
* `GSL` : The GNU Scientific Library (GSL) is a C library for numerical computations. It can be found on the [`GSL` website](https://www.gnu.org/software/gsl/). Most Linux package managers will have a stable version as will any ports for Mac. 
* `C++11` : The compilation forces the `C++` standard to 11. 
## Install `RGESolver`
The installation of `RGESolver` requires the availability of `CMake` in the system (version `3.1` or greater). A description of `CMake` and the instructions for its installation can be found in the [`CMake`website](https://cmake.org/).

The installation can be performed writhing the following lines in a terminal session (in the `RGESolver` directory):
```
mkdir build && cd $_
cmake ..
make
make install
```
Note that depending on the setting of installation prefix (see below) the user might need root privileges to be able to install `RGESolver` (so the should use `sudo make install` instead of `make install`).
### Command line options for the installation
* `-DLOCAL_INSTALL:BOOL=<ON or OFF>` : to install `RGESolver` in the directory `build/install` (default: `OFF`).
* `-DCMAKE_INSTALL_PREFIX:PATH=<RGESolver installation directory>` : the directory in which `RGESolver`	will be installed (default: `/usr/local`). This variable cannot be modified when `-DLOCAL INSTALL ALL=ON` is set.
* `-DDEBUG_MODE:BOOL=<ON or OFF>` : to enable the debug mode (default: `OFF`).
* `-DBOOST_INCLUDE_DIR:PATH=<include path>/boost/` : `CMake`checks for `BOOST` headers availability in the system and fails if they are not installed. Thus, if  `BOOST` is not installed 	in the predefined search path, the user can specify where it is with this option. The path must end with the `boost/`directory which contains the headers.
* `-DGSL_CONFIG_DIR:PATH=<gsl-config directory>` :  `RGESolver` uses `gsl-config` to get the `GSL` parameters. If this is not in the predefined search path, the user can specify it with this option.

## Compiling a program that uses `RGESolver` 
 After the installation, the example program `ExampleProgram.cpp` (available in the `Example Program` directory) can be compiled with the command 
 ```
 g++ -o app ExampleProgram.cpp -lRGESolver -lgsl -lgslcblas
 ```
 Mac users might need to add the flag `-std=c++11` (or greater).  
 
 If the `RGESolver` library is not in the predefined search path (and usually is the case for local installation), it may be necessary to specify the path needed for compilation and linking against `RGESolver`. A `rgesolver-config` script is available in the `<CMAKE_INSTALL_PREFIX>/bin` directory, which can be invoked with the following options:
* `--cflags`: to obtain the include path needed for compilation against the `RGESolver`.
* `--libs`:  to obtain the flags needed for linking against the `RGESolver`.

## Uninstall `RGESolver` 
The user can uninstall the library typing in a terminal session in the `build` directory:
 ```
(sudo) make uninstall
 ```

