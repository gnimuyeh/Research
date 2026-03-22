# Foundational Papers on Large Language Models

A curated list of the most important papers in the development of LLMs, organized chronologically. Every citation below has been verified via web search.

---

## Pre-Transformer Foundations

### 1. Long Short-Term Memory (LSTM)
- **Authors:** Sepp Hochreiter, Jürgen Schmidhuber
- **Year:** 1997
- **Venue:** Neural Computation
- **Why it matters:** Introduced the LSTM architecture, solving the vanishing gradient problem in recurrent neural networks. LSTMs became the dominant architecture for sequence modeling for nearly two decades and were a direct predecessor to modern language models.

### 2. A Neural Probabilistic Language Model
- **Authors:** Yoshua Bengio, Réjean Ducharme, Pascal Vincent, Christian Jauvin
- **Year:** 2003
- **Venue:** Journal of Machine Learning Research (JMLR)
- **Why it matters:** Proposed using neural networks to learn "distributed representations" of words (what we now call word embeddings) for language modeling. This foundational idea — that words can be represented as dense vectors in continuous space — underpins all modern LLMs.

### 3. Efficient Estimation of Word Representations in Vector Space (Word2Vec)
- **Authors:** Tomas Mikolov, Kai Chen, Greg Corrado, Jeffrey Dean
- **Year:** 2013
- **Venue:** ICLR 2013 Workshop Track
- **ArXiv:** [1301.3781](https://arxiv.org/abs/1301.3781)
- **Why it matters:** Introduced the CBOW and Skip-gram models for learning word embeddings efficiently at scale. Word2Vec demonstrated that word vectors capture semantic relationships (e.g., "king - man + woman ≈ queen") and became one of the most cited papers in NLP with 195,000+ citations.

### 4. Distributed Representations of Words and Phrases and their Compositionality
- **Authors:** Tomas Mikolov, Ilya Sutskever, Kai Chen, Greg Corrado, Jeffrey Dean
- **Year:** 2013
- **Venue:** NeurIPS 2013
- **ArXiv:** [1310.4546](https://arxiv.org/abs/1310.4546)
- **Why it matters:** Follow-up to Word2Vec introducing negative sampling and phrase-level embeddings, making training more efficient and practical.

---

## The Attention Revolution

### 5. Neural Machine Translation by Jointly Learning to Align and Translate
- **Authors:** Dzmitry Bahdanau, Kyunghyun Cho, Yoshua Bengio
- **Year:** 2014 (published at ICLR 2015)
- **ArXiv:** [1409.0473](https://arxiv.org/abs/1409.0473)
- **Why it matters:** Introduced the **attention mechanism** for neural machine translation, allowing models to dynamically focus on relevant parts of the input. This removed the information bottleneck of fixed-length context vectors and directly inspired the Transformer.

### 6. Attention Is All You Need
- **Authors:** Ashish Vaswani, Noam Shazeer, Niki Parmar, Jakob Uszkoreit, Llion Jones, Aidan N. Gomez, Łukasz Kaiser, Illia Polosukhin
- **Year:** 2017
- **Venue:** NeurIPS 2017
- **ArXiv:** [1706.03762](https://arxiv.org/abs/1706.03762)
- **Why it matters:** **The most important paper in LLM history.** Introduced the Transformer architecture, which entirely replaced recurrence with self-attention. Key innovations include multi-head attention, scaled dot-product attention, and positional encoding. Every major LLM today (GPT, Claude, Llama, Gemini) is built on this architecture. All eight authors were equal contributors from Google Brain/Research and University of Toronto.

---

## Pre-training & the Birth of LLMs

### 7. Deep Contextualized Word Representations (ELMo)
- **Authors:** Matthew E. Peters, Mark Neumann, Mohit Iyyer, Matt Gardner, Christopher Clark, Kenton Lee, Luke Zettlemoyer
- **Year:** 2018
- **Venue:** NAACL 2018
- **Why it matters:** Showed that word representations should be contextualized (the same word gets different embeddings in different contexts), using deep bidirectional LSTMs. A stepping stone from static embeddings to full pre-trained language models.

### 8. Improving Language Understanding by Generative Pre-Training (GPT-1)
- **Authors:** Alec Radford, Karthik Narasimhan, Tim Salimans, Ilya Sutskever
- **Year:** 2018
- **Venue:** OpenAI Technical Report
- **Why it matters:** Introduced the **decoder-only Transformer** approach: pre-train a language model on a large corpus via next-token prediction, then fine-tune on downstream tasks. This autoregressive pre-training paradigm is the foundation of GPT-2, GPT-3, GPT-4, Claude, and all modern generative LLMs.

### 9. BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding
- **Authors:** Jacob Devlin, Ming-Wei Chang, Kenton Lee, Kristina Toutanova
- **Year:** 2018
- **Venue:** NAACL 2019
- **ArXiv:** [1810.04805](https://arxiv.org/abs/1810.04805)
- **Why it matters:** Introduced bidirectional pre-training using masked language modeling (MLM). BERT dominated NLP benchmarks and popularized the pre-train → fine-tune paradigm for encoder-style models. While decoder-only models (GPT) eventually won for generation, BERT remains influential for classification, search, and embedding tasks.

### 10. Language Models are Unsupervised Multitask Learners (GPT-2)
- **Authors:** Alec Radford, Jeffrey Wu, Rewon Child, David Luan, Dario Amodei, Ilya Sutskever
- **Year:** 2019
- **Venue:** OpenAI Technical Report
- **Why it matters:** Scaled up GPT to 1.5B parameters and demonstrated that language models can perform tasks zero-shot without any fine-tuning. OpenAI initially withheld the full model over misuse concerns, sparking debate about responsible AI release.

---

## The Modern LLM Era

### 11. Language Models are Few-Shot Learners (GPT-3)
- **Authors:** Tom Brown, Benjamin Mann, Nick Ryder, et al.
- **Year:** 2020
- **Venue:** NeurIPS 2020
- **ArXiv:** [2005.14165](https://arxiv.org/abs/2005.14165)
- **Why it matters:** **Marked the entry into the modern LLM era.** Scaled to 175B parameters and showed that LLMs can learn new tasks from just a few examples in the prompt (few-shot learning) without gradient updates. Demonstrated emergent in-context learning abilities and kicked off the "foundation model" paradigm.

### 12. Scaling Laws for Neural Language Models
- **Authors:** Jared Kaplan, Sam McCandlish, Tom Henighan, Tom B. Brown, Benjamin Chess, Rewon Child, Scott Gray, Alec Radford, Jeffrey Wu, Dario Amodei
- **Year:** 2020
- **Venue:** OpenAI (arXiv)
- **ArXiv:** [2001.08361](https://arxiv.org/abs/2001.08361)
- **Why it matters:** Discovered that LLM performance follows predictable **power-law relationships** with model size, dataset size, and compute. Argued that model size should grow faster than data. These scaling laws guided the development of GPT-3 and subsequent models.

### 13. Training Compute-Optimal Large Language Models (Chinchilla)
- **Authors:** Jordan Hoffmann, Sebastian Borgeaud, Arthur Mensch, et al.
- **Year:** 2022
- **Venue:** NeurIPS 2022
- **ArXiv:** [2203.15556](https://arxiv.org/abs/2203.15556)
- **Why it matters:** **Revised the scaling laws.** Showed that most LLMs were undertrained — model size and training data should be scaled equally (~20 tokens per parameter). Their 70B Chinchilla model outperformed the 280B Gopher using the same compute budget. This shifted the industry toward training smaller models on more data.

### 14. Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks (RAG)
- **Authors:** Patrick Lewis, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich Küttler, Mike Lewis, Wen-tau Yih, Tim Rocktäschel, Sebastian Riedel, Douwe Kiela
- **Year:** 2020
- **Venue:** NeurIPS 2020
- **ArXiv:** [2005.11401](https://arxiv.org/abs/2005.11401)
- **Why it matters:** Coined the term "Retrieval-Augmented Generation" and showed that combining LLMs with external knowledge retrieval produces more factual, specific, and up-to-date outputs. RAG is now a standard technique used in most production LLM applications to reduce hallucination.

---

## Alignment & Reasoning

### 15. Training Language Models to Follow Instructions with Human Feedback (InstructGPT)
- **Authors:** Long Ouyang, Jeff Wu, Xu Jiang, et al. (20 authors)
- **Year:** 2022
- **Venue:** NeurIPS 2022
- **ArXiv:** [2203.02155](https://arxiv.org/abs/2203.02155)
- **Why it matters:** Introduced the **RLHF pipeline** (Supervised Fine-Tuning → Reward Model → PPO) for aligning LLMs with human preferences. A 1.3B InstructGPT model was preferred by humans over the 175B GPT-3 (100x larger), proving that alignment is more cost-effective than scaling alone. This technique became the standard for training ChatGPT, Claude, and all conversational AI.

### 16. Chain-of-Thought Prompting Elicits Reasoning in Large Language Models
- **Authors:** Jason Wei, Xuezhi Wang, Dale Schuurmans, Maarten Bosma, Brian Ichter, Fei Xia, Ed Chi, Quoc Le, Denny Zhou
- **Year:** 2022
- **Venue:** NeurIPS 2022
- **ArXiv:** [2201.11903](https://arxiv.org/abs/2201.11903)
- **Why it matters:** Showed that prompting LLMs to produce intermediate reasoning steps ("chain of thought") dramatically improves performance on math, logic, and commonsense tasks. An emergent ability of scale — only works with models ≥100B parameters. Spawned an entire research area on LLM reasoning.

### 17. ReAct: Synergizing Reasoning and Acting in Language Models
- **Authors:** Shunyu Yao, Jeffrey Zhao, Dian Yu, Nan Du, Izhak Shafran, Karthik Narasimhan, Yuan Cao
- **Year:** 2023
- **Venue:** ICLR 2023
- **ArXiv:** [2210.03629](https://arxiv.org/abs/2210.03629)
- **Why it matters:** Combined chain-of-thought reasoning with action-taking (tool use, search), enabling LLMs to interact with external environments. A foundational paper for the "agentic AI" paradigm.

---

## Key Surveys

- **A Survey of Large Language Models** — Zhao et al. (2023) — [arXiv:2303.18223](https://arxiv.org/abs/2303.18223)
- **Large Language Models: A Survey** — Minaee et al. (2024) — [arXiv:2402.06196](https://arxiv.org/abs/2402.06196)
- **History, Development, and Principles of Large Language Models** — Wang et al. (2024) — [arXiv:2402.06853](https://arxiv.org/abs/2402.06853)
