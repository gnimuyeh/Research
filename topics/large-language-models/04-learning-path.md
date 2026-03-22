# Learning Path: Large Language Models

A step-by-step curriculum from beginner to advanced. Each stage includes specific resources verified via web search.

---

## Stage 1: Prerequisites (2–4 weeks)

**Goal:** Build the mathematical and machine learning foundations.

| Topic | Resource | Format | Cost |
|-------|----------|--------|------|
| Linear algebra | 3Blue1Brown — *Essence of Linear Algebra* | YouTube | Free |
| Probability & statistics | Khan Academy — Statistics & Probability | Online | Free |
| Python programming | Python.org official tutorial | Online | Free |
| Neural networks intro | 3Blue1Brown — *Neural Networks* series | YouTube | Free |
| Deep learning foundations | Andrew Ng — *Deep Learning Specialization* | Coursera | Free to audit |

**Milestone:** You can explain backpropagation, gradient descent, and why neural networks work.

---

## Stage 2: NLP Foundations (2–3 weeks)

**Goal:** Understand the NLP problems LLMs are designed to solve.

| Topic | Resource | Format | Cost |
|-------|----------|--------|------|
| NLP overview | *Speech and Language Processing* — Jurafsky & Martin (3rd ed. draft) | Free textbook (online) | Free |
| Word embeddings | Read: Mikolov et al. — "Efficient Estimation of Word Representations in Vector Space" (2013) | Paper | Free |
| Sequence models | Andrew Ng — Sequence Models course (DL Specialization, Course 5) | Coursera | Free to audit |

**Milestone:** You understand tokenization, word embeddings, language modeling, and RNN/LSTM basics.

---

## Stage 3: The Transformer (2–3 weeks)

**Goal:** Deeply understand the architecture that powers all modern LLMs.

| Topic | Resource | Format | Cost |
|-------|----------|--------|------|
| Attention mechanism | Read: Bahdanau et al. — "Neural Machine Translation by Jointly Learning to Align and Translate" (2014) | Paper | Free |
| The Transformer | Read: Vaswani et al. — "Attention Is All You Need" (2017) | Paper ([arXiv](https://arxiv.org/abs/1706.03762)) | Free |
| Visual explanation | Jay Alammar — *The Illustrated Transformer* | Blog post | Free |
| Code implementation | Andrej Karpathy — "Let's build GPT from scratch" | YouTube | Free |
| Textbook | Sebastian Raschka — *Build a Large Language Model (from Scratch)* | Book | ~$40 |

**Milestone:** You can implement a small Transformer from scratch and explain multi-head attention, positional encoding, and the training loop.

---

## Stage 4: Pre-training & Scaling (2–3 weeks)

**Goal:** Understand how LLMs are trained at scale and what drives their performance.

| Topic | Resource | Format | Cost |
|-------|----------|--------|------|
| GPT architecture evolution | Read: GPT-1 (2018), GPT-2 (2019), GPT-3 (2020) papers | Papers | Free |
| BERT vs GPT | Read: BERT paper (Devlin et al., 2018) | Paper ([arXiv](https://arxiv.org/abs/1810.04805)) | Free |
| Scaling laws | Read: Kaplan et al. (2020) and Chinchilla/Hoffmann et al. (2022) | Papers | Free |
| Training infrastructure | Google DeepMind — *How to Scale Your Model* | Free ebook | Free |
| Comprehensive survey | Read: Zhao et al. — "A Survey of Large Language Models" (2023) | Paper ([arXiv](https://arxiv.org/abs/2303.18223)) | Free |

**Milestone:** You can explain CLM vs MLM, why scale matters, compute-optimal training, and the trade-offs between model size and data.

---

## Stage 5: Alignment & RLHF (1–2 weeks)

**Goal:** Understand how raw LLMs are turned into helpful, safe AI assistants.

| Topic | Resource | Format | Cost |
|-------|----------|--------|------|
| RLHF pipeline | Read: Ouyang et al. — "Training language models to follow instructions with human feedback" (2022) | Paper ([arXiv](https://arxiv.org/abs/2203.02155)) | Free |
| RLHF explainer | Chip Huyen — "RLHF: Reinforcement Learning from Human Feedback" | Blog post | Free |
| DPO | Read: Rafailov et al. — "Direct Preference Optimization" (2023) | Paper | Free |
| Constitutional AI | Read: Bai et al. — "Constitutional AI" (2022) | Paper | Free |
| Course | DeepLearning.AI & AWS — *Generative AI with Large Language Models* | Coursera | Free to audit |

**Milestone:** You can explain the SFT → RM → PPO pipeline, why alignment works, and alternatives like DPO and Constitutional AI.

---

## Stage 6: Prompting & Practical Use (1–2 weeks)

**Goal:** Learn to effectively use and prompt LLMs.

| Topic | Resource | Format | Cost |
|-------|----------|--------|------|
| Few-shot learning | Read: Brown et al. — "Language Models are Few-Shot Learners" (GPT-3, 2020) | Paper | Free |
| Chain-of-thought | Read: Wei et al. — "Chain-of-Thought Prompting Elicits Reasoning in Large Language Models" (2022) | Paper ([arXiv](https://arxiv.org/abs/2201.11903)) | Free |
| ReAct | Read: Yao et al. — "ReAct: Synergizing Reasoning and Acting" (2023) | Paper | Free |
| Practical prompting | DeepLearning.AI — *ChatGPT Prompt Engineering for Developers* | Short course | Free |
| HuggingFace ecosystem | HuggingFace NLP Course | Online course | Free |

**Milestone:** You can design effective prompts, use CoT reasoning, and build applications with the HuggingFace Transformers library.

---

## Stage 7: Advanced Topics (2–4 weeks)

**Goal:** Explore the cutting edge of LLM research and engineering.

| Topic | Resource | Format | Cost |
|-------|----------|--------|------|
| RAG | Read: Lewis et al. — "Retrieval-Augmented Generation" (2020) | Paper ([arXiv](https://arxiv.org/abs/2005.11401)) | Free |
| Fine-tuning (LoRA) | Read: Hu et al. — "LoRA: Low-Rank Adaptation of Large Language Models" (2021) | Paper | Free |
| Mixture of Experts | Read: Fedus et al. — "Switch Transformers" (2022) | Paper | Free |
| Multimodal LLMs | Explore: GPT-4V technical report, LLaVA paper | Papers | Free |
| Agentic AI | Read: Yao et al. — ReAct; explore LangChain, CrewAI frameworks | Papers + docs | Free |
| Applied LLM building | *Hands-On Large Language Models* — Jay Alammar & Maarten Grootendorst | Book | ~$50 |
| Full-stack LLM apps | Full Stack LLM Bootcamp | Online recordings | Free |

**Milestone:** You can build RAG systems, fine-tune models with LoRA, and design agentic AI applications.

---

## Stage 8: Research Frontiers (Ongoing)

**Goal:** Stay current with the rapidly evolving field.

| Activity | Resource |
|----------|----------|
| Weekly paper tracking | Sebastian Raschka's *Ahead of AI* newsletter |
| Paper discussions | r/MachineLearning, r/LocalLLaMA (Reddit) |
| Arxiv tracking | [Papers With Code](https://paperswithcode.com/) — LLM section |
| Open-source models | HuggingFace model hub, Llama, Mistral, DeepSeek releases |
| Benchmarks | MMLU, HumanEval, MATH, ARC, LiveBench |
| Stanford course | CS324 — Large Language Models (Stanford, lecture notes online) |

---

## Quick-Start Path (for the impatient)

If you want the fastest path to understanding LLMs:

1. Watch Andrej Karpathy's "Let's build GPT from scratch" (2 hours)
2. Read *The Hundred-Page Language Models Book* by Andriy Burkov
3. Take the HuggingFace NLP Course
4. Read the Transformer paper and the GPT-3 paper
5. Build something with the HuggingFace Transformers library
