Some binaries used for our GitHub Actions jobs.

Build and package Doxygen
=========================

::

    export DOXYGEN_VERSION=1.9.3
    wget https://www.doxygen.nl/files/doxygen-${DOXYGEN_VERSION}.src.tar.gz -O - | tar -xz
    cd doxygen-${DOXYGEN_VERSION}
    mkdir build
    cd build
    cmake -G Ninja -DCMAKE_BUILD_TYPE=Release ..
    ninja
    cd bin
    tar -cz doxygen -f ~/Desktop/doxygen.${DOXYGEN_VERSION}.linux.tar.gz

Build and package LLVM+Clang
============================

::

    export LLVMCLANG_MAJOR_VERSION=14
    export LLVMCLANG_VERSION=${LLVMCLANG_MAJOR_VERSION}.0.5
    wget https://github.com/llvm/llvm-project/archive/refs/tags/llvmorg-${LLVMCLANG_VERSION}.tar.gz -O - | tar -xz
    cd llvm-project-llvmorg-${LLVMCLANG_VERSION}
    mkdir build
    cd build
    cmake -G Ninja -DCMAKE_BUILD_TYPE=Release -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra" -DLLVM_TARGETS_TO_BUILD=X86 ../llvm
    ninja
    cd bin
    \rm clang
    cp -p clang-${LLVMCLANG_MAJOR_VERSION} clang
    tar -cz clang -f ~/Desktop/clang.${LLVMCLANG_VERSION}.linux.tar.gz
    tar -cz clang-format -f ~/Desktop/clang-format.${LLVMCLANG_VERSION}.linux.tar.gz
    tar -cz clang-tidy -f ~/Desktop/clang-tidy.${LLVMCLANG_VERSION}.linux.tar.gz
    cd ../lib/clang/${LLVMCLANG_VERSION}
    tar -cz . -f ~/Desktop/clang-include.${LLVMCLANG_VERSION}.linux.tar.gz
