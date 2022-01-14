# bazel

## Define WORKSPACE file

`mkdir root-dir/`  
`touch root-dir/WORKSPACE` &larr; empty

## Define package directory

`mkdir root-dir/pkg-dir/`  
`touch root-dir/pkg-dir/src.cc`  
`touch root-dir/pkg-dir/BUILD`

## Content of BUILD file

```starlark
load("@rules_cc//cc:defs.bzl", "cc_binary")

cc_binary(
    name = "pkg-name",
    srcs = ["src.cc"],
)
```

## Build

`bazel build //pkg-dir:pkg-name`

## Run build

`bazel-bin/pkg-dir/pkg-name`

## Dependency graph

`bazel query --notool_deps --noimplicit_deps "deps(//pkg-dir:pkg-name)" --output graph`

## Add a dependency

`touch root-dir/pkg-dir/lib-src.cc`  
`touch root-dir/pkg-dir/lib.hdr.h`

## Update BUILD file

```starlark
load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library")

cc_library(
    name = "my-library",
    srcs = ["lib-src.cc"],
    hdrs = ["lib-hdr.h"],
)

cc_binary(
    name = "pkg-name",
    srcs = ["src.cc"],
    deps = [
        ":my-library",
    ],
)
```

## Add another package

`mkdir root-dir/pkg-dir_2/`  
`touch root-dir/pkg-dir_2/other-src.cc`  
`touch root-dir/pkg-dir_2/other-hdr.h`  
`touch root-dir/pkg-dir_2/BUILD` &larr; new BUILD file

## Content of _new_ BUILD file

```starlark
load("@rules_cc//cc:defs.bzl", "cc_library")

cc_library(
    name = "other-pkg",
    srcs = ["other-src.cc"],
    hdrs = ["other-hdr.h"],
    visibility = ["//pkg-dir:__pkg__"],
)
```

## Update _original_ BUILD file

Content of `root-dir/pkg-dir/BUILD`

```starlark
load("@rules_cc//cc:defs.bzl", "cc_binary", "cc_library")

cc_library(
    name = "my-library",
    srcs = ["lib-src.cc"],
    hdrs = ["lib-hdr.h"],
)

cc_binary(
    name = "pkg-name",
    srcs = ["src.cc"],
    deps = [
        ":my-library",
        "//pkg-dir_2:other-pkg",
    ],
)
```
