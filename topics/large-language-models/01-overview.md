# Large Language Models (LLMs) — Overview

## What Are Large Language Models?

Large Language Models (LLMs) are neural networks with billions of parameters, trained on massive text corpora to understand and generate human language. They are built on the **Transformer architecture** (Vaswani et al., 2017) and learn by predicting the next token in a sequence. When scaled beyond a certain parameter threshold, these models exhibit **emergent abilities** — capabilities not present in smaller models — such as in-context learning, chain-of-thought reasoning, and instruction following.

## Why Do LLMs Matter?

LLMs represent a paradigm shift in artificial intelligence:

- **Generalization**: Unlike previous NLP systems built for single tasks, LLMs can perform translation, summarization, question answering, code generation, reasoning, and more — all with a single model.
- **Few-shot and zero-shot learning**: LLMs can solve new tasks from just a few examples (or none), without retraining.
- **Foundation for AI applications**: Nearly all modern AI assistants (ChatGPT, Claude, Gemini), coding tools (Copilot), and enterprise AI systems are powered by LLMs.
- **Economic impact**: LLMs are reshaping industries from software development to healthcare, law, education, and finance.

## The Big Questions

1. **How do LLMs learn?** How does next-token prediction on text lead to general intelligence-like capabilities?
2. **Scaling laws**: What is the relationship between model size, data, compute, and performance? When do we hit diminishing returns?
3. **Alignment**: How do we make LLMs helpful, harmless, and honest? How do we align them with human values?
4. **Reasoning**: Can LLMs truly reason, or are they sophisticated pattern matchers? What are the limits of their reasoning?
5. **Hallucination**: Why do LLMs generate plausible-sounding but false information, and how can this be mitigated?
6. **Efficiency**: How do we make LLMs smaller, faster, and cheaper without sacrificing capability?
7. **Multimodality**: How do we extend LLMs to process images, audio, video, and other modalities natively?

## Historical Timeline

| Year | Milestone |
|------|-----------|
| 1997 | LSTM networks (Hochreiter & Schmidhuber) |
| 2003 | Neural probabilistic language model (Bengio et al.) |
| 2013 | Word2Vec word embeddings (Mikolov et al.) |
| 2014 | Attention mechanism for NMT (Bahdanau et al.) |
| 2017 | Transformer architecture — "Attention Is All You Need" (Vaswani et al.) |
| 2018 | ELMo (Peters et al.), GPT-1 (Radford et al.), BERT (Devlin et al.) |
| 2019 | GPT-2 (Radford et al.) — zero-shot multitask learning |
| 2020 | GPT-3 — 175B parameters, few-shot learning (Brown et al.) |
| 2020 | Scaling laws for neural language models (Kaplan et al.) |
| 2020 | Retrieval-Augmented Generation (Lewis et al.) |
| 2022 | Chinchilla scaling laws (Hoffmann et al.) |
| 2022 | Chain-of-thought prompting (Wei et al.) |
| 2022 | InstructGPT / RLHF (Ouyang et al.) |
| 2022 | ChatGPT released (OpenAI) |
| 2023 | GPT-4, Claude, Llama, open-source LLM explosion |
| 2024 | Llama 3, Mixtral MoE, multimodal models |
| 2025 | DeepSeek-R1 reasoning models, agentic AI |
| 2026 | Autonomous agents, multimodal reasoning, domain-specific LLMs |
