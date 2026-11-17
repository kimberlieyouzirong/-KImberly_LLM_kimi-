# LLM 研究知識庫 (Personal LLM Research Wiki)

> 參考 **Andrej Karpathy** 提出的 **LLM Wiki Pattern** 打造之個人大語言模型研究知識庫。
> 結合 **Obsidian（人類瀏覽與圖譜介面）** 與 **LLM Agent（知識庫維護者與研究助理）**，實現知識的持續積累與雙向聯網。

---

## 為什麼選擇 LLM Wiki，而非傳統 RAG？

| 維度 | 傳統 RAG / 文件上傳 | LLM Wiki 模式 |
| :--- | :--- | :--- |
| **知識積累** | 無累積，每次提問從零切塊檢索碎片 | **複合累積 (Compounding Artifact)**，越用越豐富 |
| **文獻關聯** | 難以跨越 5~10 篇長文獻進行複雜綜合 | 自動建立 `[[雙向鏈接]]`，脈絡與演進一目了然 |
| **矛盾處理** | 檢索出衝突資訊時容易產生幻覺 | 寫入時主動比對新舊論文，標註爭議點與推翻記錄 |
| **人機協作** | 人類問答、AI 簡答後資訊消失在對話流中 | **優質分析與橫向對比沉澱回 Wiki**，成為持久資產 |

---

## 知識庫架構 (Three-Layer Architecture)

```
LLM wiki 專案/
├── AGENT.md                 # 規範層：Agent 的行為規則、SOP 與標準模板
├── README.md                # 說明層：本指南文件
├── raw/                     # 原始來源層 (Immutable)：不可變真實數據源
│   ├── papers/              # 學術論文 (Markdown, PDF, 等)
│   ├── articles/            # 技術部落格、技術報告、演講逐字稿
│   └── assets/              # 圖片附件 (架構圖、測試曲線等)
└── wiki/                    # 知識庫層 (The Wiki)：LLM 全權維護與互聯
    ├── index.md             # 知識庫總導航索引
    ├── log.md               # 操作日誌 (append-only)
    ├── concepts/            # 核心理論與概念 (如 CoT, Attention, RLHF, MoE)
    ├── entities/            # 模型、研究機構、框架工具 (如 DeepSeek-R1, vLLM)
    ├── sources/             # 各來源的萃取摘要與重點引文
    └── synthesis/           # 橫向對比、技術演化史與專題報告
```

---

## 快速開始指南

### 第一步：在 Obsidian 中開啟本專案
1. 下載並安裝 [Obsidian](https://obsidian.md/)。
2. 點選 **「Open folder as vault」（開啟現有資料夾為倉庫）**，選擇本專案目錄 `c:\LLM wiki 專案`。
3. 開啟左側側邊欄的 **圖譜檢視 (Graph view)**，即可看到已為您初始化的知識節點與互連網絡！

### 第二步：建議的 Obsidian 設定與外掛
- **附件資料夾**：
  進入 Obsidian 設定 $\to$ **Files and links (檔案與連結)** $\to$ 將 **Default location for new attachments (新附件的預設位置)** 設定為：
  `Specified folder below`，並填入 `raw/assets`。
- **Obsidian Web Clipper**：
  安裝 Chrome / Firefox 瀏覽器擴充功能「Obsidian Web Clipper」，一鍵將 arXiv 摘要頁面或技術部落格剪藏為 Markdown 存入 `raw/`。
- **推薦社群外掛 (Community Plugins)**：
  - **Dataview**：根據 YAML Frontmatter 動態聚合查詢頁面表格。
  - **Marp** 或 **Advanced Slides**：直接將 `wiki/synthesis/` 的分析報告一鍵轉為簡報投影片。

---

## 日常操作與 Prompt 指令範例

在與 LLM Agent（如 Antigravity, Claude Code, Codex 等）對話時，您可直接使用以下操作指令：

### 1. 導入新資料（Ingest）
> 範例 Prompt：
> 「我剛把 DeepSeek-V3 的技術報告放進了 `raw/papers/deepseek-v3.md`，請幫我 Ingest 該來源，更新相關概念與實體頁面，並記錄到 log。」
- Agent 會讀取論文、建立 `wiki/sources/` 摘要，並自動連動更新 `wiki/concepts/`、`wiki/entities/`，最後更新 `index.md` 與 `log.md`。

### 2. 深度查詢與沉澱（Query & Synthesis）
> 範例 Prompt：
> 「根據 Wiki 現有的文獻，幫我比較 DeepSeek-R1 與傳統 CoT Prompting 在推理機制上的核心差異與優劣，並生成一篇橫向對比報告沉澱到 Wiki 中。」
- Agent 會先查閱 `wiki/index.md` 與相關頁面進行綜合分析，並將高品質分析寫入 `wiki/synthesis/`。

### 3. 健康巡檢（Lint）
> 範例 Prompt：
> 「請對目前的 Wiki 執行 Lint 健康檢查，找出未連線的孤島頁面、失效連結，以及是否有尚未建立獨立頁面的重要概念。」
- Agent 會逐一比對連結完整性，並給出後續研究與文獻補全建議。

---

## 核心設計規範詳情
所有關於頁面模板、Frontmatter 欄位規範、日誌格式與工作細節，請參閱根目錄的：
**[AGENT.md](file:///c:/LLM%20wiki%20專案/AGENT.md)**
