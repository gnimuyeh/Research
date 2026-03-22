# Key Concepts in Large Language Models

Concepts are organized in **learning order** — each section builds on the previous ones.

---

## Level 1: Foundations (Prerequisites)

### 1.1 Linear Algebra Basics
- Vectors, matrices, matrix multiplication, dot products
- These are the fundamental operations inside every neural network
- **Resource:** 3Blue1Brown's "Essence of Linear Algebra" (YouTube, free)

### 1.2 Probability and Statistics
- Probability distributions, conditional probability, Bayes' theorem
- Maximum likelihood estimation, cross-entropy loss
- Language modeling is fundamentally about predicting probability distributions over words
- **Resource:** Chapter 3 of *Deep Learning* by Goodfellow, Bengio, and Courville (free online)

### 1.3 Neural Network Fundamentals
- Neurons, layers, activation functions, forward/backward propagation
- Gradient descent, stochastic gradient descent (SGD), Adam optimizer
- Overfitting, regularization, batch normalization
- **Resource:** Andrew Ng's Deep Learning Specialization (Coursera)

### 1.4 Word Embeddings
- Words as dense vectors in continuous space (vs. one-hot encoding)
- Word2Vec (CBOW, Skip-gram) — Mikolov et al. (2013)
- Semantic relationships captured geometrically: "king - man + woman ≈ queen"
- GloVe embeddings (Pennington et al., 2014)
- **Key insight:** The idea that meaning can be represented as a point in high-dimensional space

---

## Level 2: Core Architecture

### 2.1 Sequence-to-Sequence Models
- Encoder-decoder architecture for mapping input sequences to output sequences
- Originally built with RNNs/LSTMs (Sutskever et al., 2014)
- The bottleneck: compressing entire input into a single fixed-length vector

### 2.2 The Attention Mechanism
- Allows the model to focus on different parts of the input when generating each output token
- Bahdanau attention (2014): additive attention for machine translation
- Solves the fixed-length bottleneck by providing direct access to all input positions
- **Key insight:** Not all input tokens are equally relevant for generating each output token

### 2.3 The Transformer Architecture
- **The core innovation behind all modern LLMs**
- Replaces recurrence entirely with **self-attention** — processes all positions in parallel
- Key components:
  - **Scaled dot-product attention:** Q (query), K (key), V (value) matrices → Attention(Q,K,V) = softmax(QK^T/√d)V
  - **Multi-head attention:** Multiple attention heads capture different relationships
  - **Positional encoding:** Sine/cosine functions inject position information (since there's no recurrence)
  - **Feed-forward layers:** Two-layer MLP applied to each position independently
  - **Layer normalization and residual connections:** Stabilize training
- Three architectural variants:
  - **Encoder-only** (BERT): bidirectional, used for classification and embeddings
  - **Decoder-only** (GPT): autoregressive, used for generation — dominates modern LLMs
  - **Encoder-decoder** (T5, original Transformer): used for translation and seq2seq tasks
- **Paper:** "Attention Is All You Need" (Vaswani et al., 2017)

### 2.4 Tokenization
- Subword tokenization: Byte-Pair Encoding (BPE), WordPiece, SentencePiece
- Converts raw text into integer token IDs that the model processes
- Trade-off between vocabulary size and sequence length
- Modern LLMs typically use 32K–128K token vocabularies

---

## Level 3: Pre-training

### 3.1 Language Modeling Objectives
- **Causal language modeling (CLM):** Predict the next token given all previous tokens — used by GPT, Llama, Claude
- **Masked language modeling (MLM):** Predict randomly masked tokens using bidirectional context — used by BERT
- CLM enables generation; MLM enables understanding. Modern LLMs use CLM.

### 3.2 Pre-training Data
- Trained on trillions of tokens from the internet: web pages, books, code, Wikipedia, academic papers
- Data quality, deduplication, and filtering are critical
- Common datasets: Common Crawl, The Pile, RedPajama, FineWeb
- Data preprocessing: deduplication, quality filtering, toxicity removal, PII scrubbing

### 3.3 Scaling Laws
- **Kaplan et al. (2020):** Performance follows power-law relationships with model size, data, and compute
- **Chinchilla / Hoffmann et al. (2022):** Model size and data should be scaled equally (~20 tokens per parameter)
- In practice, modern models "overtrain" smaller models beyond Chinchilla-optimal to reduce inference costs
- **Key insight:** Bigger is generally better, but how you allocate compute between parameters and data matters enormously

### 3.4 Training Infrastructure
- Distributed training across thousands of GPUs/TPUs
- Data parallelism, tensor parallelism, pipeline parallelism
- Mixed-precision training (FP16/BF16), gradient checkpointing
- Training runs cost millions of dollars and take weeks/months

---

## Level 4: Post-training & Alignment

### 4.1 Supervised Fine-Tuning (SFT)
- Fine-tune the pre-trained model on curated instruction-response pairs
- Teaches the model to follow instructions and produce helpful responses
- Requires high-quality human-written demonstrations

### 4.2 Reinforcement Learning from Human Feedback (RLHF)
- Three-step pipeline introduced by InstructGPT (Ouyang et al., 2022):
  1. **SFT:** Fine-tune on demonstrations
  2. **Reward model training:** Train a model to predict human preferences from ranked outputs
  3. **PPO optimization:** Use the reward model to further fine-tune the LLM via reinforcement learning
- A 1.3B InstructGPT beats a 175B GPT-3 in human evaluations
- **Key insight:** Alignment is more cost-effective than scale alone

### 4.3 Direct Preference Optimization (DPO)
- Simplifies RLHF by directly optimizing the policy without a separate reward model
- Rafailov et al. (2023) — more stable and simpler to implement than PPO
- Increasingly popular as an alternative to RLHF

### 4.4 Constitutional AI (CAI)
- Bai et al. (2022, Anthropic) — LLM self-critiques and revises its own outputs based on a set of principles
- Reduces reliance on human labelers for alignment
- Used in training Claude models

---

## Level 5: Inference & Prompting

### 5.1 Prompting Techniques
- **Zero-shot:** Ask the model directly with no examples
- **Few-shot:** Provide a few input-output examples in the prompt (Brown et al., 2020)
- **Chain-of-thought (CoT):** Ask the model to show its reasoning steps (Wei et al., 2022)
- **Self-consistency:** Sample multiple CoT paths and take the majority answer
- **ReAct:** Interleave reasoning and actions (Yao et al., 2023)

### 5.2 In-Context Learning
- LLMs can learn new tasks from examples in the prompt, without any gradient updates
- An emergent capability that appears at scale
- Still not fully understood theoretically — active research area

### 5.3 Decoding Strategies
- **Greedy decoding:** Always pick the highest-probability token
- **Beam search:** Maintain top-k candidates
- **Sampling:** Random sampling with temperature, top-k, top-p (nucleus sampling)
- Temperature controls randomness: low = deterministic, high = creative

### 5.4 Context Window and Long Context
- Transformers have a fixed context length (originally 512 tokens, now up to 1M+)
- Techniques for extending context: RoPE, ALiBi, ring attention, sliding window
- Longer context enables processing entire documents, codebases, and multi-turn conversations

---

## Level 6: Advanced Topics

### 6.1 Retrieval-Augmented Generation (RAG)
- Combine LLMs with external knowledge retrieval (Lewis et al., 2020)
- Retrieve relevant documents → inject into prompt → generate grounded response
- Reduces hallucination and provides up-to-date information
- Now standard in production LLM applications

### 6.2 Mixture of Experts (MoE)
- Not all parameters activate for every input — only a subset of "expert" sub-networks are used
- Allows massive model capacity with lower inference cost
- Examples: Mixtral (Mistral), Switch Transformer (Google), DeepSeek-V3

### 6.3 Parameter-Efficient Fine-Tuning (PEFT)
- LoRA (Low-Rank Adaptation): Train small adapter matrices instead of full model weights
- QLoRA: Combine LoRA with 4-bit quantization
- Enables fine-tuning billion-parameter models on consumer hardware

### 6.4 Quantization and Efficiency
- Reduce model precision from FP32/FP16 to INT8/INT4 for faster, cheaper inference
- GPTQ, AWQ, GGUF formats for efficient deployment
- Knowledge distillation: Train a smaller model to mimic a larger one

### 6.5 Multimodal LLMs
- Extend LLMs to process images (GPT-4V, Claude 3), audio, and video
- Vision encoders (ViT) connected to language decoders
- Native multimodal models integrate vision and language earlier in the architecture

### 6.6 Agentic AI
- LLMs as autonomous agents that plan, reason, and take actions
- Tool use: calling APIs, searching the web, executing code
- Multi-agent systems: specialized agents collaborating on complex tasks
- Memory and planning capabilities
