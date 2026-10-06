# JSON 結構化輸出

使用者要求 JSON、或要把成品接到其他程式（排程、生成管線、資料庫）時，使用以下結構。欄位名稱固定用英文 snake_case，內容可用任何語言。未定的值填 `null`，不要省略欄位。

## 共用中繼資料

每個成品最外層都有 `meta`：

```json
{
  "meta": {
    "title": "劇名",
    "stage": "series_bible | characters | outline | script | storyboard | ai_prompts",
    "version": 1,
    "language": "zh-TW",
    "based_on": ["01-series-bible.md"],
    "changelog": ["v1 初版"]
  }
}
```

## 企劃書（series_bible）

```json
{
  "meta": {},
  "requirements": {
    "genre": ["重生", "霸總"],
    "audience": "女頻",
    "episodes": 60,
    "episode_seconds": 90,
    "aspect_ratio": "9:16",
    "production": "ai | live_action | hybrid",
    "assumptions": ["未指定集數，採預設 60 集"]
  },
  "logline": "",
  "selling_points": [""],
  "core_payoff_types": ["身分揭露", "打臉反轉"],
  "acts": [
    { "name": "第一幕", "episodes": [1, 10], "goal": "" }
  ],
  "paywall_episodes": [10, 25, 40],
  "world": { "setting": "", "rules": [""], "taboos": [""] }
}
```

## 角色表（characters）

```json
{
  "meta": {},
  "characters": [
    {
      "id": "LIN_YAN",
      "name": "林嫣",
      "role": "protagonist | antagonist | love_interest | support",
      "age": 26,
      "appearance": "",
      "visual_anchor": "26-year-old East Asian woman, ...",
      "public_identity": "",
      "hidden_identity": "",
      "reveal_episode": 18,
      "desire": "",
      "fear": "",
      "arc": "",
      "speech_style": "",
      "catchphrase": "",
      "voice": "female, mid-20s, clear and cold, medium pace"
    }
  ],
  "relationships": [
    { "a": "LIN_YAN", "b": "GU_CHEN", "type": "契約夫妻", "tension": "" }
  ]
}
```

## 分集大綱（outline）

```json
{
  "meta": {},
  "episodes": [
    {
      "ep": 1,
      "title": "",
      "opening_hook": "",
      "events": "",
      "payoff": "",
      "twist": null,
      "ending_hook": "",
      "emotion": -3,
      "paywall": false
    }
  ]
}
```

## 劇本（script）

```json
{
  "meta": {},
  "ep": 1,
  "estimated_seconds": 92,
  "scenes": [
    {
      "scene": 1,
      "int_ext": "內",
      "location": "飯店大廳",
      "time": "夜",
      "beats": [
        { "type": "action", "text": "" },
        { "type": "dialogue", "character": "LIN_YAN", "direction": "冷笑", "text": "" },
        { "type": "marker", "text": "爽點" }
      ]
    }
  ]
}
```

`beats.type` 可為 `action`、`dialogue`、`vo`、`marker`。

## 分鏡（storyboard）

```json
{
  "meta": {},
  "ep": 1,
  "total_seconds": 90,
  "shots": [
    {
      "shot": 1,
      "scene": 1,
      "seconds": 3,
      "size": "CU",
      "angle": "low angle",
      "movement": "push in",
      "content": "",
      "characters": ["LIN_YAN"],
      "dialogue": null,
      "sound": "HIT: 巴掌聲",
      "caption": null,
      "transition": "cut",
      "notes": ""
    }
  ]
}
```

## AI 提示詞（ai_prompts）

```json
{
  "meta": {},
  "ep": 1,
  "character_anchors": [
    { "id": "LIN_YAN", "anchor": "", "reference_prompts": { "front": "", "side": "", "full_body": "" } }
  ],
  "shots": [
    {
      "shot": 1,
      "mode": "image_to_video | text_to_video",
      "start_frame": "LIN_YAN.front | prev_shot_last_frame | null",
      "prompt": "",
      "negative_prompt": "",
      "seconds": 3,
      "aspect_ratio": "9:16",
      "post_text": null
    }
  ],
  "voice_lines": [
    { "shot": 1, "character": "LIN_YAN", "line": "", "emotion": "冷笑", "intensity": 3 }
  ]
}
```
