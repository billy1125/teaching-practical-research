# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

本專案用於撰寫教育部教學實踐研究計畫（Teaching Practice Research，以下多簡稱為 TPR）的計畫書草稿。工作範圍只有兩件事：讓草稿對齊 TPR 的計畫精神，以及對齊作者的撰寫風格。

# 專案目的

根據「第一部分：研究計畫基礎」的文件，依照「第二部分：工作指引」撰寫 TPR 計畫書草稿。這不是一般軟體專案——沒有 build／lint／test 流程；主要產出是 `drafts/<計畫資料夾>/` 內的 Markdown 計畫書草稿。

> **`CLAUDE.md` 只放與特定計畫無關的通用工作方式，勿把個別計畫的資料寫進本檔**

# 核心規則（Rules）

動筆前的速查閘門，濃縮五類行動指令（絕對不能做／一定要做／要問使用者／按照流程／有條件選擇），內容抽出至 `reference/rules.md`，於此以 import 自動載入：

@reference/rules.md

# 第一部分：研究計畫基礎

## 教學實踐研究計畫(TPR)基本綱領

這是研究計畫撰寫的基本綱領，也是草稿要對齊的計畫精神；屬基本原則而非硬性條款，細節可由使用者微調。參考文件置放於 `tpr-guiding-principle/`，所有計畫共用：

- 教學實踐研究計畫基本精神文件：`教學實踐研究計畫基本精神.md`
- 徵件說明與計畫書格式：`附件1_115年度徵件說明與計畫書格式.md`（由官方 PDF 抽取）、`附件1_計畫書格式_結構化.md`（結構化整理，撰寫時的主要依循）

原始 PDF 不放在資料夾內（`.gitignore` 排除 `*.pdf`）。年度更新時，以 `source-document-extraction` 抽取新版 PDF 後取代上列文件。

> TPR 參考文件會隨時更新，需要定時來確認與整理

## 計畫資料夾

每份計畫書放在 `drafts/` 底下的一個計畫資料夾，**資料夾名稱由使用者自行決定**（例如 `drafts/TPR-2026/`）。Claude 不替計畫資料夾命名，也不假設固定名稱；開始工作前先確認本次處理哪一個計畫資料夾。

新計畫由使用者把 `drafts/_template/` 複製成新資料夾後填寫。計畫資料夾的基本結構：

```
drafts/<計畫資料夾>/
├── PROJECT.md            # 計畫基本資料：題目、年度、摘要、關鍵字、課程場域、素材來源、產出設定
├── research-material/    # 研究素材：發想筆記、與 LLM 的整理與對話筆記等
├── history/              # 舊版草稿
├── MEMO.md               # 待決策、待釐清、可能有問題之處與待補資料
└── <草稿>.md              # 計畫書草稿，檔名依 PROJECT.md 的檔名慣例
```

## 決策與待補紀錄（MEMO.md）

計畫需要決策、需要釐清、可能有問題的地方，以及待補資料清單，一律寫在該計畫資料夾的 `MEMO.md`，不寫進計畫書草稿。草稿內只留短標記（〔待補〕〔待確認〕`TODO(cite)`／`TODO(confirm)`），需要說明時寫「見 `MEMO.md` 某項」，不在草稿內寫長段註記或在草稿末附清單。`MEMO.md` 分「需要決策」「需要釐清」「可能有問題」「待補資料」四類，每項給編號；項目處理完後從 `MEMO.md` 刪除，並同步清除草稿內對應標記。改動草稿時，若產生新的待決策或待釐清事項，同步寫入 `MEMO.md`。

計畫資料夾內可另放使用者的其他文件（例如課程設計、教材差異分析），用途寫在 `PROJECT.md`「產出設定」的其他檔案說明。計畫資料夾屬個人資料，預設不進版控；`.gitignore` 只放行 `drafts/.gitkeep` 與 `drafts/_template/`。

## 計畫基本資料（PROJECT.md）

每份計畫的設定寫在該計畫資料夾的 `PROJECT.md`，格式以 `drafts/_template/PROJECT.md` 為準。課程場域（課程名稱、學生背景、課程長度、分組、階段規劃）直接寫在 `PROJECT.md`「課程場域」一節，不另設課程文件資料夾。撰寫草稿前先讀 `PROJECT.md`。

## 研究素材

使用者會預先思考研究發想，整理成以 Markdown 為主的純文字文件，放在計畫資料夾的 `research-material/`。文件類型包括：

- 使用者個人發想筆記
- 使用者與其他 LLM 進行的整理筆記
- 使用者與 LLM 討論的對話整理筆記
- 未整理的其他筆記文件

研究發想內容從這些文件中取得。若使用者另有其他素材，於動筆前一併指定。

---

# 第二部分：工作指引（撰寫計畫書時）

## 文件來源與角色

撰寫的素材分兩種角色——三類內容來源與一類撰寫風格參考；各項「是什麼」見第一部分，這裡只講撰寫時「怎麼用」：

- **綱領**（`tpr-guiding-principle/`）：草稿要對齊的計畫精神與計畫書格式，界定 TPR 的審查邏輯與章節要求。屬基本原則而非逐條硬性條款——與使用者當下指示衝突時，以使用者的決定為準。
- **計畫設定**（`<計畫資料夾>/PROJECT.md`）：題目、課程場域與產出設定，界定教學介入能落在哪個課程階段。
- **研究素材**（`<計畫資料夾>/research-material/`）：實際研究構想的來源。文件常有演進與從屬關係（整體整理、主軸文件、各主題分冊、年度規劃、子方案），動筆前先掃過資料夾、由檔名與內文判斷主軸與閱讀順序，而非假設固定清單——素材會隨計畫發展增減。
- **撰寫風格**（`writing-style/`）：草稿要對齊的作者筆法，界定「中文怎麼寫」而非「寫什麼」。筆法摘要為 `writing-style/personal-voice.md`，由使用者提供與維護；資料夾內容屬個人資料、不進版控。套用時機見下方標準工作流程「定筆法」。

**動筆前先向使用者確認是否有預設之外的額外素材需納入**，有的話一併指定。

## 計畫書內文格式

計畫書內文格式單純，一段文字就是一段，不要隨意分行——同一段落寫成單一行，不在段落中間手動換行或硬斷到固定欄寬，段落之間以空行分隔。草稿輸出的其餘格式規範（標題階層、表格清單、待補標示、定稿 Word 體例等）見 `reference/report-format.md`，撰寫前一併參照。

## 標準工作流程

1. **選定計畫資料夾**：確認本次處理 `drafts/` 底下哪一個計畫資料夾；新計畫請使用者從 `drafts/_template/` 複製並自行命名。
2. **讀設定**：讀該計畫資料夾的 `PROJECT.md`，取得題目、摘要、關鍵字、課程場域、指定素材與產出設定。
3. **確認來源**：掃過 `tpr-guiding-principle/` 與計畫資料夾的 `research-material/`，並向使用者確認是否有額外素材。
4. **讀 PDF**：本機 Read 工具無法渲染 PDF（缺 poppler／pdftoppm）。要讀 PDF／Word 時，先用 `source-document-extraction` 技能抽成 `.md` 再以 Read 開啟，不直接對 PDF 動手。
5. **定筆法**：撰寫前優先檢視 `writing-style/`——有 `personal-voice.md` 就套用作者筆法；沒有先提醒使用者可提供 `personal-voice.md` 或確認是否套用；使用者仍未指定，才以預設的通用標準學術中文撰寫。
6. **撰寫**：以綱領＋`PROJECT.md`＋研究素材為依據撰寫草稿，寫入該計畫資料夾；舊版草稿移入 `history/`。
7. TPR 參考文件（`tpr-guiding-principle/`）會隨年度更新，動筆前先確認是否為最新版本。

# 第三部分：其他專案資源

## 技能

`.claude/skills/` 內的技能：

| 技能 | 用途 |
|---|---|
| `source-document-extraction` | 把指定路徑的 PDF／Word 抽成結構化 Markdown，供閱讀新版附件1 PDF 或其他 PDF／Word 文件 |
| `passage-editing-zh` | 套用 `writing-style/personal-voice.md` 逐段編修草稿；只動語言表層，不改論證 |
| `speak-academic-tw` | 繁體中文學術文章的語言修飾：修語法、調學術語域、去 AI 味、校正中國用語與半形標點，保住數據、引用與推論強度；不評研究內容 |

兩個改稿技能分工：`passage-editing-zh` 套作者個人筆法，前提是 `writing-style/personal-voice.md` 已存在；`speak-academic-tw` 不套個人筆法，做通用學術中文的語言品質修飾，沒有 `personal-voice.md` 時用它。兩者都只動語言表層、不改論證，需要同時做就先跑 `speak-academic-tw` 再跑 `passage-editing-zh`。

## 共用規範（`.claude/skills/_shared/`）

跨 skill 的共同紀律抽在此處，各 skill 以相對路徑引用，不各自重寫：`anti_leakage.md`（以眼前素材為準的鐵律）、`confidence_language.md`（讀到多少就講多少的分級用語）、`output_language.md`（輸出語言慣例）。

## 初始設定（一次性）

環境設定、套件與安裝、資料夾結構等一次性設定通常只在建立環境或初次動筆時用到，已抽出至 `reference/initial-setup.md`，需要時再參閱。重點提醒：Python 一律在 conda `research` 環境（Python 3.11）以 `conda run -n research` 執行，直接使用 `python`／`pip` 已被專案權限封鎖。
