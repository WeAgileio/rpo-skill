# rpo-skill

給 PO（Product Owner，產品負責人）使用的 AI 技能集合，將問題探索、需求整理、優先排序與交付協作中的常用做法，整理成可重複使用的 Agent Skills。

每個技能聚焦一個工作情境，可以依需要個別安裝。首頁以繁體中文整理，各技能保留原始語言，適合與 AI 一起釐清問題、整理資訊、做出決策並推進產品工作。

## 已收錄技能

目前收錄 **5 個技能**，後續可持續擴充。

| 技能 | 識別名稱 | 適用情境 | 主要產出 |
|---|---|---|---|
| [探索問題](skills/explore-problems/README.md) | `explore-problems` | 想法還很模糊、不確定問題出在哪，或需要先釐清真正要解決什麼 | 問題定義、事實與假設、待確認事項、下一步驗證方向 |
| [Handoff（對話交接）](skills/handoff/SKILL.md) | `handoff` | 準備換到新對話或交給另一個 agent，需要保留接續工作的脈絡 | 對話交接文件、既有產出的引用、下一階段重點與建議使用的技能 |
| [Market Segments（市場分群）](skills/market-segments/SKILL.md) | `market-segments` | 探索潛在市場、辨識目標客群，或評估產品適合服務哪些人 | 3–5 個客群的人口／企業特徵、JTBD、痛點、產品適配與競爭分析 |
| [新產品驗證實驗](skills/brainstorm-experiments-new/SKILL.md) | `brainstorm-experiments-new` | 驗證新產品構想、測試市場需求，或設計低成本的前型實驗（pretotype） | XYZ 假設、2–3 個實驗方案，以及各實驗的衡量指標與成功門檻 |
| [價值主張](skills/value-proposition/SKILL.md) | `value-proposition` | 釐清產品定位、目標顧客需求與替代方案的差異 | 七行價值主張及必要的假設與待驗證事項 |

## PO 工作情境與擴充方向

以下是技能集合的擴充方向；目前已提供的技能以「已收錄技能」表格為準。

| 工作情境 | 可加入的技能方向 |
|---|---|
| 問題探索與產品發現 | 問題釐清、訪談準備、使用者回饋整理、機會辨識 |
| 市場研究與客群理解 | 市場分群、客群輪廓、競品分析、市場規模評估 |
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

若要安裝其他技能，將上述來源目錄換成 `skills/handoff`、`skills/market-segments`、`skills/brainstorm-experiments-new` 或 `skills/value-proposition`。

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

「探索問題」安裝後可以直接描述工作情境，或指定要使用的技能。例如：

> 用探索問題幫我釐清：使用者常說流程很麻煩，但我還不知道真正卡在哪裡。

也可以在 Codex 中使用技能識別名稱：

```text
$explore-problems 先幫我想清楚要解決什麼，再討論做法。
```

Handoff 需要明確呼叫，並可附上下一個對話的工作重點：

```text
$handoff 下一個對話要接續整理產品需求與驗收條件，請產出交接文件。
```

交接文件會儲存到作業系統的暫存目錄，引用既有文件、議題或提交，避免重複抄寫內容，並遮蔽敏感資訊。

Market Segments 可用來探索產品的潛在客群。提供產品描述，並附上已有的訪談、研究或客戶資料：

```text
$market-segments 我們正在設計一款協助小型團隊管理產品需求的工具。請辨識 3–5 個潛在客群，分析各自的 JTBD、痛點與產品適配程度，並標示需要驗證的假設。
```

新產品驗證實驗可將產品構想轉成可衡量的 XYZ 假設，並設計低成本的需求驗證方式：

```text
$brainstorm-experiments-new 我們想為小型團隊推出產品需求管理工具。請建立 XYZ 假設，設計 2–3 個低成本驗證實驗，列出衡量指標與成功門檻，並標示尚待驗證的假設。
```

價值主張技能協助釐清產品、目標顧客及替代方案，再撰寫七行定位。預設會在撰寫前確認摘要；也可明確要求跳過確認並標示假設：

```text
$value-proposition 為協助小型團隊管理產品需求的工具撰寫價值主張，請先幫我釐清目標顧客與替代方案。
```

個別技能的流程與範例，請參考該技能目錄內的說明。

## 儲存庫結構

```text
rpo-skill/
├── README.md
└── skills/
    ├── explore-problems/
    │   ├── SKILL.md
    │   ├── README.md
    │   ├── agents/
    │   │   └── openai.yaml
    │   ├── grill-boss-icon.png
    │   └── social-preview.png
    ├── handoff/
    │   ├── SKILL.md
    │   └── agents/
    │       └── openai.yaml
    ├── market-segments/
    │   ├── SKILL.md
    │   └── LICENSE
    ├── brainstorm-experiments-new/
    │   ├── SKILL.md
    │   └── LICENSE
    └── value-proposition/
        └── SKILL.md
```

## 新增技能

1. 在 `skills/` 下建立獨立目錄，使用小寫英文與連字號命名。
2. 撰寫 `SKILL.md`，包含 `name`、`description`，以及適用情境、工作流程和預期產出。
3. 視需要加入 `agents/openai.yaml`、範例、參考資料或工具腳本。
4. 以實際工作情境確認技能能正確觸發、提問與產出，再將它加入上方「已收錄技能」表格。

技能應清楚區分事實、推論與假設，保留使用者的決策權，並在資訊不足時說明仍需確認的事項。

## 來源與致謝

「探索問題」改編自 [grill-boss 繁體中文原始版本](https://github.com/WeAgileio/rpo-skill/tree/b65446a97d55e95e2ad2dcd91bcb40d235ee43c3)，原始方法來自 [onlyLT/grill-boss](https://github.com/onlyLT/grill-boss)。此版本將情境延伸為通用問題探索，保留分輪提問、事實查證與假設清單等做法。

「Handoff」收錄自本專案的既有技能，保留原始內容與明確呼叫設定。

「Market Segments」來自 Paweł Huryn 的 [PM Skills Marketplace](https://github.com/phuryn/pm-skills/tree/main/pm-market-research/skills/market-segments)，收錄本專案已安裝的 `pm-market-research` 2.1.0 版本，保留原始英文內容與參考連結。該技能採用 MIT 授權，授權與著作權聲明見 [skills/market-segments/LICENSE](skills/market-segments/LICENSE)。

「新產品驗證實驗」來自 Paweł Huryn 的 [PM Skills Marketplace](https://github.com/phuryn/pm-skills/tree/main/pm-product-discovery/skills/brainstorm-experiments-new)，收錄本專案已安裝的 `brainstorm-experiments-new`，保留原始英文內容與參考連結。該技能採用 MIT 授權，授權與著作權聲明見 [skills/brainstorm-experiments-new/LICENSE](skills/brainstorm-experiments-new/LICENSE)。

「價值主張」依 Geoffrey A. Moore 的定位方法整理，七行格式及參考資料見 [技能說明](skills/value-proposition/SKILL.md)。
