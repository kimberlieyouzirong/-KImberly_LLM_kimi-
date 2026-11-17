# LLM Wiki 操作日誌 (Log)

本文件為時間序列追加（Append-only）的操作紀錄。每筆記錄遵循統一前綴格式：
`## [YYYY-MM-DD] <操作類型> | <描述>`
常見操作類型包含：`init`, `ingest`, `query`, `lint`, `refactor`。

---

## [2026-11-17] init | 初始化 LLM Wiki 知識庫結構與範本
- 依據 Andrej Karpathy LLM Wiki 模式建立 `AGENT.md`、三層目錄結構 (`raw/`, `wiki/`, `AGENT.md`)。
- 初始化 `wiki/index.md` 與 `wiki/log.md`。
- 植入基礎示範概念頁面（[[transformer-architecture]]、[[chain-of-thought]]）、實體頁（[[deepseek-r1]]）、文獻摘要（[[source-chain-of-thought-wei-2022]]）及綜述報告（[[reasoning-models-evolution]]），以供 Obsidian Graph View 立即體驗雙向鏈接。


## [2026-11-17] ingest | The Business Model: Theoretical Roots, Recent Developments, and Future Research (Zott, Amit & Massa, 2010)
- 原始文件已存檔至 `raw/papers/business-model-theoretical-roots-zott-2010.md`。
- 建立文獻提煉頁面：[[source-zott-amit-massa-2010-business-model]]。
- 擴散建立/更新 4 篇核心概念頁面：
  - [[business-model|商業模式]]（四大共識、定義匯整）
  - [[activity-system|活動系統觀點]]（波特活動三層配適度、跨邊界設計）
  - [[business-model-innovation|商業模式創新]]（三大類型、資產慣性與主導邏輯陷阱）
  - [[value-creation-and-capture|價值創造與價值捕獲]]（NICE 價值驅動架構）
- 擴散建立 3 篇實體頁面：[[christoph-zott]]、[[raphael-amit]]、[[iese-business-school]]。
- 產出深度綜述對比報告：[[business-model-vs-strategy|商業模式 vs 競爭策略 vs 技術創新：文獻綜述與本質辨析]]。
- 同步更新 `wiki/index.md` 與統計數據。


## [2026-11-17] ingest | Digital Product Passport for Sustainable Marketing: Core Propositions and Research Agenda (Koukopoulos & Lazaris, 2026)
- 原始文件已存檔至 `raw/papers/digital-product-passport-sustainable-marketing-2026.md`。
- 建立文獻提煉頁面：[[source-koukopoulos-lazaris-2026-dpp]]。
- 擴散建立 3 篇核心概念頁面：
  - [[digital-product-passport|數位產品護照 (DPP)]]（歐盟 ESPR、電池法規、生命週期溯源架構）
  - [[signaling-theory-sustainability|永續訊號理論與信任屬性]]（阿克洛夫信任屬性、Spence 訊號分離均衡公式、審計邊界）
  - [[sustainable-marketing-circular-economy|永續行銷與循環經濟]]（理性行為理論傳導鏈、自願期 vs 強制期兩階段競爭優勢）
- 同步更新 `wiki/index.md` 與統計數據。
