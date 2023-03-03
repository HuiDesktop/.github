# HuiDesktop

[desktop.huix.cc](https://desktop.huix.cc)

高拓展性、高性能的桌宠喵~ 还能当壁纸引擎啥的用~

~~关键词~~  `C` `OpenGL` `Lua` `C#`(HDTLPanel)

开发交流：QQ群762939884

## Current status

已发行版本的代号：Light

* [LightBuild](https://github.com/HuiDesktop/LightBuild) 项目所需C DLL的一键编译，hdt-raylib-spine, HuIPC等作为其submodule
* [HDTLPanel](https://github.com/HuiDesktop/HDTLPanel) 设置面板，通过IPC和Lua端通信
* [HDTL-LuaRoot](https://github.com/HuiDesktop/HDTL-LuaRoot) Lua包（？），包含下面两个库的共同代码
* [HDTL-Arknights](https://github.com/HuiDesktop/HDTL-Arknights), [HDTL-Azurlane](https://github.com/HuiDesktop/HDTL-Azurlane) 上面仓库的fork，明日方舟模块和碧蓝航线模块的特殊逻辑
* [hdt-raylib-spine](https://github.com/HuiDesktop/hdt-raylib-spine) 给HuiDesktop用的Spine渲染器，但是改改也能直接给raylib-based的项目用
* [HuIPC](https://github.com/HuiDesktop/HuIPC) 简简单单IPC，用于HDTLPanel和Lua通信

## Cross-platform

已发布版本中，这些东西是Windows only的：

* HuIPC: 使用的Windows的Shared memory
* HDTLPanel: 毕竟是WPF写的，不支持Linux
* HDTL-LuaRoot: `lua/win32`下的API，很少（如检测是否有窗口全屏等），不影响主体运行

## Next

### Structure（预览）

* LuaJIT: 脚本引擎，桌宠的逻辑核心
* OpenGL/raylib(C Lib): 渲染核心
* Qt(?): 运行时配置窗口
* WebView2(?): 启动器、配置器

### Features

所有二进制使用C/Rust/...暴露C API给LuaJIT，所有的桌宠相关逻辑和渲染在Lua脚本中完成，LuaJIT使用Socket/pipe/Shared memory和其他的独立进程通讯（如配置窗口）

Lua脚本使用ECS（Entity, Component, System），便于合到一起

使用纯文本的配置文件进行逻辑组装（做不到就写一个Lua库）

### Plan

- [ ] 完成对Lua脚本的同构（ECS）
- [ ] 检查二进制的跨平台支持
- [ ] 跨平台的HDTLPanel（计划使用Qt？）
- [ ] 编辑器（组合ECS模块、编辑配置文件）
