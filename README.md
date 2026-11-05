# ComfyStdio

ComfyStdio 是一个 ComfyUI 桌面启动器项目，计划支持实例启动与日志、模型下载与管理、网络代理以及自定义节点安装。

## 多语言实现

各实现放在 `implementations/` 下，独立构建、运行和测试，可以在同一个分支中并存。例如 `implementations/rust-gpui/`、`implementations/cpp-qt/` 和 `implementations/electron-vue/`。启动某个实现时再创建对应目录，并在目录内记录依赖、运行方式和平台要求。

不同实现可用同一套手工验收场景做横向对比，先覆盖导入已有实例、启动并查看日志、经代理下载模型并在 ComfyUI 中识别、向指定实例安装自定义节点。测试时使用各自的实例和配置目录，避免相互影响。
