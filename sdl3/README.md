# SDL3 离线源码包

`SDL3-3.4.18.tar.gz` 是 SDL 3.4.18 官方发布源码包，供主仓库 `cmake/FindSDL3.cmake` 的
FetchContent 离线优先使用，避免每次配置都从 GitHub 下载（弱网/代理环境会因
HTTP2 framing 等问题随机失败）。

- 来源：https://github.com/libsdl-org/SDL/releases/download/release-3.4.18/SDL3-3.4.18.tar.gz
- SHA256：`9c75cf16330322c217dedd2e0609f1124f1b54b8633e763467b4684d0f4334a3`
  （与 `cmake/FindSDL3.cmake` 中 `URL_HASH` 一致，篡改会被校验拒绝）
- 解包与编译仍由主仓库 FetchContent 完成（SDL_STATIC、X11 补丁等流程不变）；
  本目录只承担"离线下载源"角色。

升级 SDL 版本时：替换本文件，同步更新 `cmake/FindSDL3.cmake` 的 URL_HASH 与
`cmake/PatchSDL3X11.cmake` 的适配性。
