# 初始設定（一次性）

本檔為專案的一次性設定說明，由根目錄 `CLAUDE.md` 引用。內容通常只在建立環境或初次動筆時用到，故獨立於此，避免佔用 `CLAUDE.md` 的日常工作指引篇幅。

## 環境設定

本專案的 Python 只用於驅動 `source-document-extraction` 技能。一律在名為 `research` 的 conda 環境（Python 3.11，跨平台：Windows／macOS〔含 Apple Silicon〕／Linux 通用）中執行；所有 Python 指令請一律使用 `conda run -n research`：

```
conda run -n research python script.py
conda run -n research pip install <套件名稱>
```

專案權限設定已封鎖直接使用 `python`、`python3`、`pip`、`pip3`。

## 套件與安裝

本工作區的 conda 環境與下列套件，**存在目的就是支援 `source-document-extraction` 技能**——該技能在此環境執行，把 PDF（例如新版 `附件1` 徵件說明 PDF）與 Word（`.docx`）抽成結構化 Markdown 供 Read 閱讀。套件清單與版本以技能 `SKILL.md`「環境需求」為準，本檔與其對齊；技能更新套件需求時，一併更新此處。相關套件與用途：

| 用途 | 套件 | 說明 |
|---|---|---|
| 讀 PDF | `pymupdf`（`import fitz`）、`pymupdf4llm`、`pdfplumber` | `pymupdf` 開檔；`pymupdf4llm` 為預設 Markdown 後端（依字型推斷標題、輸出表格、處理多欄）；`pdfplumber` 輔助 |
| 讀 Word（`.docx`） | `mammoth`、`python-docx`（`import docx`） | `mammoth` 轉 Markdown 保留標題層級（預設）；`python-docx` 精確擷取段落／表格純文字（`--txt`） |

安裝與驗證：

```bash
conda create -n research python=3.11 -y
conda run -n research pip install pymupdf pdfplumber pymupdf4llm python-docx mammoth
conda run -n research python -c "import fitz, pdfplumber, pymupdf4llm"
```

## 資料夾結構與建立

專案由共用的綱領與撰寫風格、各計畫資料夾、技能構成。各項的完整角色見 `CLAUDE.md` 第二部分「文件來源與角色」。

```
tpr-guiding-principle/     # 綱領（所有計畫共用）：TPR 基本精神、附件1 徵件說明與計畫書格式（由 PDF 抽成 .md）
writing-style/             # 撰寫風格（所有計畫共用）：作者筆法摘要 personal-voice.md 與相關素材；內容不進版控，僅保留空資料夾
reference/                 # 參考：核心規則（rules.md）、輸出格式（report-format.md）、學術討論（academic.md）、本一次性設定說明（initial-setup.md）
drafts/                    # 計畫資料夾的上層；除 .gitkeep 與 _template/ 外預設不進版控
├── _template/             #   新計畫範本：PROJECT.md、research-material/、history/
└── <計畫資料夾>/           #   每份計畫一個，名稱由使用者自訂（例如 TPR-2026/），結構同 _template/
.claude/skills/            # 技能：source-document-extraction、passage-editing-zh、speak-academic-tw
```

新計畫的建立方式：把 `drafts/_template/` 複製成新的計畫資料夾、自行命名，再填寫其中的 `PROJECT.md`。使用者若另有其他素材，於動筆前一併指定，不限於上述預設來源。
