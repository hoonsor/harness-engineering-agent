# 駕馭工程代理 (Harness Engineering Agent)

> 一個專業、常駐於本地的「駕馭工程 (Harness Engineering)」代理，專注於 LLM 的平行比對、評估、知識蒸餾與安全紅隊演練。

## 📖 專案簡介 (Overview)
駕馭工程代理 (Harness Engineering Agent) 是一個為了解決「高低階大型語言模型產出落差」而生的自動化評估系統。它的主要任務是接收由低階模型（如 Gemini Flash）與高階模型（如 Gemini Pro）在相同 Prompt 下生成的程式專案，並透過嚴格的平行審查與測試框架進行比對。

透過這個系統，開發者無需手動檢閱上千行的程式碼差異。代理會自動扮演無私的裁判，找出低階模型在「防禦性編程、架構解耦、安全性」上的盲點。更重要的是，它具備「知識蒸餾」的能力，能將高階模型的優勢提煉為通用的「昇華提示詞 (Elevation Prompt)」，讓低階模型在未來的任務中也能具備專家級的思維深度與防護機制。此專案專為需要建立高穩定度 AI Agent 的團隊與開發者設計。

## ✨ 核心功能 (Key Features)
- **平行比對 (Side-by-side Evaluation)**：基於 Promptfoo 概念，自動針對雙方專案進行結構與程式碼的盲測對比，產出詳細的差異矩陣。
- **自動化裁判 (LLM-as-a-judge)**：整合 DeepEval 評估指標，對系統的架構健全度、容錯性與安全合規性給出量化分數與推論。
- **知識蒸餾 (Knowledge Distillation)**：基於 Reflexion 架構，提煉高階模型的防護欄原則，產出可供低階模型注入的系統指令。
- **紅隊安全演練 (Security Red Teaming)**：內建 Garak/PyRIT 風格的對抗性測試，自動掃描 Agent 的提示詞注入漏洞與越獄風險。

## 🛠 技術棧 (Tech Stack)
- **評估框架概念**：Promptfoo, DeepEval, Reflexion, DSPy, Garak
- **自動化代理引擎**：Google Antigravity SDK
- **開發環境**：Python / Node.js
- **版控與部署**：Git / GitHub

## 🚀 快速開始 (Quick Start)

### 執行駕馭工作流
本專案透過 `ANTIGRAVITY.md` 中定義的專屬指令進行操作：

```bash
# 啟動模型比對與知識蒸餾流程
#執行模型比較與蒸餾

# 啟動自動化紅隊漏洞掃描
#執行安全紅隊演練
```

## 📁 專案結構 (Project Structure)
```text
/
 ├── .agents/
 │    └── skills/                        # 本地化部署的駕馭工程核心技能
 │         ├── promptfoo-comparative-evaluator/  # 平行比對技能
 │         ├── deepeval-judge-framework/         # 裁判評分技能
 │         ├── reflexion-prompt-distiller/       # 知識蒸餾技能
 │         └── llm-red-team-garak/               # 紅隊演練技能
 ├── PROJECT_STATUS.md                   # 專案版本與狀態監控表
 └── ANTIGRAVITY.md                      # 開發與流程指導原則
```

## 🔄 最新更新 (Recent Updates)
- **v0.3.0 (2026-06-18)**: 補充完整駕馭工程版圖：新增 `llm-red-team-garak` 安全紅隊演練技能。
- **v0.2.0 (2026-06-18)**: 新增「模型比較與知識蒸餾」架構，實作 Promptfoo、DeepEval 與 Reflexion 本地技能。
- **v0.1.0 (2026-06-18)**: 專案初始化，建立基本結構，導入核心測試與防護欄技能。

---
*Generated and maintained by Google Antigravity Architect*
