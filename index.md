# Build LLVM from source on Windows

```
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"
git clone https://github.com/zhangchengkai826/zhangchengkai826.github.io.git
cd llvm-project
mkdir build
cd build
```

To build core components only

```
cmake -G Ninja -DCMAKE_INSTALL_PREFIX=(some path) -DCMAKE_BUILD_TYPE=RelWithDebInfo ..\llvm
```

To build all components

```
cmake -G Ninja -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra;compiler-rt;debuginfo-tests;libc;libclc;libcxx;libcxxabi;libunwind;lld;lldb;openmp;parallel-libs;polly;pstl" -DCMAKE_INSTALL_PREFIX=(some path) -DCMAKE_BUILD_TYPE=RelWithDebInfo -DPYTHON_HOME=C:\Python27 -DPYTHON_DLL_PATH_OVERWRITE=C:\Windows\System32 ..\llvm
```

```
ninja
ninja install
```