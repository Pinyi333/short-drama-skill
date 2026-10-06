# AI 影像、影片與配音提示詞

本文件說明如何把分鏡轉成 AI 生成工具可用的提示詞。內容不綁定特定模型；使用者指定工具時，依該工具的官方格式與長度限制調整。

## 角色一致性

AI 短劇最常見的問題是同一角色每個鏡頭長得不一樣。處理方式：

1. **先做定裝圖**：每個主要角色產出一組「角色錨點」提示詞，生成正面、側面、全身三張參考圖。
2. **固定錨點關鍵詞**：從角色表抽出 5–8 個不會變的外型詞（髮型、髮色、臉型特徵、標誌配件、主要服裝），每次提到該角色都原封不動帶上。
3. **優先用圖生影片**：有角色出現的鏡頭，以定裝圖或前一鏡的最後一格作為起始圖。
4. **換裝要建新錨點**：角色換衣服時，另建一組錨點並在分鏡中標註。

### 角色錨點格式

```
[角色代號] = <年齡> <性別> <族裔>, <髮型與髮色>, <臉部特徵>, <服裝>, <標誌配件>
```

範例：

```
[LIN_YAN] = 26-year-old East Asian woman, shoulder-length straight black hair with side bangs,
small mole under left eye, white silk blouse, black tailored trousers, thin silver watch on left wrist
```

## 影片提示詞結構

每鏡依序填入，用逗號分隔：

```
<主體與錨點>, <動作>, <場景>, <景別>, <角度>, <運鏡>, <光線>, <風格>, <時長>, <畫幅>
```

| 欄位 | 寫法要點 |
|------|----------|
| 主體與錨點 | 直接貼上角色錨點 |
| 動作 | 一鏡一個主要動作，用具體動詞（slaps, turns around slowly, tears the contract） |
| 場景 | 地點＋2–3 個環境細節 |
| 景別／角度／運鏡 | 使用 `shot-vocabulary.md` 的英文用語 |
| 光線 | 一種主光線描述 |
| 風格 | 預設 `cinematic, photorealistic, shallow depth of field, film grain` |
| 時長 | 依分鏡秒數，多數工具單段 4–10 秒 |
| 畫幅 | 竪屏固定寫 `vertical 9:16` |

範例：

```
[LIN_YAN], raises her hand and slaps the man in front of her, luxury hotel lobby with marble floor
and crystal chandelier, medium close-up, low angle, slow push in, cool rim light, cinematic,
photorealistic, shallow depth of field, slow motion, 5 seconds, vertical 9:16
```

## 負面提示詞（若工具支援）

```
deformed hands, extra fingers, distorted face, inconsistent clothing, text, watermark,
subtitles, blurry, low quality, horizontal frame
```

## 文生影片與圖生影片的分工

| 鏡頭類型 | 建議方式 |
|----------|----------|
| 空鏡、環境、建立鏡頭 | 文生影片 |
| 有主要角色的鏡頭 | 圖生影片（起始圖用定裝圖或上一鏡末格） |
| 物件特寫（合約、戒指、手機畫面） | 文生圖＋圖生影片 |
| 多人互動 | 先生成構圖靜態圖，再圖生影片 |

## 配音提示詞

每個角色一組聲線設定，逐句對白附情緒標記：

```
[角色代號] voice: <性別>, <年齡感>, <音色>, <語速>, <口音>
台詞：「……」
情緒：<冷笑／哽咽／憤怒低吼／溫柔>，強度 <1–5>
```

## 字幕與文字

AI 影片模型生成的文字常出錯。畫面中需要出現文字（手機訊息、合約標題、招牌）時：

- 提示詞中寫 `no text`，後製再加上文字。
- 在分鏡表的「字幕」欄標註需要後製的文字內容。

## 權利與揭露

- 不要求模型模仿真實演員或公眾人物的長相或聲音。
- 提醒使用者依發布平台規定標示 AI 生成內容。
