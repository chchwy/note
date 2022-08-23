---
---

## How to compile Godot

[[Godot]] 用的建構工具是 Scons。安裝 Scons:

```
pip install scons
```

編譯指令：
```shell
scons p=windows tools=no target=release_debug -j 8
```
 - p=(平台)
 - tools=yes/no 是否包含遊戲編輯器
 - target=debug/release/release_debug
 - j=(平行編譯數目)

產生 Visual Studio 專案
```shell
scons platform=windows vsproj=yes -j 8
```
