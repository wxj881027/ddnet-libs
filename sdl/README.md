# SDL3 预编译库

本目录存放客户端使用的 SDL3 预编译产物，构建期不再编译 SDL 源码。

## 布局

- `include/<平台>/SDL3/*.h`：随库分发的头文件（含构建期生成的 `SDL_build_config.h`）
- `windows/lib{64,32,arm64}/{SDL3.dll,SDL3.lib}`：Windows 动态库（x64 / x86 / arm64）
- `linux/lib64/{libSDL3.so.0,libSDL3.so}`：Linux 动态库（`.so.0` 是运行时 SONAME，`.so` 供链接）
- `android/lib{32,64,arm,arm64}/libSDL3.a`：Android 静态库
- `java/org/libsdl/app`：Android 绑定
- `VERSION`：当前预编译的 SDL3 版本

当前已产出：Windows x64/x86/arm64、Linux x64（含 `cmake/PatchSDL3X11.cmake` 的修复）、Android 四个 ABI。
待补：macOS、iOS、webasm 需要用对应工具链（Xcode / emsdk）在同一版本上生成。

## 重新生成

```bash
qmclient_scripts/build_sdl3_prebuilt.sh <SDL3 源码目录> windows linux android macos ios webasm
```

只生成当前平台切片时省略平台参数。Linux 切片建库前会自动打 X11 补丁；
预编译之后该补丁无处可打，必须在这一步带上。
