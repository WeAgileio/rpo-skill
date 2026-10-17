# rpo-skill

給 PO（Product Owner，產品負責人）使用的 AI 技能集合，將問題探索、需求整理、優先排序與交付協作中的常用做法，整理成可重複使用的 Agent Skills。

每個技能聚焦一個工作情境，可以依需要個別安裝。內容以繁體中文為主，適合與 AI 一起釐清問題、整理資訊、做出決策並推進產品工作。

## 已收錄技能

目前收錄 **1 個技能**，後續可持續擴充。

| 技能 | 識別名稱 | 適用情境 | 主要產出 |
|---|---|---|---|
| [探索問題](skills/explore-problems/README.md) | `explore-problems` | 想法還很模糊、不確定問題出在哪，或需要先釐清真正要解決什麼 | 問題定義、事實與假設、待確認事項、下一步驗證方向 |

## PO 工作情境與擴充方向

以下是技能集合的擴充方向；除了「探索問題」，其餘技能尚未收錄。

| 工作情境 | 可加入的技能方向 |
|---|---|
| 問題探索與產品發現 | 問題釐清、訪談準備、使用者回饋整理、機會辨識 |
| 需求與範圍管理 | 需求拆解、User Story、驗收條件、PRD、範圍取捨 |
| 價值判斷與優先排序 | 價值評估、假設排序、Backlog 整理、產品路線圖 |
| 團隊協作與交付 | Sprint 準備、依賴整理、利害關係人溝通、交付風險盤點 |
| 驗收與成效追蹤 | 測試情境、成果驗收、指標定義、實驗設計與回顧 |
| 持續改善 | Retrospective、流程問題整理、產品決策紀錄 |

## 安裝

選擇需要的技能，將 `skills/<技能識別名稱>/` 整個目錄複製到使用工具的技能目錄。保留目錄內的 `SKILL.md`、`agents/` 與其他附帶資源。

### Codex 專案技能

以「探索問題」為例，在下載的儲存庫根目錄執行以下指令，並將 `/path/to/your-project` 換成你的專案路徑：

```bash
mkdir -p /path/to/your-project/.agents/skills
cp -R skills/explore-problems /path/to/your-project/.agents/skills/
```

安裝後，技能檔案應位於：

```text
你的專案/.agents/skills/explore-problems/SKILL.md
```

### Claude Code 專案技能

將選定的技能目錄放到使用專案的 `.claude/skills/`。例如：

```text
你的專案/.claude/skills/explore-problems/SKILL.md
```

## 使用

安裝後可以直接描述工作情境，或指定要使用的技能。例如：

> 用探索問題幫我釐清：使用者常說流程很麻煩，但我還不知道真正卡在哪裡。

也可以在 Codex 中使用技能識別名稱：

```text
$explore-problems 先幫我想清楚要解決什麼，再討論做法。
```

個別技能的流程與範例，請參考該技能目錄內的說明。

## 儲存庫結構

```text
rpo-skill/
├── README.md
└── skills/
    └── explore-problems/
        ├── SKILL.md
        ├── README.md
        ├── agents/
        │   └── openai.yaml
        ├── grill-boss-icon.png
        └── social-preview.png
```

## 新增技能

1. 在 `skills/` 下建立獨立目錄，使用小寫英文與連字號命名。
2. 撰寫 `SKILL.md`，包含 `name`、`description`，以及適用情境、工作流程和預期產出。
3. 視需要加入 `agents/openai.yaml`、範例、參考資料或工具腳本。
4. 以實際工作情境確認技能能正確觸發、提問與產出，再將它加入上方「已收錄技能」表格。

技能應清楚區分事實、推論與假設，保留使用者的決策權，並在資訊不足時說明仍需確認的事項。

## 來源與致謝

「探索問題」改編自 [grill-boss 繁體中文原始版本](https://github.com/WeAgileio/rpo-skill/tree/b65446a97d55e95e2ad2dcd91bcb40d235ee43c3)，原始方法來自 [onlyLT/grill-boss](https://github.com/onlyLT/grill-boss)。此版本將情境延伸為通用問題探索，保留分輪提問、事實查證與假設清單等做法。

各技能的來源與改編說明，記錄在各自的目錄中。
