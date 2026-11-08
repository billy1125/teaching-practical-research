# Teaching-Practical-Research-2027 — 教學實踐研究計畫書撰寫工作台

> **MOE Teaching Practice Research proposal workbench for Claude Code** — 在 Claude Code 裡撰寫教育部教學實踐研究計畫（Teaching Practice Research，以下簡稱 TPR）的計畫書草稿，讓草稿對齊 TPR 的計畫精神與作者本人的撰寫風格。

---

## ⚠️ 免責聲明與使用須知 Disclaimer

> **請先讀完再使用。** 使用本專案即表示你已理解並接受以下事項。

- **專案性質 Side project**：這是作者**個人研究與測試用的 side project**，內容多為**與 AI 協作產生的初稿**，**測試尚未完整**、可能含有錯誤或 bug，並非正式、穩定或經完整驗證的產品。
- **不保證正確性 No warranty**：草稿內容**不保證正確、完整或合法**。**送件前務必自行核實所有事實、數據與文獻。** 作者不對任何因使用本專案而產生的後果負責。
- **學術倫理 Academic integrity**：依徵件說明「計畫申請聲明書」第 7 點，使用 AI 工具輔助撰寫須於計畫書中揭露使用目的、方式與範圍，且主持人對內容的正確性、真實性與完整性負最終責任。AI 產生的文獻一律視為未經核實，須逐筆查證後才能引用。
- **個資保護 Personal data**：計畫書涉及學生資料時須去識別化至無從識別特定當事人（個資法 §20、施行細則 §17）。
- **使用者自負責任 Use at your own risk**。

---

## 🎯 這個專案在做什麼

本專案只做兩件事：

1. **對齊計畫精神**——依 `tpr-guiding-principle/` 的 TPR 基本精神與計畫書格式撰寫各節。
2. **對齊撰寫風格**——依 `writing-style/personal-voice.md` 的作者筆法撰寫與編修。

主要產出是 `drafts/<計畫資料夾>/` 內的 Markdown 計畫書草稿。這不是軟體專案，沒有 build／lint／test。

## 🗂️ 專案結構 Project structure

```
Teaching-Practical-Research-2027/
├── CLAUDE.md                    # 通用工作方式（與特定計畫無關）
│
├── tpr-guiding-principle/       # 綱領（共用）：TPR 基本精神、附件1 徵件說明與計畫書格式
├── writing-style/               # 撰寫風格（共用）：personal-voice.md；個人資料，不進版控
│
├── reference/                   # 規範
│   ├── rules.md                 #   核心規則（由 CLAUDE.md 以 @import 載入）
│   ├── report-format.md         #   草稿輸出格式與定稿體例
│   ├── academic.md              #   學術討論的認識論標示與論證要求
│   └── initial-setup.md         #   一次性環境設定
│
├── drafts/                      # 計畫資料夾的上層；除範本外預設不進版控
│   ├── _template/               #   新計畫範本
│   │   ├── PROJECT.md           #     計畫基本資料：題目、年度、課程場域、素材、產出設定
│   │   ├── research-material/   #     研究素材：發想筆記、主題整理、年度規劃
│   │   └── history/             #     舊版草稿
│   └── <計畫資料夾>/             #   每份計畫一個，名稱自訂（例如 TPR-2026/）
│
└── .claude/
    └── skills/                  # 見下表
```

## 🧩 技能總覽 Skills

| 技能 | 何時觸發 | 產出 |
|------|----------|------|
| **`source-document-extraction`** | Read 無法渲染 PDF、需抽取 PDF／Word 文字或定位章節頁碼 | 結構化 Markdown `.md` |
| **`passage-editing-zh`** | 「用我的筆法改這一節」「潤一下這段」 | 直接修改計畫資料夾內的草稿 |
| **`speak-academic-tw`** | 「幫我潤稿」「這段像 AI 寫的」（沒有 `personal-voice.md` 時） | 逐句修訂的草稿文字 |

技能依 Claude Code 規範放在 `.claude/skills/`，會被**自動探索**；用自然語言描述需求即可觸發。

素材以眼前文件為準：理論、文獻、課程事實只能引用計畫資料夾內實際存在的內容，素材裡沒有的一律標 `〔待補〕`／`〔TODO(cite)〕`，**不得用模型記憶補完**。規則見 `.claude/skills/_shared/anti_leakage.md`。

## 🔧 需求 Requirements

1. **Claude Code**（[安裝說明](https://claude.com/claude-code)）。
2. **conda**（Miniconda／Anaconda 皆可），用來建立名為 `research` 的 Python 3.11 環境。

   ```bash
   conda create -n research python=3.11 -y
   conda run -n research pip install pymupdf pdfplumber pymupdf4llm python-docx mammoth
   conda run -n research python -c "import fitz, pdfplumber, pymupdf4llm"
   ```

   > 專案權限已封鎖直接使用 `python`／`pip`；所有 Python 指令一律走 `conda run -n research`。
   >
   > ⚠️ **授權注意 PyMuPDF / AGPL**：PDF 抽取使用的 **PyMuPDF（`pymupdf`）為 AGPL-3.0 授權**。本專案不打包該套件、由使用者自行安裝。若你打算把本工具**散布為產品**或**跑成對外網路服務**，AGPL 的原始碼揭露義務可能被觸發；屆時可改用 MIT 授權的 `pdfplumber`，或自行評估法律風險。

完整環境說明見 [`reference/initial-setup.md`](reference/initial-setup.md)。

## 🚀 開始使用 Getting started

```bash
git clone https://github.com/billy1125/Teaching-Practical-Research-2027.git
```

在專案根目錄開啟 Claude Code，完成上方 conda 設定，然後：

1. **建立計畫資料夾**——把 `drafts/_template/` 複製成新資料夾，名稱自訂（例如 `drafts/TPR-2026/`）。
2. **填 `PROJECT.md`**——題目、年度、學門、課程場域、產出設定。
3. **放素材**——研究發想放計畫資料夾的 `research-material/`；徵件說明放 `tpr-guiding-principle/`。
4. **（建議）放入筆法摘要**——把自己的筆法摘要放在 `writing-style/personal-voice.md`。
5. **開始寫**。

## 💡 使用範例 Usage

```
> 依 drafts/TPR-2026/PROJECT.md 寫一版計畫書草稿的（五）研究設計與執行規劃
> 對照計畫精神，檢查（一）動機這節有沒有偏離
> 用我的筆法潤一下（一）動機這節
```

## 📐 撰寫規範重點

- **計畫精神**（`tpr-guiding-principle/`）：撰寫各節時對照 TPR 基本精神與附件1 計畫書格式的對應要求。
- **內文格式**（[`reference/report-format.md`](reference/report-format.md)）：同一段落寫成**單一行**，段落之間空一行；中文標點全形、中英數之間加半形空格；待補一律標 `〔待補：說明〕`。

## 📄 授權 License

MIT 授權；內容「AS IS」提供，不負擔保責任，另見上方[免責聲明](#️-免責聲明與使用須知-disclaimer)。

`writing-style/` 內的個人寫作素材、各計畫資料夾內的研究發想不隨授權開放再散布。

© 2026 Cho-Hsun Lu (billy1125)
