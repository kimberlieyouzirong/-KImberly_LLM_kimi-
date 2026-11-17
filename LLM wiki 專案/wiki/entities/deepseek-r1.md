---
title: "DeepSeek-R1"
aliases: ["DeepSeek R1", "R1", "DeepSeek-R1-Zero"]
type: entity
category: model
updated_date: 2026-11-17
tags: [entity, model, reasoning, rl, open-source]
---

# DeepSeek-R1

## 基本資訊
- **開發機構**：[[deepseek|DeepSeek (深度求索)]]
- **發布時間**：2025-01
- **開源狀態**：開源權重 (MIT License) 與技術報告，包含 R1-Zero, R1 以及多款 Distilled 蒸餾模型 (1.5B ~ 70B)
- **基礎底座**：基於 DeepSeek-V3-Base (671B 總參數，活躍參數約 37B MoE)

## 架構與核心技術亮點
1. **純強化學習激發推理 (DeepSeek-R1-Zero)**：
   - 不經由傳統 SFT（監督微調），直接在 Base 模型上使用大規模強化學習 (GRPO: Group Relative Policy Optimization)。
   - 模型自主展現出「頓悟時刻 (Aha moment)」、自我驗證、錯誤修正與超長 [[chain-of-thought|思維鏈 (CoT)]]。
2. **多階段訓練管線 (DeepSeek-R1)**：
   - 冷啟動數據 (Cold-start data) 微調 $\to$ 第一階段大規模推理導向 RL $\to$ 拒絕採樣與通用 SFT $\to$ 第二階段全場景偏好對齊 RL。
3. **低成本蒸餾 (Distillation)**：
   - 將 R1 的長推理軌跡直接蒸餾給 LLaMA、Qwen 等稠密小模型（如 Qwen-2.5-32B），證明推理能力可透過微調轉移。

## 評測表現
- 在 AIME 2024、MATH-500、Codeforces 等高難度數學與程式競賽基準上，達到與 OpenAI o1 等閉源頂尖推理模型相當的水準。

## 關聯頁面
- 所屬機構：[[deepseek]]
- 核心技術：[[chain-of-thought]], [[transformer-architecture]]
- 綜合綜述：[[reasoning-models-evolution]]
