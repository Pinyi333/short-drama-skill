---
title: <劇名>
stage: ai_prompts
version: 1
language: zh-TW
episode: <1>
based_on: [05-storyboard-ep01.md, 02-characters.md]
target_tool: <未指定／使用者指定的工具名稱>
changelog:
  - v1 初版
---

# <劇名>｜第 <1> 集 AI 生成提示詞

撰寫規則見 `references/ai-video-prompting.md`。

**用法**：表格中的 `[代號]` 是佔位符，送進工具前換成錨點全文，一字不改。

## 1. 角色錨點與定裝圖

### <代號>

**錨點**

```
[<代號>] = 
```

**定裝圖提示詞**

| 視角 | 提示詞 |
|------|--------|
| 正面 | `[<代號>], front view, neutral expression, plain studio background, full lighting, photorealistic, vertical 9:16` |
| 側面 | `[<代號>], side profile view, ...` |
| 全身 | `[<代號>], full body shot, standing, ...` |

<!-- 每個主要角色一組；換裝另建 <代號>_<服裝> -->

### 場景錨點

```
[<場景代號>] = <地點類型>, <2–4 個固定陳設>, <主光線與時段>
```

<!-- 每個反覆出現的地點一組 -->

## 2. 逐鏡影片提示詞

**通用風格**：`cinematic, photorealistic, shallow depth of field, film grain, vertical 9:16`

**通用負面提示詞**：`deformed hands, extra fingers, distorted face, inconsistent clothing, text, watermark, subtitles, blurry, horizontal frame`

| 鏡號 | 方式 | 起始圖 | 秒 | 提示詞 | 後製文字 |
|------|------|--------|----|--------|----------|
| 1 | 圖生影片 | <代號>.front | 3 | | |
| 2 | 文生影片 | — | | | |
| 3 | 圖生影片 | 鏡 2 末格 | | | |

<!--
方式：圖生影片（有主要角色）／文生影片（空鏡、環境）／文生圖＋圖生影片（物件特寫、多人互動）
起始圖：<代號>.front／.side／.full_body，或「鏡 N 末格」
-->

## 3. 配音

### 聲線設定

| 代號 | 聲線 |
|------|------|
| | `voice: ` |

### 逐句台詞

| 鏡號 | 角色 | 台詞 | 情緒 | 強度（1–5） |
|------|------|------|------|-------------|
| | | | | |

## 4. 音效與配樂

| 鏡號 | 類型 | 描述 |
|------|------|------|
| | SFX／BGM／HIT | |

## 自檢結果

| 項目 | 結果 | 備註 |
|------|------|------|
| | | |
