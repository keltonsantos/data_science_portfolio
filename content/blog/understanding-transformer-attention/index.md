---
title: "Understanding Transformer Attention from Scratch"
date: 2026-05-10
description: "A ground-up explanation of how self-attention works in transformer models, with code examples in PyTorch."
tags: ["NLP", "Transformers", "Deep Learning", "PyTorch"]
showTableOfContents: true
---

## Introduction

*(Write your intro here — hook the reader, explain what they'll learn.)*

## What is attention?

*(Explain the intuition — why attention was invented, what problem it solves.)*

## The math

The attention mechanism computes:

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$

Where:
- **Q** = query matrix
- **K** = key matrix  
- **V** = value matrix
- **d_k** = dimension of the keys

## Code example

```python
import torch
import torch.nn.functional as F

def scaled_dot_product_attention(Q, K, V):
    d_k = Q.size(-1)
    scores = torch.matmul(Q, K.transpose(-2, -1)) / d_k ** 0.5
    weights = F.softmax(scores, dim=-1)
    return torch.matmul(weights, V)
```

## Conclusion

*(Summarize key takeaways and point to further reading.)*

## References

- Vaswani et al. (2017). [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
- The Annotated Transformer — Harvard NLP
