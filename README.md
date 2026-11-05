# world.execute(me); — DeepSeek 鲸鱼娘 · DSH 特别版

> 非官方同人 MV · 代码逐帧渲染 · 4K60
> 3 分 37 秒，没有剪辑、没有视频素材、没有手绘：每一帧只由歌曲时间决定。

![封面](screenshots/cover_16x9.jpg)

## 观看 / 下载

> 上传前把下面三个 `REPLACE_ME` / `YOUR_NAME` 换成你自己的链接（见 UPLOAD.md）。

- B 站：`https://www.bilibili.com/video/REPLACE_ME`
- 抖音：`https://www.douyin.com/video/REPLACE_ME`
- GitHub Releases：`https://github.com/YOUR_NAME/world-execute-me-deepseek-whale-mv/releases/tag/v4`

## 它是什么

以 Mili《world.execute(me);》为音乐、DeepSeek 鲸鱼娘与 DSH 为主题的**非官方同人 MV**。
画面由一套基于 DSH 的同人 MV 引擎逐帧绘制，再经 Chrome 导出、Node 收集原始帧、ffmpeg 封装成片。
全片 **13,017 帧 / 3840×2160 / 60fps / 3:36.95**。

| 开场 | 人格加载 |
| --- | --- |
| ![开场](screenshots/01_opening_logo.jpg) | ![人格加载](screenshots/02_persona_load.jpg) |
| **插件安装面板** | **记忆相册** |
| ![插件面板](screenshots/03_plugin_panel.jpg) | ![相册](screenshots/04_memory_album.jpg) |
| **配置 diff** | **未发送草稿** |
| ![diff](screenshots/05_config_diff.jpg) | ![草稿](screenshots/06_unsent_drafts.jpg) |
| **新角色（2:08 / 3:04）** | **鲸落结尾** |
| ![新角色](screenshots/07_new_character.jpg) | ![结尾](screenshots/08_whale_fall.jpg) |

## 特色

- **官方 DeepSeek 鲸鱼 logo**：官方 mark 的矢量路径重绘，替换手绘卡通鲸，全片图标、开场、结尾统一
- **深海开场 + 鲸落结尾**：电力线、海雪、声呐环
- **六个叠加段落**：`persona.load` 人格加载 / 插件安装面板 / 记忆相册 / 五句未发送草稿 / 配置 diff / 末句「谁来陪我」
- **三墨视觉**：cream / blue / deep 三色平涂 + 网点；`f_ref` 为参考图重制的右侧人物
- **逐帧确定性**：没有剪辑时间线，任意一帧只由 `t` 决定

## 制作方式

完整交互式架构图：[docs/architecture.html](docs/architecture.html)（开启 GitHub Pages 后可直接在线看）。

```
素材/脚本 → DSH MV 引擎 → 导出页面（Chrome）→ WebSocket 原始 RGBA 帧
        → Node 渲染 harness（QA 静帧 → 自动 GO → 分块 NVENC）→ ffmpeg concat + 5s 静音封装
        → 4K60 母版 → QA（闪屏/音画偏移）→ 下采样 1080p60 / 720p30 / 竖版
```

## 版本

| 版本 | 规格 | 大小 | 说明 |
| --- | --- | --- | --- |
| 4K60 | 3840×2160 / 60fps / H.264 / AAC 320k | ~2.18 GB（原始）/ ~1.7 GiB（GitHub 版） | 主交付版 |
| 1080p60 | 1920×1080 / 60fps | 421 MB | 平台/播放友好 |
| 720p30 | 1280×720 / 30fps | 107 MB | 预览 |
| 竖版全片 | 1080×1920 / 30fps | 100 MB | 抖音 |
| 竖版预告 | 1080×1920 / 30fps / 35s | 14 MB | 引流 |
| 封面 | 1920×1080 / 1080×1920 | — | 16:9 与 9:16 |

## 工程结构

```
code/               引擎与场景源码（运行需自备音乐/歌词，见 code/SETUP.md）
docs/               交付说明、修改记录、授权与署名、QA、架构图
screenshots/        关键帧与封面
release/            Release 资产校验和
```

## 本地运行（源码）

见 [code/SETUP.md](code/SETUP.md)。简要：

```bash
cd code
npm install
# 把 song.wav / song.lrc 放进 code/song/，然后：
python tools/analyze_audio.py
node tools/fill_lyrics.mjs
node export/server.mjs
```

> 仓库不含 Mili 的音频与歌词（版权原因），也不含 `node_modules` 与渲染中间文件。

## QA（4K60 实测）

- 闪屏检查：一般闪 **2.0 次/秒**（上限 3）、红色闪 **0**、无单帧闪烁 → **PASS**
- 音画偏移：交叉相关峰值 **+5.000s**（片头 5 秒静音警告页为设计值）→ **PASS**
- 帧数/时长：**13017 帧 / 216.95 秒** → 与工程一致
- 详细报告：[docs/QA报告.md](docs/QA报告.md)

## 授权与署名

- **代码**：MIT（基于 [world.execute-me-lyric-mv](https://github.com/Nyankomintsu/world.execute-me-lyric-mv) 引擎）
- **文档 / 成片**：CC BY-NC-SA 4.0，**仅限非商业使用**
- **音乐**：Mili《world.execute(me);》，版权归 Mili；仓库**不含**音频与歌词
- **角色 / 图像素材**：CC BY-NC-SA 4.0，作者与来源见 [docs/授权与署名.md](docs/授权与署名.md)
- **DeepSeek logo**：DeepSeek 商标，本作为非官方同人使用，不代表官方
- **AI 内容**：画面由代码渲染；角色/图像素材含 AI 生成与社区二创。转载/发布请标注“含 AI 生成内容”

> 本仓库是一个 fan work。若权利方认为有不妥，请开 issue 联系，我会立即处理。

## 更新日志

- **v4**：31s 人格加载窗口按拍关闭
- **v3**：56s 晃动加强；1:30.27 插件面板按拍关闭；1:36 硬切改淡入叠化；2:08 / 3:04 右侧人物替换
- **v2**：官方 logo、去星芒改声呐环、深海开场、六段叠加（人格加载/插件/相册/草稿/diff/末句）、鲸落结尾
- **v1**：首版 DeepSeek 鲸鱼娘版

## 致谢

- [Mili](https://www.mili-music.com/) — 音乐
- [Nyankomintsu / world.execute-me-lyric-mv](https://github.com/Nyankomintsu/world.execute-me-lyric-mv) — 引擎
- [Iphsiibl / deepseek-whale-girl-gallery](https://github.com/Iphsiibl/deepseek-whale-girl-gallery) — 相册/参考立绘
- [OMGLogic / dsh-whale-persona](https://github.com/OMGLogic/dsh-whale-persona) — 人格标签
- 社区角色作者：ZipZipPipe、萌娘百科 Commons、十六夜猫咪QWQ 等（详见署名文件）

---

## English summary

An unofficial, non-commercial fan MV for Mili's *world.execute(me);*, starring a DeepSeek whale-girl in a DSH-themed interface.
Every frame is drawn by code (Canvas 2D + WebGL2) and exported at 3840×2160/60fps — 13,017 frames, 3:36.95.
Source code lives in `code/` (requires your own copy of the song and lyrics; not included). Content is licensed CC BY-NC-SA 4.0; code is MIT. See [NOTICE.md](NOTICE.md) for credits.
