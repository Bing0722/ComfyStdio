# ComfyStdio

ComfyStdio 是一个 ComfyUI 桌面启动器项目，计划支持实例启动与日志、模型下载与管理、网络代理以及自定义节点安装。

## 多语言实现

当前优先开发 **Electron + React**，开发目录为 `implementations/electron-react/`。当前 Electron 版本为 0.8.1，按一个 ComfyUI 工作目录组织运行与资产。支持真实启动、启动设置恢复、运行日志、官方源码与 Windows 便携版获取、软件更新检查及文件夹便携包；模拟功能已移除，尚未接入的资产修改仅展示真实读取结果。 [Electron 开发说明](https://github.com/Bing0722/ComfyStdio-electron-react#本地开发)

每次改动完成后，在对应仓库本地提交并推送。 [协作规范](AGENTS.md)

三个实现各有独立仓库，通过 Git submodule 挂到这里。各版本可以独立构建、运行、测试和提交。主仓库记录各子仓库用于对比测试的具体提交。

| 实现 | 目录 | 仓库 |
| --- | --- | --- |
| Rust + GPUI | `implementations/rust-gpui/` | [ComfyStdio-rust-gpui](https://github.com/Bing0722/ComfyStdio-rust-gpui) |
| C++ + Qt | `implementations/cpp-qt/` | [ComfyStdio-cpp-qt](https://github.com/Bing0722/ComfyStdio-cpp-qt) |
| Electron + React | `implementations/electron-react/` | [ComfyStdio-electron-react](https://github.com/Bing0722/ComfyStdio-electron-react) |

同时获取三个实现时，递归克隆主仓库。

```sh
git clone --recurse-submodules https://github.com/Bing0722/ComfyStdio.git
```

已有主仓库时，先拉取最新的 `main`，然后运行 `git submodule update --init --recursive`。只开发一个版本时，可以直接克隆对应子仓库，也可以在主仓库内进入该子模块后从当前提交创建开发分支。从主仓库开发时，先提交并推送子仓库，再提交并推送主仓库中的子模块指针。

完成真实接入后，不同实现可用同一套手工验收场景做横向对比，包括读取已有 ComfyUI、启动并查看日志、经代理下载模型并在 ComfyUI 中识别、向当前 ComfyUI 安装自定义节点。测试时使用各自的实例和配置目录，避免相互影响。
