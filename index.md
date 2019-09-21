# Compile C source code to LLVM IR code

```
clang.exe -cc1 -emit-llvm a.c
```

a.c

```
int main() {
    return 0;
}
```

a.ll

```
; ModuleID = 'a.c'
source_filename = "a.c"
target datalayout = "e-m:w-p270:32:32-p271:32:32-p272:64:64-i64:64-f80:128-n8:16:32:64-S128"
target triple = "x86_64-pc-windows-msvc"

; Function Attrs: noinline nounwind optnone
define dso_local i32 @main() #0 {
entry:
  %retval = alloca i32, align 4
  store i32 0, i32* %retval, align 4
  ret i32 0
}

attributes #0 = { noinline nounwind optnone "correctly-rounded-divide-sqrt-fp-math"="false" "disable-tail-calls"="false" "frame-pointer"="none" "less-precise-fpmad"="false" "min-legal-vector-width"="0" "no-infs-fp-math"="false" "no-jump-tables"="false" "no-nans-fp-math"="false" "no-signed-zeros-fp-math"="false" "no-trapping-math"="false" "stack-protector-buffer-size"="8" "target-features"="+cx8,+mmx,+sse,+sse2,+x87" "unsafe-fp-math"="false" "use-soft-float"="false" }

!llvm.module.flags = !{!0}
!llvm.ident = !{!1}

!0 = !{i32 1, !"wchar_size", i32 2}
!1 = !{!"clang version 10.0.0 (https://github.com/zhangchengkai826/llvm-project.git 250e7001e17083e6aeb42861c9efb5a23c76e953)"}
```

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