# ddnet-libs

Libraries for Linux, Windows and macOS are updated using [ddnet-lib-update.sh](https://github.com/ddnet/ddnet-scripts/blob/master/ddnet-lib-update.sh).

Libraries for Android and Emscripten (WebAssembly) are updated using [gen_libs.sh](https://github.com/ddnet/ddnet/blob/master/scripts/compile_libs/gen_libs.sh).

## WebP（QmClient 专用）

`webp/` 存放 libwebp v1.6.0（含 sharpyuv）的预编译产物，供 QmClient 的皮肤预览 WebP 缓存使用（上游 ddnet-libs 不包含该库）：

- `windows/lib64/`：MSVC 静态库（.lib）
- `android/{lib32,lib64,libarm,libarm64}/`：NDK 交叉编译的静态库（.a）
- `include/`：公共头文件

构建方式：libwebp v1.6.0，静态链接（`BUILD_SHARED_LIBS=OFF`），关闭全部工具程序（cwebp/dwebp/extras/gif2webp/img2webp/vwebp/webpinfo/webpmux/webp_js）。产出流程参考 QmClient 仓库 CI 中「Build WebP for Windows / Android」步骤的历史记录。
