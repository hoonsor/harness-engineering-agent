# 01-常駐馬鞍工程代理 - 專案引導指南 (ANTIGRAVITY.md)

## 📌 專案簡介
本專案專注於開發與維護「常駐馬鞍工程代理」，為異步 AI Swarm 協作與後台自動化測試建立支撐框架 (Scaffold/Harness)。

---

## 📂 專案結構與技能地圖

### 1. 專案專屬隱藏技能目錄 (`.agents/skills/`)
本專案已本地化配置了以下專屬技能，用於引導 AI 在此專案中開發時的行為：
*   **`tool-use-guardian`**：工具呼叫可靠性包裝器，提供自動重試與 checkpoint 恢復。
*   **`agent-evaluation`**：代理人行為統計學評估與 AgentBench/Tau-bench 基準整合。
*   **`llm-evaluation`**：自動化評估指標與 LLM-as-Judge 評分系統架構。
*   **`context-guardian`**：防範 System Prompt 被污染的上下文防護網。

### 2. 核心技術棧
*   **語言與環境**：PowerShell (Windows)、Python 3.12+、Node.js。
*   **自動化驅動**：Playwright / pytest。

### 3. 駕馭工程專屬工作流 (Harness Engineering Workflows)
*   **#執行模型比較與蒸餾 (Model Comparison & Distillation)**:
    1.  **載入專案**：接收使用者指定的「低階模型產出路徑」與「高階模型產出路徑」。
    2.  **平行比對**：載入 `promptfoo-comparative-evaluator` 技能，產生雙方結構與程式碼的對比矩陣 (Comparative Matrix)。
    3.  **自動化評分**：載入 `deepeval-judge-framework` 技能，對雙方進行獨立打分，產生包含推論 (CoT) 的評估報告。
    4.  **知識蒸餾**：載入 `reflexion-prompt-distiller` 技能，將評估報告中的缺失轉換為通用的系統防護欄。
    5.  **產出**：輸出 `elevation_prompt.md` 供使用者後續注入至低階模型。
*   **#執行安全紅隊演練 (Security Red Teaming)**:
    1.  **載入技能**：啟動 `llm-red-team-garak` 技能，針對指定的模型或 Agent 發動自動化攻擊（含 Prompt Injection 與 Jailbreak）。
    2.  **產出報告**：輸出 `red_team_report.md`，分析安全漏洞並提供具體修復方案。

---

## 🛠️ 開發與協作規範

### 1. 變更管理與狀態追蹤
*   本專案的根目錄必須維護 [PROJECT_STATUS.md](file:///d:/Antigravity/01-常駐馬鞍工程代理/PROJECT_STATUS.md)。
*   每次代碼變更或技能導入後，必須更新其「版本歷程」與「目前專案進度進展狀態」。

### 2. 測試與評估優先
*   開發任何 Harness 組件前，應先撰寫單元/整合測試案例（遵循 TDD 工作流）。
*   利用 `.agents/skills/agent-evaluation` 指南對代理人模型進行多輪統計測試，確保其通過率不低於基線。
