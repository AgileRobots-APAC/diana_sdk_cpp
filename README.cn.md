# DianaApi SDK

[English](README.md) | [中文](README.cn.md)

思灵机器人 Diana C/C++ SDK 的独立仓库。当前内容为主 examples 仓库使用的 **3.4.0** C/C++ 包；主 examples 仓库会以 Git submodule 的形式引用本仓库。

发布或共享本仓库前，请确认厂商 SDK 许可允许在目标私有仓库中保存和分发二进制、头文件及保留的 PDF 文档。

需要升级 SDK 时，直接替换 `include/`、`lib/`、`doc/` 和 `version` 中的 C/C++ 内容，并以 SDK 版本号提交；`doc/` 只保留应随本 C/C++ examples 仓库发布的文档，不要再增加版本子目录。

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
│   └── 思灵机器人工业版API手册（C&C++版）
└── version
```

在 examples 主仓库中以子模块形式使用时，无需指定 `DIANA_SDK_DIR`；CMake 默认会在这里查找 SDK。若使用外部 SDK，则传入其根目录：

```bash
cmake -S . -B build -DDIANA_SDK_DIR=/opt/diana_sdk_cpp
```

运行可执行文件前，还需要使动态链接器能找到 `lib/` 中的全部 SDK 依赖：

```bash
export LD_LIBRARY_PATH="$PWD/third_party/diana_sdk_cpp/lib:$LD_LIBRARY_PATH"
```
