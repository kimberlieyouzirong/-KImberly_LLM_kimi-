---
title: "思維鏈 (Chain of Thought, CoT)"
aliases: ["CoT", "Chain of Thought", "逐步推理"]
type: concept
updated_date: 2026-11-17
tags: [concept, reasoning, prompt-engineering]
---

# 思維鏈 (Chain of Thought, CoT)

## 概念定義
**思維鏈 (Chain of Thought, CoT)** 是一種引導大語言模型 (LLM) 在給出最終答案前，先生成中間推理步驟（intermediate reasoning steps）的技術。它模仿人類解決複雜多步驟問題時的心智歷程，能大幅提高模型在算術、常識推理與符號邏輯上的準確率。

## 關鍵運作機制
傳統 Prompting 直接要求模型輸出答案：
$$Q \to A$$

而 CoT 要求模型將推理過程顯式化：
$$Q \to r_1 \to r_2 \to \dots \to r_k \to A$$

```mermaid
flowchart LR
    subgraph Standard [標準 Prompt]
        Q1[問題輸入] --> A1[直接輸出解答 (容易幻覺/出錯)]
    end

    subgraph CoT [思維鏈 Prompt]
        Q2[問題輸入] --> R1[步驟 1: 拆解子問題]
        R1 --> R2[步驟 2: 中間運算]
        R2 --> A2[步驟 3: 得出最終結論]
    end
```

## 技術演進歷程
1. **Few-Shot CoT**：[[source-chain-of-thought-wei-2022]] 首度提出，在 Prompt 範例中加入「一步一步思考」的解題過程。
2. **Zero-Shot CoT**：Kojima 等人發現只要在結尾加入 `"Let's think step by step"`，即可在無示範例的情況下激發 CoT。
3. **自我一致性 (Self-Consistency)**：Wang 等人提出採樣多條不同的推理路徑，投票選出最高共識解答。
4. **內在化推理模型 (Test-time RL / System 2 Thinking)**：如 OpenAI o1/o3 與 [[deepseek-r1]]，透過純強化學習 (RL) 讓模型自主學會反思、回溯、驗證與長文本思維鏈，脫離單純人工 prompt 誘導。

## 關聯頁面
- 理論基礎：[[transformer-architecture]]
- 實體案例：[[deepseek-r1]]
- 綜述報告：[[reasoning-models-evolution]]
- 原始論文：[[source-chain-of-thought-wei-2022]]
