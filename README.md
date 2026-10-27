# DianaApi SDK

[English](README.md) | [中文](README.cn.md)

Standalone repository for the Siasun Diana C/C++ SDK. The current contents are the **3.3.0** C/C++ package used by this examples repository. The main examples repository references this repository as a Git submodule.

Before publishing or sharing this repository, confirm that the vendor SDK license allows the target private repository to store and distribute the SDK binaries, headers, and retained PDF documentation.

To upgrade the SDK, replace the C/C++ contents of `include/`, `lib/`, `doc/`, and `version`, then commit with the SDK version number. Keep `doc/` limited to documentation that should ship with this C/C++ examples repository, and do not add nested version directories.

```text
diana_sdk_cpp/
├── include/
│   ├── DianaAPI.h
│   ├── DianaAPIDef.h
│   └── ...
├── lib/
│   ├── libDianaApi.so
│   ├── libToolSdk.so
│   ├── libBasicSdk.so
│   └── libGenericAlgorithm.so
├── doc/
│   └── Siasun Diana industrial robot API manual (C/C++ edition)
└── version
```

When used as a submodule from the main examples repository, `DIANA_SDK_DIR` does not need to be specified; CMake looks for the SDK here by default. If an external SDK is used instead, pass its root directory:

```bash
cmake -S . -B build -DDIANA_SDK_DIR=/opt/diana_sdk_cpp
```

Before running executables from the main examples repository, make the dynamic linker able to find all SDK dependencies in `lib/`:

```bash
export LD_LIBRARY_PATH="$PWD/third_party/diana_sdk_cpp/lib:$LD_LIBRARY_PATH"
```
