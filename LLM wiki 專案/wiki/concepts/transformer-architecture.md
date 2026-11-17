---
title: "Transformer 架構"
aliases: ["Transformer", "自注意力機制", "Self-Attention"]
type: concept
updated_date: 2026-11-17
tags: [concept, architecture, deep-learning]
---

# Transformer 架構 (Transformer Architecture)

## 概念定義
**Transformer** 是由 Vaswani 等人於 2017 年在論文《Attention Is All You Need》中提出的深度神經網絡架構。其完全揚棄了傳統的循環神經網絡 (RNN) 與卷積神經網絡 (CNN)，純粹依賴**自注意力機制 (Self-Attention)** 來捕捉序列中任意兩個 Token 之間的全局上下文相依關係。

## 關鍵運作機制
核心運算為縮放點積注意力（Scaled Dot-Product Attention）：
$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

```mermaid
flowchart TD
    Input[輸入 Tokens] --> Embed[嵌入層 + 位置編碼]
    Embed --> Block[Transformer 區塊 (Decoder-only)]
    subgraph Block [Transformer Block]
        Attn[多頭自注意力 / MHA / GQA]
        Norm1[RMSNorm / LayerNorm]
        FFN[前饋網絡 / MoE]
        Norm2[RMSNorm / LayerNorm]
        Attn --> Norm1 --> FFN --> Norm2
    end
    Block --> Output[輸出層 (Next Token Prediction)]
```

## 現代 LLM 的架構演進
當今主流大語言模型幾乎皆採用 **Decoder-only** 架構，並經歷了以下演變：
1. **位置編碼**：從 Absolute Positional Encoding 轉向 RoPE (Rotary Position Embedding)。
2. **正規化**：普遍以 RMSNorm 取代 LayerNorm，提升數值穩定性與運算效率。
3. **注意力優化**：由 MHA (Multi-Head) 轉向 MQA / GQA (Grouped-Query Attention)，或 DeepSeek 提出的 MLA (Multi-head Latent Attention) 以壓低 KV 快取開銷。
4. **前饋層 (FFN)**：從 Dense FFN 演進為 [[moe|混合專家模型 (MoE)]]。

## 關聯頁面
- 延伸技術：[[chain-of-thought]]
- 相關實體：[[deepseek-r1]]
