# cmake

## Build it

### Old CMake version

```bash
~/pkg $ mkdir build
~/pkg $ cd build
~/pkg/build $ cmake ..
~/pkg/build $ make
```

### New CMake version

```bash
~/pkg $ cmake -S . -B build
~/pkg $ cmake --build build
```

---

## Install it

### From build dir (pick one)

`~/pkg/build $ make install`  
or `~/pkg/build $ cmake --build . --target install`  
CMake 3.15+ only `~/pkg/build $ cmake --install .`

### From source dir (pick one)

`~/pkg $ make -C build install`  
or `~/pkg $ cmake --build build --target install`  
CMake 3.15+ only `~/pkg $ cmake --install build`

---

## Pick a compiler

`~/pkg/build $ CC=clang CXX=clang++ cmake ..`

## Pick a generator

Find a generator  
`~/pkg/build $ cmake --help`  
Pick with `-G "My Tool"`  
Env var `CMAKE_GENERATOR`  
Run in parallel `make -j2`  
or `cmake --build . -j2`

---

## Set options

List options `cmake -L`  
With human-readable help `cmake -LH`  
Set with `cmake -D .`

### Common options

`-DCMAKE_BUILD_TYPE=`  
Can be `Release`, `RelWithDebInfo`, `Debug`, etc.

Install location `-DCMAKE_INSTALL_PREFIX=`  
System install at `/usr/local`, otherwise `~/.local`

`-DBUILD_SHARED_LIBS=` as `ON` or `OFF`  
`-DBUILD_TESTING=` for testing.

---

## Debugging CMake

Tack on `--trace` (verbose)  
Or be specific `--trace-source="filename"`
