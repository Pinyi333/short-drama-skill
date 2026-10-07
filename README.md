# Short Drama Skill｜AI 短劇創作 Skill

一個開源的 Claude Agent Skill，用多階段工作流把一個點子變成可拍攝、可交給 AI 生成的竪屏短劇。

An open-source Claude Agent Skill that turns an idea into a production-ready vertical short drama (micro drama) through a staged workflow with structured outputs.

## 功能

- **七階段工作流**：需求釐清 → 企劃書 → 角色表 → 分集大綱 → 劇本 → 分鏡 → AI 生成提示詞，每階段附品質自檢
- **結構化輸出**：每個階段有固定模板（Markdown），也可輸出 JSON 接入生成管線
- **短劇專屬節奏規則**：前 3 秒鉤子、每集爽點、集尾懸念、付費卡點、情緒曲線
- **AI 生成友善**：角色視覺錨點維持一致性，逐鏡產出影片、圖像、配音提示詞
- **可從任一階段切入**：已有劇本可直接做分鏡，已有分鏡可直接轉提示詞

## 目錄結構

```
short-drama-skill/
├── SKILL.md                     # Skill 入口：觸發詞、工作流、輸出規範
├── references/
│   ├── workflow.md              # 各階段詳細步驟與切入點判斷
│   ├── genre-tropes.md          # 題材、爽點類型、反轉橋段
│   ├── pacing-rules.md          # 單集節奏、情緒曲線、付費卡點
│   ├── shot-vocabulary.md       # 景別、角度、運鏡、轉場（中英對照）
│   ├── ai-video-prompting.md    # AI 影像／影片／配音提示詞規則
│   ├── quality-checklist.md     # 各階段自檢清單
│   └── output-schema.md         # JSON 結構化輸出格式
└── templates/
    ├── series-bible.md          # 企劃書
    ├── character-sheet.md       # 角色表
    ├── episode-outline.md       # 分集大綱
    ├── script.md                # 劇本
    ├── storyboard.md            # 分鏡表
    └── ai-prompts.md            # AI 生成提示詞
```

## 安裝

### Claude Code

```bash
# 個人使用
git clone https://github.com/Pinyi333/short-drama-skill.git ~/.claude/skills/short-drama-tw

# 或放在專案內，與團隊共用
git clone https://github.com/Pinyi333/short-drama-skill.git .claude/skills/short-drama-tw
```

### Claude.ai／Claude 桌面版

將整個資料夾壓縮成 zip，在「設定 → Capabilities → Skills」上傳。

## 使用範例

安裝後直接用自然語言描述需求，Skill 會自動觸發：

```
幫我寫一部重生復仇題材的短劇，60 集，每集 90 秒，要用 AI 生成。
```

```
這是我第 3 集的劇本，幫我做分鏡，再轉成 AI 影片提示詞。
```

```
檢查這份分集大綱的節奏和付費卡點。
```

```
Write a 30-episode billionaire romance micro drama, output as JSON.
```

## 輸出檔案命名

| 階段 | 檔名 |
|------|------|
| 企劃書 | `01-series-bible.md` |
| 角色表 | `02-characters.md` |
| 分集大綱 | `03-outline.md` |
| 劇本 | `04-script-ep01.md` |
| 分鏡 | `05-storyboard-ep01.md` |
| AI 提示詞 | `06-ai-prompts-ep01.md` |

## 設計原則

- `SKILL.md` 控制在 500 行內，細節放在 `references/`，需要時才載入，節省上下文。
- 下游階段只讀上游成品，不依賴對話記錄，因此可以中斷、修改、換人接手。
- 不綁定特定 AI 影片模型；使用者指定工具時再依其格式調整。

## 貢獻

歡迎提交 Issue 與 Pull Request，特別是：

- 新的題材與反轉橋段
- 各 AI 影片工具的提示詞格式適配
- 其他語言（簡體中文、英文、日文、韓文）的模板
- 完整的範例作品

## 授權

[MIT License](LICENSE)

## 聲明

本專案為社群開源專案，與 Anthropic 無隸屬或合作關係，亦未獲其背書。Claude、Claude Code 為 Anthropic 的商標，文中提及僅為說明相容的使用環境。

This is an independent community project and is not affiliated with or endorsed by Anthropic. Claude and Claude Code are trademarks of Anthropic, mentioned only to describe compatibility.
