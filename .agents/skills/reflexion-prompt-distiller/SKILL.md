---
name: reflexion-prompt-distiller
description: "基於 Reflexion 與 DSPy 的概念，將程式碼評估與比對的結果（教訓），提煉為可用於指引低階模型（知識蒸餾）的「昇華提示詞 (Elevation Prompt)」。觸發關鍵字：知識蒸餾、提煉提示詞、Reflexion"
---

# Reflexion Prompt Distiller (反射與提示詞蒸餾器)

## 📌 技能目的
本技能是模型能力提升的關鍵。當「Comparative Evaluator」找出了雙方差異，且「DeepEval Judge」給出了缺失的具體原因後，本技能負責將這些分析結果（通常冗長且具體於特定程式碼）**抽象化、通則化**，最終蒸餾成一組強而有力的「系統提示詞」或「防護欄規則」。
當低階模型（如 Gemini Flash）載入這組蒸餾後的提示詞，便能在該領域發揮出接近高階模型（如 Gemini Pro）的水準。

## ⚙️ 啟動時機
當使用者要求「產生指引」、「提煉規則」、「進行知識蒸餾」或在模型比對與評估完成後自動啟動。

## 🛠️ 執行工作流 (Workflow)

### 階段 1：收集批判與教訓 (Collect Critiques & Lessons)
1. 讀取先前的比對報告或評分報告。
2. 提取出所有「高階模型做對了，但低階模型做錯了或忽略了」的關鍵點。

### 階段 2：模式抽象化 (Pattern Abstraction)
將具體的程式碼錯誤轉化為架構或行為上的「原則 (Principles)」。
*   *範例（具體）*：「Flash 忘了在 user_id 查詢前加 try-catch，而 Pro 有加。」
*   *範例（抽象）*：「針對所有外部資源操作（DB/API），必須強制實作邊界容錯與完整的 Exception 捕捉機制。」

### 階段 3：建構昇華提示詞 (Construct Elevation Prompt)
撰寫一組對 LLM 高度友善的系統指令。這組指令必須：
1. **角色賦予 (Role-playing)**：定義一個嚴謹的專家角色。
2. **負面約束 (Negative Constraints)**：明確指出不該做的事（基於 Flash 之前犯的錯）。
3. **正面強制規範 (Positive Mandatory Rules)**：明確要求必須包含的架構層次（如 DTO, Type hint, Error handling）。
4. **檢查清單 (Self-Correction Checklist)**：要求模型在產出結果前，先透過一段 `<thinking>` 區塊檢查是否滿足上述規範。

## 📄 產出格式範例

請將結果輸出為名為 `elevation_prompt.md` 的 Artifact，格式如下：

```xml
<SYSTEM_INSTRUCTION>
你是頂級架構師。在撰寫程式碼時，你必須遵守以下「絕對防護欄」：

[原則 1：例如 - 強制型別與防禦性邊界檢查]
[原則 2：例如 - 模組解耦與依賴注入]

在輸出任何程式碼前，請先在 <scratchpad> 中逐一確認你是否已經實作了上述防護欄機制。如果沒有，請重新設計你的程式碼結構。
</SYSTEM_INSTRUCTION>
```

## 🚨 注意事項
- 提示詞應該盡量簡潔有力，過長的提示詞會稀釋低階模型的注意力 (Attention Span)。
- 使用 XML 標籤（如 `<rule>`, `<constraint>`, `<thinking>`）能夠有效增強低階模型遵循指令的能力。
