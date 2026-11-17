# 原始資料層 (Raw Sources)

此目錄存放所有未經修改的原始資料，是整個 Wiki 的真實性依據（Ground Truth / Source of Truth）。

## 資料夾說明
- `papers/`：學術論文（支援 Markdown 筆記、PDF 檔案、arXiv 轉錄文字等）。
- `articles/`：技術部落格、發表會逐字稿、技術通訊、產業報告。
- `assets/`：圖片、圖表附件。可搭配 Obsidian 的 Attachment 設定指定到此資料夾。

## 使用原則
1. **不可變性 (Immutable)**：LLM Agent **只會讀取** 這裡的檔案，絕對不會修改或刪除原始檔案。
2. **如何導入**：
   - 將新論文或文章放入 `papers/` 或 `articles/`。
   - 在與 Agent 對話時指示：「請幫我 Ingest / 導入 `raw/papers/xxx.md`」。
   - Agent 將會自動萃取摘要、更新 `wiki/` 內相關的概念與實體頁面、更新 `wiki/index.md` 並在 `wiki/log.md` 留上記錄。
