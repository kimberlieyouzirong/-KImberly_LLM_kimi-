---
title: "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models"
aliases: ["Wei et al. 2022", "CoT 原始論文"]
type: source
date_published: 2022-01-28
ingested_date: 2026-11-17
authors: ["Jason Wei", "Xuezhi Wang", "Dale Schuurmans", "Maarten Bosma", "Ed Chi", "Quoc Le", "Denny Zhou"]
organization: ["Google Research, Brain Team"]
original_url: "https://arxiv.org/abs/2201.11903"
tags: [source, paper, cot, reasoning]
---

# Chain-of-Thought Prompting Elicits Reasoning in Large Language Models

## 核心摘要（TL;DR）
本篇開創性論文證明：只需在 Few-Shot Prompt 中為示範例加入「中間推理鏈條」，就能引導大語言模型自主產生推理過程，進而大幅突破算術（GSM8K、SVAMP）、常識推理與符號操作等複雜任務的瓶頸。

## 關鍵貢獻與方法
1. **提出 CoT Prompting 方法**：打破過往直接將題目映對到解答 $(Q \to A)$ 的限制，改為 $(Q \to \text{Reasoning} \to A)$。
2. **湧現特徵 (Emergent Ability)**：
   - CoT 的性能提升僅在模型規模足夠大（如 PaLM 540B、GPT-3 175B）時才會顯著湧現；小型模型產生 CoT 往往反而容易產生幻覺。
3. **無須微調權重**：完全透過 In-Context Learning 達成，不改變任何模型參數。

## 實驗與重要結論
- 在小學數學題庫 **GSM8K** 上，PaLM 540B 配合 CoT 的準確率從原本標準 Prompt 的 17.9% 飆升至 56.9%，大幅縮短與人類平均水準的差距。

## 與其他工作之關聯與演化
- 本篇文獻催生了後續的 Zero-Shot CoT ("Let's think step by step")、Tree of Thoughts (ToT) 以及 2024~2025 年以強化學習驅動的自主推理模型（如 OpenAI o1, [[deepseek-r1]]）。

## 關聯概念與實體
- 核心概念：[[chain-of-thought]]
- 相關實體：[[google-deepmind]]
- 綜述回流：[[reasoning-models-evolution]]
