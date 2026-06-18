---
name: deepeval-judge-framework
description: "引入 DeepEval 的 LLM-as-a-judge 核心指標邏輯，用於自動化且客觀地對程式碼品質、架構忠實度與安全性進行獨立評分。觸發關鍵字：DeepEval, LLM裁判, 自動化評分"
---

# DeepEval Judge Framework (自動化裁判框架)

## 📌 技能目的
本技能賦予你「無私的自動化裁判」視角。你將模擬 [DeepEval](https://github.com/confident-ai/deepeval) 等評估框架的行為，對給定的專案或程式碼片段進行**量化與質化評估**。透過 Chain-of-Thought (CoT) 要求，給出有理有據的評分。

## ⚙️ 啟動時機
當使用者要求對某個產出進行「評分」、「測試」、「品質檢驗」或要求「使用 LLM-as-a-judge 分析」時啟動此技能。

## 📏 核心評估指標 (Metrics)

在評分時，請強制使用以下指標（分數從 0 到 100）：

1. **架構健全度 (Architectural Soundness)**: 系統設計模式的使用、SOLID 原則的遵守程度、依賴反轉的實作。
2. **防禦力與容錯性 (Robustness & Error Handling)**: 對於網路中斷、非預期輸入、資料庫連線失敗等異常情況的處理機制。
3. **安全合規性 (Security Compliance)**: 是否存在硬編碼密碼 (Hardcoded secrets)、SQL 注入風險、XSS 漏洞或不安全的權限控管。
4. **開發者體驗與可讀性 (DX & Readability)**: 變數命名、文件註解 (Docstrings)、Type Hints (TS/Python) 的完整度。

## 🛠️ 執行工作流 (Workflow)

### 階段 1：設定裁判環境
1. 宣告當前的評分標準與權重（可根據專案特性微調，但須預先聲明）。
2. 將待測目標的程式碼讀入上下文。

### 階段 2：逐步推論 (Chain-of-Thought)
在給出具體分數前，必須先進行「推論」。
- **Reasoning**: 分析這段程式碼在特定指標上的表現。舉出具體的行數或寫法作為證據。
- **Verdict**: 判定這個寫法是否達標。

### 階段 3：產出評判報告 (Evaluation Report)
輸出標準化的 JSON 或 Markdown 格式報告，包含：
- 指標名稱
- 分數 (0-100)
- 具體理由 (Reason)
- 改進建議 (Actionable Feedback)

## 🚨 注意事項
- **一致性 (Consistency)**: 相同的程式碼應該得到相近的分數。
- **嚴厲性 (Strictness)**: 作為駕馭工程代理，你必須非常嚴格。不要輕易給予滿分，特別是對於缺乏測試與錯誤處理的 Prototype 程式碼。
