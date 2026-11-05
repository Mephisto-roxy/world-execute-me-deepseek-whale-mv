# 制作框架图

交互式架构图：[architecture.html](architecture.html)（Archify architecture，深色主题，可直接 GitHub Pages 托管）。

## 它展示什么
- 输入：Mili 音频 + LRC、立绘与参考素材、人格与对话脚本、官方鲸鱼 logo
- 引擎：DSH MV 引擎（scenes / 叠加层 / 调色 / 三墨）
- 渲染链路：导出页面（Chrome）→ WebSocket 帧通道 → Node 渲染 harness → ffmpeg · NVENC
- 输出：4K60 母版 → QA 门禁（闪屏/音画偏移）→ 下采样与衍生（1080p60 / 720p30 / 竖版）→ 交付与发布包

## 开启 Pages
Settings → Pages → Deploy from a branch → `main` / `docs` 目录。
之后访问 `https://YOUR_NAME.github.io/world-execute-me-deepseek-whale-mv/architecture.html`。
