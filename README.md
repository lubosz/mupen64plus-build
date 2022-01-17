# Mupen64Plus for OpenDingux

This repository contains a build of mupen64plus for Ingenic JZ4770 based
retro gaming consoles running a 2022 version of [OpenDingux](https://github.com/opendingux/).

It is the resurrection of Nebuleon's [old repository](https://github.com/Nebuleon/mupen64plus-build),
rebasing on most recent Mupen64Plus upstream and making it build with most recent
OpenDingux, using GCC 11, where the old one used GCC 4.

Currently there are no performance or compatiblity advantages over the OPK from 2015 that can be found in various OPK repos.

## Cloning this repo

Since all the Mupen64Plus repos are git submodules, you need to clone this
repo with `--recursive`.

```
git clone --recursive https://github.com/lubosz/mupen64plus-build.git
```

If you somehow forget that, you can still fetch the submodules later via

```
git submodule update --init --depth 1 --recursive
```

## Build

### Setting up 2022 gcw0-toolchain

Make sure you have a 2022 gcw0-toolchain set up. You can build one with
OpenDingux's [buildroot](https://github.com/OpenDingux/buildroot).

In the `buildroot` directory, running

```
CONFIG=gcw0 ./rebuild.sh
```

This will create a toolchain tarball in `output/gcw0/images/opendingux-gcw0-toolchain.20XX-XX-XX.tar.xz`,
which you can extract wherever you want. `/opt/gcw0-toolchain/` is popular.

Before you start the build, make sure you add the toolchain to your path.

```
export PATH=/opt/gcw0-toolchain/usr/bin:$PATH
```

### Build the opk

To create `mupen64plus.opk`.

```
make -f Makefile.gcw0
```
