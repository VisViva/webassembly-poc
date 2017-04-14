## Web Assembly Poc

## Installing the Firefox Nightly

`cd`

`wget https://archive.mozilla.org/pub/firefox/nightly/latest-mozilla-central/firefox-53.0a1.en-US.linux-x86_64.tar.bz2`

`tar xf firefox-53.0a1.en-US.linux-i686.tar.bz2`

`cd firefox`

`./firefox`

## Ubuntu requirements

`sudo apt-get install git cmake make ninja-build`

## LLVM with WebAssembly support

`git clone http://llvm.org/git/llvm.git`

`cd llvm/tools`

`git clone http://llvm.org/git/clang.git`

`cd ../projects`

`git clone http://llvm.org/git/compiler-rt.git`

`cd ..`

`mkdir build`

`cd build`

`cmake -G Ninja -DLLVM_EXPERIMENTAL_TARGETS_TO_BUILD=WebAssembly ..`

`ninja`

`ninja install`

## Compiling Binaryen

`cd`

`git clone https://github.com/WebAssembly/binaryen`

`cd binaryen`

`cmake .`

`make`

`sudo make install`

## Installing the WebAssembly Binary Toolkit

`git clone https://github.com/WebAssembly/wabt.git`

`cd wabt`

`mkdir build`

`cd build`

`cmake -G Ninja -DBUILD_TESTS=OFF ..`

`ninja`

`sudo ninja install`

## Compiling the code

`clang -emit-llvm --target=wasm32 -S index.c`

`llc index.ll -march=wasm32`

`s2wasm index.s > index.wast`

`wast2wasm -o index.wasm index.wast`
