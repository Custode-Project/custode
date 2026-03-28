# Custodes 

Custodes is a modern, blazingly-fast SDC library with sensible defaults built to last. 

## Dependencies

Custodes requires C++17, git (unless downloading the source manually), [CMake](https://cmake.org/download/) version 3.28 or higher, [Doxygen](https://www.doxygen.nl/download.html) for documentation, and a [CMake supported build system](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html#manual:cmake-generators(7)) (we recommend [Ninja](https://github.com/ninja-build/ninja/releases) for this.)

### Windows

As Windows lacks a consistent package manager, install the dependencies via the links above.

### Pacman

``` shell
pacman -S gcc git cmake doxygen ninja 
```

### APT

```shell
apt update
apt install g++ git cmake doxygen ninja-build
```

### DNF

```shell
dnf install gcc-c++ git cmake doxygen ninja-build
```

### Homebrew

```shell
brew install clang git cmake doxygen ninja
```

## Building

To clone and build with Ninja:
```shell
git clone https://github.com/Custodes-Project/custodes.git --depth=1
cd custodes
cmake -S . -B ./build -G "Ninja Multi-Config"
```

To build the main lib:
```shell
cmake --build ./build
```

To build the docs:
```shell
cmake --build ./build --target=docs
```

You can also specify the build configuration as Debug, Release, MinSizeRel, RelWithDebInfo:
```shell
cmake --build ./build --config=Release
```

To include the GTest suite set the `CSDC_BUILD_TESTING` flag (default is OFF):
```shell
cmake -S . -B ./build -G "Ninja Multi-Config" -DCSDC_BUILD_TESTING=ON
```