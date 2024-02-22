Set up GCC
==========

[![Test](https://github.com/LRGH/setup-gcc/actions/workflows/test.yml/badge.svg)](https://github.com/LRGH/setup-gcc/actions/workflows/test.yml)

This GitHub action sets up a specific version of GCC as the default compiler in your workflow.

1. Installs both `gcc` and `g++`, with multilib support for `gcc`
2. Can also be used to install Cygwin (work in progress), as an alternative to egor-tensin action [setup-cygwin]
3. For installing GCC on Windows please see egor-tensin action [setup-mingw].

[setup-cygwin]: https://github.com/egor-tensin/setup-cygwin

[setup-mingw]: https://github.com/egor-tensin/setup-mingw

Use it in your workflow like this:

    - name: Set up GCC
      uses: LRGH/setup-gcc@v2
      with:
        version: 7

API
---

| Input     | Value   | Default | Description
| --------- | ------- | ------- | -----------
| version   | latest  | ✓       | Install the latest version available in the repository.
|           | *any*   |         | Install a specific version if it's available (see below).
| platform  | x64     | ✓       | Install the x86_64 toolchain.
|           | *any*   |         | Install the i686 toolchain.
| cygwin    | *any*   | ✓       | Install native binaries.
|           | 1       |         | Install Cygwin packages.
| cc        | 1       | ✓       | Set up `cc`/`gcc`/`c++`/`g++` executables.
|           | *any*   |         | Don't set up the executables.
| hardlinks | *any*   | ✓       | Cygwin: don't convert any symlinks.
|           | 1       |         | Cygwin: convert symlinks in /usr/bin to hardlinks.

Supported versions
------------------

Differing from the original action by egor-tensin [setup-gcc], we don't rely on what is made available in Ubuntu's PPA, because most old versions of gcc are missing.
Packages are manually installed.

[setup-gcc]: https://github.com/egor-tensin/setup-gcc

Available versions are:

| `version` |  20.04 | 22.04
| --------- |  ----- | -----
| 4.4       |  ✓     |
| 4.6       |  ✓     |
| 4.8       |  ✓     | ✓
| 5         |  ✓     | ✓
| 6         |  ✓     | ✓
| 7         |  ✓     | ✓
| 8         |  ✓     |
| 9         |  ✓     | ✓
| 10        |  ✓     | ✓
| 11        |  ✓     | ✓
| 12        |        | ✓
| 13        |        | ✓

License
-------

Distributed under the MIT License.
See [LICENSE.txt] for details.

[LICENSE.txt]: LICENSE.txt
