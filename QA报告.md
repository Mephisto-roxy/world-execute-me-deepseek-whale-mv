# QA 报告 — v4

## 规格
- 4K60：3840×2160，60fps，13017 帧，216.95s

## 闪屏（tools/check_flash.py）
```
general: worst 1 s window = 2.0 flashes -> PASS (limit 3)
red:     0.0 flashes -> PASS (limit 3)
single-frame pops: none
```

## 音画同步（交叉相关）
```
mp4 audio 216.944s   wav 211.967s
audio-to-wav cross-correlation peak lag: +5.000 s (expected +5.000)
verdict: PASS
```
