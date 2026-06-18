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

---

## 🛠️ 開發與協作規範

### 1. 變更管理與狀態追蹤
*   本專案的根目錄必須維護 [PROJECT_STATUS.md](file:///d:/Antigravity/01-常駐馬鞍工程代理/PROJECT_STATUS.md)。
*   每次代碼變更或技能導入後，必須更新其「版本歷程」與「目前專案進度進展狀態」。

### 2. 測試與評估優先
*   開發任何 Harness 組件前，應先撰寫單元/整合測試案例（遵循 TDD 工作流）。
*   利用 `.agents/skills/agent-evaluation` 指南對代理人模型進行多輪統計測試，確保其通過率不低於基線。
