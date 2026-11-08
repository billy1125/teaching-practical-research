# 核心規則（Rules）

動筆前的速查閘門。本檔由根目錄 `CLAUDE.md` 以 `@import` 載入，是各項行動指令的正典；細節與理由見 `CLAUDE.md` 各部分。與 `CLAUDE.md` 後文的完整說明衝突時以後文為準，與使用者當下指示衝突時以使用者為準。

## 絕對不能做（NEVER）

- **不把個別計畫的資料寫進 `CLAUDE.md`**——題目、摘要、課程場域等特定計畫設定一律寫在該計畫資料夾的 `PROJECT.md`；`CLAUDE.md` 只放通用工作方式。
- **不替計畫資料夾命名**——`drafts/` 底下的計畫資料夾名稱由使用者決定；新計畫由使用者從 `drafts/_template/` 複製。
- **不直接對 PDF／Word 動 Read**——本機 Read 無法渲染 PDF（缺 poppler／pdftoppm）；一律先用 `source-document-extraction` 抽成 `.md` 再讀。
- **不直接用 `python`／`python3`／`pip`／`pip3`**——已被專案權限封鎖；一律 `conda run -n research`。
- **不改寫 `source-document-extraction` 內附腳本的指令或增減旗標**——內附腳本為確定性工具，缺少的行為改用既有旗標達成。
- **不把個人資料進版控**——`writing-style/` 只保留空資料夾；`drafts/` 底下的計畫資料夾預設不追蹤，只放行 `drafts/.gitkeep` 與 `drafts/_template/`。
- **段落中間不手動換行、不硬斷到固定欄寬**——同一段落寫成單一行。
- **不用模型記憶補文獻、理論、課程事實或數據**——素材（`PROJECT.md`、`research-material/`、`tpr-guiding-principle/`）裡沒有的一律標 `〔待補〕`／`〔TODO(cite)〕`，寧可留白。
- **改稿技能不新增主張**——`passage-editing-zh` 與 `speak-academic-tw` 只動語言表層，不改論證、引用與待補標記。

## 一定要做（ALWAYS）

- **動筆前先確認計畫資料夾並讀它的 `PROJECT.md`**，取得題目、摘要、關鍵字、課程場域、指定素材與產出設定。
- **撰寫依據＝綱領（`tpr-guiding-principle/`）＋計畫設定（`PROJECT.md`）＋研究素材（`research-material/`）**。
- **對齊計畫精神**：撰寫各節時對照 `tpr-guiding-principle/教學實踐研究計畫基本精神.md` 與 `附件1_計畫書格式_結構化.md` 的對應要求。
- **對齊撰寫風格**：依「定筆法」套用 `writing-style/personal-voice.md`。
- **草稿寫入該計畫資料夾**；舊版草稿移入該資料夾的 `history/`。
- **內文格式**：同段單一行、段落間空行分隔；其餘格式（標題階層、表格、待補標示、定稿體例）遵循 `reference/report-format.md`。
- **對話一律繁體中文、台灣用語**，回答簡潔直接。

## 要問使用者（ASK）

- **動筆前確認**本次處理哪一個計畫資料夾。
- **動筆前確認**是否有 `PROJECT.md` 預設之外的額外素材需納入。
- **動筆前確認** `tpr-guiding-principle/` 是否為最新版本（參考文件隨年度更新）。
- **`writing-style/` 無 `personal-voice.md` 時**，先提醒使用者可提供 `personal-voice.md`、或確認是否套用個人筆法，勿逕自略過。
- **`source-document-extraction` 抽取後是否要由 LLM 進一步整理版面**——會額外耗 token，先問再做。

## 按照流程（PROCESS）

嚴格依「標準工作流程」七步，不跳步：

1. 選定計畫資料夾 → 2. 讀設定（`PROJECT.md`）→ 3. 確認來源（綱領＋研究素材＋確認額外素材）→ 4. 讀 PDF（先以技能抽取再 Read）→ 5. 定筆法 → 6. 撰寫（寫入計畫資料夾）→ 7. 確認綱領為最新版。

## 有條件選擇（CONDITIONAL）

- **定筆法（三層遞退）**：有 `writing-style/personal-voice.md` 就套用作者筆法；沒有先提醒使用者；使用者仍未指定，才以通用標準學術中文撰寫。
- **PDF 擷取後端**：預設 `pymupdf4llm`；僅在輸出結構不理想、或需頁首頁尾去重／PAGE 分隔／自訂章節名時，才加 `--legacy`。
- **技能取用**：`source-document-extraction`（抽取 PDF／Word）；`passage-editing-zh`（套個人筆法改稿）；`speak-academic-tw`（不套個人筆法的學術中文語言修飾，去 AI 味與中國用語校正）。
- **改稿技能二選一**：有 `writing-style/personal-voice.md` 用 `passage-editing-zh`；沒有就用 `speak-academic-tw`。兩者都只動語言表層，都不得更動論證、引用與待補標記；要併用時先 `speak-academic-tw` 再 `passage-editing-zh`。
- **綱領適用性**：`tpr-guiding-principle/` 屬基本原則而非逐條硬性條款；與使用者當下指示衝突時，以使用者的決定為準。
