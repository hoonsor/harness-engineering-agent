# 01-常駐馬鞍工程代理# 專案狀態監控表 (PROJECT_STATUS)

- **專案名稱**：駕馭工程代理 (harness-engineering-agent)
- **當前版本**：v0.3.0
- **最後更新**：2026-06-18
- **主要狀態**：開發中 (Development)

---

## 📖 專案程式功能概述

本專案旨在建立一個「常駐馬鞍工程代理 (Resident Harness Engineering Agent)」。
此代理人主要用於：
1. 為其他 AI 代理與系統搭建穩固的**測試駕馭 (Test Harness)**、**安全駕馭 (Safety Harness / Guardrails)** 與**評估駕馭 (Evaluation Harness)** 系統。
2. 作為常駐後台進程，持久化監控系統運行、捕捉工具呼叫錯誤並進行自動恢復與檢修。

---

## 📋 版本歷程

| 版本 | 日期 | 更新內容摘要 | 狀態 |
| :--- | :--- | :--- | :--- |
| v0.3.0 | 2026-06-18 | 補充完整駕馭工程版圖：新增 `llm-red-team-garak` 安全紅隊演練技能 | ✅ 完成 |
| v0.2.0 | 2026-06-18 | 新增「模型比較與知識蒸餾」架構，實作 Promptfoo、DeepEval 與 Reflexion 本地技能 | ✅ 完成 |
| v0.1.0 | 2026-06-18 | 專案初始化，建立基本結構，導入核心測試與防護欄技能 | ✅ 完成 |

## 待辦事項 (Backlog)

---

## 🎯 目前專案進度進展狀態

### 主要任務

- [x] 建立專案技能資料夾 `.agents/skills/` (v0.1.0)
- [x] 從冷儲存區導入 `tool-use-guardian` (工具使用監管) (v0.1.0)
- [x] 從冷儲存區導入 `agent-evaluation` (代理人評估) (v0.1.0)
- [x] 從冷儲存區導入 `llm-evaluation` (LLM 應用評估) (v0.1.0)
- [x] 從冷儲存區導入 `context-guardian` (上下文監護) (v0.1.0)
- [ ] 撰寫專案引導指南 `ANTIGRAVITY.md`
- [ ] 建立常駐馬鞍工程代理之主控制架構 (Scaffold)

### 次要任務

- [x] 設定專案 Git 倉庫與遠端備份 (v0.1.0)

---

## 📝 歷次修訂紀錄

### 當前方向

- 優先完成基礎設施部署，導入專案層級的 Harness Engineering 核心技能。下一步將建立控制與評估架構。
