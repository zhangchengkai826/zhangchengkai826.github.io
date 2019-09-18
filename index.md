# Build LLVM from source on Windows

    git clone https://github.com/zhangchengkai826/zhangchengkai826.github.io.git
    cd llvm-project
    mkdir build
    cd build
    cmake -G Ninja -DCMAKE_INSTALL_PREFIX=(some path) -DCMAKE_BUILD_TYPE=RelWithDebInfo ..\llvm
    ninja
    ninja install