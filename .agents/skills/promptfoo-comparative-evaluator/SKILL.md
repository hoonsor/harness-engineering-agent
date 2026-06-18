---
name: promptfoo-comparative-evaluator
description: "使用 Promptfoo 概念進行平行的專案程式碼輸出比對 (Side-by-side Comparative Evaluation)，用於分析兩個不同模型產出專案的架構與程式碼差異。觸發關鍵字：平行比對、比較模型產出"
---

# Promptfoo Comparative Evaluator (平行比對裁判)

## 📌 技能目的
身為「駕馭工程代理」，此技能賦予你針對兩個不同模型產出的程式專案（例如 Gemini Pro vs Gemini Flash），進行嚴格的、無偏見的 **Side-by-side 平行對比**。找出結構性、邏輯性與維護性上的差異。

## ⚙️ 啟動時機
當使用者要求「比對兩個專案」、「比較不同模型產出」或提及「進行駕馭工程的全面分析（對比階段）」時啟動此技能。

## 🛠️ 執行工作流 (Workflow)

### 階段 1：環境定位與檔案樹比對
1. 確認目標 A（低階模型產出）與目標 B（高階模型產出）的實體路徑。
2. 使用 `run_command` 執行 `tree /F` 或 `dir /s /b` 來獲取雙方的專案結構。
3. 比對結構差異：
   - 缺少了哪些抽象層（例如：少了 DTO, Service, Middleware）？
   - 模組劃分是否過於龐大或緊耦合？
   - 是否缺乏設定檔或測試檔案？

### 階段 2：程式碼平行審查 (Side-by-Side Review)
1. 針對核心邏輯檔案（如 Main, Router, Core Service 等），同步讀取 A 與 B 版本的內容。
2. 以「盲測裁判」的視角，比較以下指標：
   - **防禦性程式設計 (Defensive Programming)**：Pro 是否比 Flash 處理了更多的邊界情況與例外？
   - **可維護性 (Maintainability)**：Pro 的變數命名、註解品質、單一職責原則 (SRP) 是否更優？
   - **效能與安全性 (Performance & Security)**：Pro 是否使用了更安全的寫法（如防 SQL Injection）或更佳的非同步處理？

### 階段 3：產出對比矩陣 (Comparative Matrix)
在對話中或指定的 Artifact 內輸出 Markdown 表格，列出：
- **檢查項目 (Criteria)**
- **模型 A (Flash) 表現**
- **模型 B (Pro) 表現**
- **勝出者與核心原因**

## 🚨 注意事項
- 避免「長度偏見 (Verbosity Bias)」：不要單純因為 Pro 的程式碼比較長就認為比較好，必須分析其邏輯。
- 避免「位置偏見 (Position Bias)」：評價時應就事論事，以「軟體工程標準」為唯一準則。
- 在本階段**不**產生修正提示詞，僅負責「客觀發現差異」，後續應交由 Reflexion Distiller 技能處理。
