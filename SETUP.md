# 本地运行

## 准备
- Node.js 20+
- Chrome（预览/导出）
- Python（音频分析）
- **自备** `song/song.wav` 与 `song/song.lrc`（仓库不含音频/歌词）

## 安装与生成数据
```bash
cd code
npm install
python tools/analyze_audio.py
node tools/fill_lyrics.mjs
```

## 预览
```bash
node export/server.mjs
```

导出脚本、QA 与场景说明见 `code/README-engine.md`。
