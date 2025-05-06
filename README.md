This aims to have everything one needs to build file on Windows with VS+CMake

## Checkout with submodules

```sh
git submodule update --init --recursive
```

## External Dependencies

- *pcre2*:  through `vcpkg` installed globally. 
- *dirent*: Dirent is not available on windows, so I used a implementation from [tronkko](https://github.com/tronkko/dirent).
- *getopt*: A similar problem exists with getopt, so I used a implementation from [skandhurkat](https://github.com/skandhurkat/Getopt-for-Visual-Studio).

## Linking

- all the dependencies are statically linked or compiled into the dll
- There is a `.def` file in windows headers describing the exports for the linker
- Since dirent defines some of the symbols used in files `readelf.c` and `magic.c` the include is "patched" into them in the `CMakeLists.txt`
