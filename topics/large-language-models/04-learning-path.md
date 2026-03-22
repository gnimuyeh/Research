# Where to Go Deeper — Curated Resources

You've already learned the core concepts by reading this material. This page is a curated guide for going deeper, organized by format and commitment level. **You do NOT need to do all of these** — pick what matches your interest and learning style.

---

## If You Have 2 Hours

These are the single best resources for each format:

| Format | Resource | Why |
|--------|----------|-----|
| Video | Andrej Karpathy — *"Let's build GPT from scratch"* (YouTube, ~2hrs) | The former Tesla/OpenAI director builds a working LLM from scratch, explaining every step. Even without coding, you'll see exactly how these models work. |
| Article | Jay Alammar — *The Illustrated Transformer* (blog post) | The clearest visual explanation of the Transformer architecture on the internet. Diagrams walk you through every component. |
| Book | Andriy Burkov — *The Hundred-Page Language Models Book* | Exactly what it sounds like — a short, clear book covering LLM essentials. Great for reinforcing what you've learned here. |

---

## If You Have a Weekend

| Resource | Format | Time | What You'll Learn |
|----------|--------|------|-------------------|
| 3Blue1Brown — *Neural Networks* series | YouTube (4 videos) | 1–2 hrs | Beautiful visual explanations of how neural networks learn. The best foundation if you want to understand the "learning" part of machine learning. |
| 3Blue1Brown — *Transformers explained visually* | YouTube | 45 min | Visual walkthrough of attention and transformers, building on the neural networks series. |
| *ChatGPT Prompt Engineering for Developers* | DeepLearning.AI short course (free) | 1–2 hrs | Hands-on guide to getting better results from LLMs through prompting techniques. Practical and immediately useful. |
| HuggingFace NLP Course — Chapters 1-2 | Online course (free) | 3–4 hrs | If you want to actually *use* LLMs programmatically, this teaches you the HuggingFace library, the standard tool for working with open-source models. |

---

## If You Want a Serious Deep Dive (weeks)

### Best Books (in order of recommendation)

1. **Sebastian Raschka — *Build a Large Language Model (from Scratch)* (~$40)**
   The gold standard. Walks you through building a working Transformer, tokenizer, and training loop. Even if you don't code along, the explanations are the clearest in any book. Raschka is a professor and former ML researcher at Lightning AI.

2. **Jay Alammar & Maarten Grootendorst — *Hands-On Large Language Models* (~$50)**
   More practical than Raschka's book — focuses on using LLMs for real tasks: search, classification, summarization, RAG. Beautiful visual explanations from the author of The Illustrated Transformer.

3. **Tong Xiao & Jingbo Zhu — *Foundations of Large Language Models* (free ebook)**
   A comprehensive textbook covering pre-training, generation, prompting, alignment, and inference. More academic but thorough. Good for theoretical depth.

4. **Jurafsky & Martin — *Speech and Language Processing* (3rd ed., free online)**
   The classic NLP textbook, updated for the LLM era. Broader than just LLMs — covers the entire NLP landscape. Best as a reference rather than reading cover to cover.

### Best Courses

1. **DeepLearning.AI & AWS — *Generative AI with Large Language Models* (Coursera, free to audit)**
   The most popular structured course on LLMs. Covers the full pipeline: pre-training, fine-tuning, RLHF, deployment. About 3 weeks of effort.

2. **Stanford CS224N — NLP with Deep Learning (lectures free on YouTube)**
   A full university course. Goes deeper into the math and theory than the Coursera course. Demanding but rewarding.

3. **Stanford CS324 — Large Language Models (lecture notes online)**
   Graduate-level course specifically on LLMs — architecture, training, capabilities, limitations, societal impact. The notes are excellent reading material on their own.

4. **Cohere's LLM Course (free)**
   Beginner-friendly course from an LLM company. Covers NLP basics, LLM architecture, and practical use. Good if you want an industry perspective.

---

## If You Want to Stay Current

The LLM field moves extremely fast. Here's how to keep up:

| Resource | Format | Frequency |
|----------|--------|-----------|
| Sebastian Raschka — *Ahead of AI* newsletter | Email | Bi-weekly |
| The Batch (by Andrew Ng, DeepLearning.AI) | Email | Weekly |
| r/LocalLLaMA (Reddit) | Forum | Daily |
| Papers With Code — LLM section | Website | Updated continuously |
| HuggingFace blog | Blog | Weekly |

---

## Recommended Learning Sequences

### "I just want to understand what's going on" (5–10 hours)
1. Read the materials in this folder (you're doing this now)
2. Watch 3Blue1Brown's Neural Networks + Transformers series (2 hrs)
3. Read Jay Alammar's *The Illustrated Transformer* (1 hr)
4. Take the ChatGPT Prompt Engineering short course (1.5 hrs)

### "I want to really understand the technology" (20–40 hours)
1. Everything in the sequence above
2. Watch Karpathy's "Let's build GPT from scratch" (2 hrs)
3. Read Raschka's *Build a Large Language Model (from Scratch)*
4. Take the DeepLearning.AI Generative AI course on Coursera

### "I want to build things with LLMs" (40+ hours)
1. Everything in the sequence above
2. Complete the HuggingFace NLP Course
3. Read *Hands-On Large Language Models* (Alammar & Grootendorst)
4. Build a RAG application with a framework like LangChain or LlamaIndex
5. Fine-tune an open-source model (Llama, Mistral) using LoRA

---

## What You Do NOT Need to Do

- **Read the original research papers** — unless you're pursuing research yourself. The resources above explain everything in them more clearly.
- **Learn advanced math** — to *understand* LLMs conceptually, you don't need linear algebra or calculus. You only need math if you want to *build* them.
- **Know how to code** — to *use* LLMs effectively (prompting, RAG, etc.), you need minimal coding. To build/train models, you need Python.
- **Understand every architecture variant** — new models come out weekly. Understanding the core Transformer is enough; everything else is a variation on it.
