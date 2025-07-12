This repository is used to build the various tools used by our GitHub Actions jobs on Ubuntu, which are:

- `Doxygen <https://doxygen.nl/>`__ (see `license <./LICENSE-Doxygen.txt>`__); and some
- `LLVM <https://llvm.org/>`__\ +\ `Clang <https://clang.llvm.org/>`__ tools (see `license <./LICENSE-LLVM+Clang.txt>`__).

These tools are automatically built and uploaded as artifacts upon pushing to this repository.
See `here <https://github.com/opencor/gha/blob/master/.github/workflows/cd.yml>`__ for the version of these tools.
