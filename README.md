# teaching-practical-research — 教學實踐研究計畫書撰寫工作台 · Proposal Workbench for MOE Teaching Practice Research (TPR)

> 以 **Claude Code** 驅動的**教育部教學實踐研究計畫（Teaching Practice Research，TPR）計畫書**撰寫工作台 — A **Claude Code–powered drafting workbench** for **Taiwan MOE Teaching Practice Research (TPR) grant proposals** in Traditional Chinese. 草稿對齊 TPR 計畫精神與計畫書格式，筆法對齊作者本人，**素材沒有的內容一律標待補、不用模型記憶補完**。

![Claude Code](https://img.shields.io/badge/Claude%20Code-Skills-8A2BE2)
![Skills](https://img.shields.io/badge/Skills-3-1857B6)
![License: MIT](https://img.shields.io/badge/License-MIT-2E9E4F)
![Language](https://img.shields.io/badge/計畫書語言-繁體中文-2E9E4F)

teaching-practical-research 幫大專校院教師撰寫教育部教學實踐研究計畫的計畫書草稿。它只做兩件事：讓草稿**對齊 TPR 的計畫精神**（依 `tpr-guiding-principle/` 的基本精神與附件1 計畫書格式），以及**對齊作者的撰寫風格**（依 `writing-style/personal-voice.md`）。主要產出是 `drafts/<計畫資料夾>/` 內的 Markdown 草稿；這不是軟體專案，沒有 build／lint／test。

teaching-practical-research helps university faculty in Taiwan draft proposals for the Ministry of Education (MOE) Teaching Practice Research program. It aligns each draft with the TPR guiding principles and proposal format, and with the author's own writing voice. Theory, literature, course facts, and data come only from the author's materials; anything missing is marked as a TODO instead of being filled in from model memory.

> 🤖 AI 的完整作業規則見 **[`CLAUDE.md`](CLAUDE.md)**（主指引）與 **[`reference/rules.md`](reference/rules.md)**（核心規則）；本檔是給人看的快速上手。姊妹專案：資管中文論文編修 [paper-editing-workbench-zh](https://github.com/billy1125/paper-editing-workbench-zh)。

## ⚠️ 免責聲明與使用須知 / Disclaimer

> **請先讀完再使用。** 使用本專案即表示你已理解並接受以下事項。**Please read before use.** Using this project means you accept the following.

- **專案性質 Side project**：這是作者**個人研究與測試用的 side project**，內容多為**與 AI 協作產生的初稿**，**測試尚未完整**、可能含有錯誤或 bug，並非正式、穩定或經完整驗證的產品。
- **不保證正確性 No warranty**：草稿內容**不保證正確、完整或合法**。**送件前務必自行核實所有事實、數據與文獻。** 作者不對任何因使用本專案而產生的後果負責（一切依 [MIT 授權](LICENSE) 之「AS IS」免責條款）。
- **學術倫理 Academic integrity**：依徵件說明「計畫申請聲明書」第 7 點，使用 AI 工具輔助撰寫須於計畫書中揭露使用目的、方式與範圍，且主持人對內容的正確性、真實性與完整性負最終責任。AI 產生的文獻一律視為未經核實，須逐筆查證後才能引用。
- **個資保護 Personal data**：計畫書涉及學生資料時須去識別化至無從識別特定當事人（個資法 §20、施行細則 §17）。
- **使用者自負責任 Use at your own risk.**

## ✨ 特色 / Features

- **對齊計畫精神 / Aligned with TPR principles**：撰寫各節時對照 `tpr-guiding-principle/` 的 TPR 基本精神與附件1 計畫書格式的對應要求。
- **對齊作者筆法 / Personal voice**：有 `writing-style/personal-voice.md` 就套用作者筆法；沒有時先提醒，仍未指定才用通用標準學術中文。
- **多計畫佈局 / Multi-proposal layout**：每份計畫各自一個 `drafts/<計畫資料夾>/`，名稱自訂，設定寫在該夾的 `PROJECT.md`。
- **素材為準 / Source-grounded**：理論、文獻、課程事實只引用計畫資料夾內實際存在的內容，素材沒有的一律標 `〔待補〕`／`〔TODO(cite)〕`。規則見 `.claude/skills/_shared/anti_leakage.md`。
- **PDF／Word 抽取 / Document extraction**：用 `source-document-extraction` 把徵件說明或其他 PDF／Word 抽成結構化 Markdown 再閱讀。
- **只動語言的改稿 / Language-only editing**：兩個改稿技能只調整句構、語域與標點，不改論證、引用與待補標記。
- **個人資料不進版控 / Private by default**：計畫資料夾與 `writing-style/` 的內容預設由 `.gitignore` 排除，只追蹤範本與空資料夾。

## 🧩 內建 Skills

| Skill | 用途 |
|---|---|
| `source-document-extraction` | 把 PDF／Word 抽成結構化 Markdown，供閱讀新版附件1 或其他文件，也可定位章節頁碼 |
| `passage-editing-zh` | 套用 `writing-style/personal-voice.md` 逐段編修草稿，只動語言表層，不改論證 |
| `speak-academic-tw` | 不套個人筆法的學術中文語言修飾：修語法、調學術語域、去 AI 味、校正中國用語與半形標點 |

技能放在 `.claude/skills/`，Claude Code 會自動探索，用自然語言描述需求即可觸發。兩個改稿技能二選一：有 `personal-voice.md` 用 `passage-editing-zh`，沒有就用 `speak-academic-tw`；要併用時先跑 `speak-academic-tw` 再跑 `passage-editing-zh`。

## 🔧 環境需求 / Requirements

需要 **[Claude Code](https://claude.com/claude-code)** 與 conda（Miniconda／Anaconda 皆可）建立的 `research` 環境（Python 3.11）。完整說明見 **[`reference/initial-setup.md`](reference/initial-setup.md)**。

```bash
conda create -n research python=3.11 -y
conda run -n research pip install pymupdf pdfplumber pymupdf4llm python-docx mammoth
conda run -n research python -c "import fitz, pdfplumber, pymupdf4llm; print('imports ok')"
```

> 專案權限已封鎖直接使用 `python`／`pip`；所有 Python 指令一律走 `conda run -n research`。
>
> ⚠️ **授權注意 PyMuPDF / AGPL**：PDF 抽取使用的 **PyMuPDF（`pymupdf`）為 AGPL-3.0 授權**。本專案不打包該套件、由使用者自行安裝。若你打算把本工具**散布為產品**或**跑成對外網路服務**，AGPL 的原始碼揭露義務可能被觸發；屆時可改用 MIT 授權的 `pdfplumber`，或自行評估法律風險。

## 🚀 開一份新計畫 / Quick start

```bash
git clone https://github.com/billy1125/teaching-practical-research.git
```

在專案根目錄開啟 Claude Code，完成上方 conda 設定，然後：

1. **建立計畫資料夾**：把 `drafts/_template/` 複製成 `drafts/<計畫資料夾>/`，名稱自訂。
2. **填 `PROJECT.md`**：題目、年度、學門、摘要、關鍵字、課程場域、素材來源、產出設定。
3. **放素材**：研究發想放該計畫的 `research-material/`；新年度的徵件說明 PDF 用 `source-document-extraction` 抽成 `.md` 後放進 `tpr-guiding-principle/`。
4. **（建議）放入筆法摘要**：把自己的筆法摘要放在 `writing-style/personal-voice.md`。
5. **開始寫**：指定要寫哪一節，Claude 依綱領、`PROJECT.md` 與研究素材撰寫，草稿寫入該計畫資料夾，舊版移入 `history/`。

## 🗣️ 常用指令速查 / Command Cheatsheet

> 這裡的「指令」**不是要輸入的程式或 slash 指令，而是你直接對 Claude 說的話**，Claude 會據此選用對應的流程或 skill。用詞不必照抄。These are **plain-language requests**, not slash commands.

| 想做的事 | 你可以這樣說 | 對應 skill／動作 |
|---|---|---|
| 撰寫某一節 | 「依 `drafts/<計畫資料夾>/PROJECT.md` 寫（五）研究設計與執行規劃」 | 標準工作流程（讀設定 → 確認來源 → 定筆法 → 撰寫） |
| 對照計畫精神 | 「對照計畫精神，檢查（一）動機這節有沒有偏離」 | 對照 `tpr-guiding-principle/` |
| 套用個人筆法 | 「用我的筆法潤一下（一）動機這節」 | `passage-editing-zh` |
| 學術中文修飾 | 「幫我潤稿」「這段像 AI 寫的」 | `speak-academic-tw` |
| 抽取 PDF／Word | 「把新版附件1 PDF 抽成 Markdown」 | `source-document-extraction` |

## 🗂️ 目錄結構 / Structure

```
teaching-practical-research/
├── CLAUDE.md                    # AI 主指引（通用工作方式，與特定計畫無關）
├── LICENSE                      # MIT
├── NOTICE                       # 第三方致謝
├── tpr-guiding-principle/       # 【共用】TPR 基本精神、附件1 徵件說明與計畫書格式（PDF 不進版控）
├── reference/                   # 規範
│   ├── rules.md                 #   核心規則（由 CLAUDE.md 以 @import 載入）
│   ├── report-format.md         #   草稿輸出格式與定稿體例
│   ├── academic.md              #   學術討論的認識論標示與論證要求
│   └── initial-setup.md         #   一次性環境設定
├── writing-style/               # 【共用】只追蹤空資料夾；personal-voice.md 由你自行放入（git-ignored 私人）
├── drafts/
│   ├── _template/               # 新計畫範本，複製改名即可（進版控）
│   │   ├── PROJECT.md           #   計畫基本資料
│   │   ├── research-material/   #   研究素材
│   │   └── history/             #   舊版草稿
│   └── <計畫資料夾>/             # 你的計畫（git-ignored 私人）
└── .claude/
    ├── settings.json            # 專案權限（封鎖直接使用 python／pip）
    └── skills/                  # 3 個 skill 與共用規範 _shared/
```

## 📄 授權 / License

[MIT](LICENSE) © 2026 Cho-Hsun Lu (billy1125) — 內容「AS IS」提供，不負擔保責任，另見上方[免責聲明](#️-免責聲明與使用須知--disclaimer)。

`writing-style/` 內的個人寫作素材、各計畫資料夾內的研究發想不隨授權開放再散布。`speak-academic-tw` 為衍生作品，所參考的第三方專案與執行時相依的外部工具見 [`NOTICE`](NOTICE)。
