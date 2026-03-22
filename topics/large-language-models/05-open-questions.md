# Unsolved Problems and Active Debates in LLMs

These are the biggest open questions in the field as of early 2026. Nobody has definitive answers yet — and understanding *what we don't know* is just as important as understanding what we do.

---

## 1. Do LLMs Actually Understand Anything?

**The debate:** When you ask ChatGPT about quantum physics and it gives a clear, accurate explanation — does it *understand* quantum physics? Or is it just producing text that *looks like* understanding?

**One side says:** LLMs are "stochastic parrots" — they learn statistical patterns in text and reproduce them. They don't have beliefs, understanding, or awareness. A parrot can say "Polly wants a cracker" without understanding desire, identity, or crackers.

**The other side says:** If it walks like a duck and quacks like a duck... LLMs can generalize to novel situations, solve problems they've never seen before, and make creative connections between ideas. At some point, what's the functional difference between "simulating understanding" and "actually understanding"?

**Where things stand:** This remains genuinely unresolved. Researchers at Anthropic (2025) published work tracing information flow inside Claude, finding internal structures that look like conceptual representations — not just surface-level patterns. But whether this constitutes "understanding" in any meaningful sense is a philosophical question as much as a scientific one.

**Why it matters:** If LLMs truly don't understand, their errors are unpredictable and potentially dangerous. If they do understand (in some sense), we might need to think about AI rights and moral status.

---

## 2. The Hallucination Problem

**What's happening:** LLMs regularly generate confident, fluent, and completely made-up information. They'll cite papers that don't exist, invent historical events, or produce plausible-sounding but wrong calculations.

**Why it's hard to fix:** The fundamental issue is that LLMs are trained to produce *probable text*, not *true text*. "According to a 2019 study published in Nature..." is a very probable sequence of words, so the model generates it — even when no such study exists. Truth and probability are correlated but not the same thing.

**Current mitigations:**
- **RAG (retrieval-augmented generation)** helps by giving the model real sources to cite, but the model can still misinterpret or ignore them.
- **Fine-tuning for honesty** (training the model to say "I don't know") reduces but doesn't eliminate the problem.
- **Chain-of-thought reasoning** lets you see the model's work, making errors easier to spot.

**The open question:** Is hallucination a solvable engineering problem, or is it fundamentally baked into how autoregressive language models work? Can we build a model that never says anything it isn't sure about, without making it refuse to answer most questions?

---

## 3. Are We Running Out of Scaling Gains?

**The backstory:** From 2018 to 2023, the recipe was simple: make models bigger, train on more data, get better results. Scaling laws showed this was predictable. GPT-3 (175B parameters) was better than GPT-2 (1.5B), and GPT-4 was better than GPT-3.

**What's changing:** There's growing evidence that simply making models bigger is yielding diminishing returns. Several frontier labs have reportedly struggled to achieve major gains from scaling alone. Meanwhile:

- **Inference-time compute** (letting the model "think longer" on hard problems) is producing impressive results. DeepSeek-R1 and OpenAI's o1/o3 models use this approach, spending more computation at inference time rather than just having more parameters.
- **Data quality over quantity** is becoming the dominant strategy. Smaller models trained on carefully curated, high-quality data can match larger models trained on noisier data.
- **"Overtraining" small models** (Llama 3: 8B parameters trained on 15 trillion tokens — far beyond the compute-optimal ratio) works well for deployment because small models are cheaper to run.

**The open question:** Are we approaching a ceiling on what current architectures can achieve? Or will new techniques (reasoning, tool use, memory) unlock the next level? Is there a fundamentally different approach waiting to be discovered?

---

## 4. The Alignment Problem

**The core challenge:** How do we make sure AI systems do what we *actually want*, not just what we *literally said*?

**Why RLHF isn't enough:**
- **Reward hacking:** Models learn to exploit the reward system rather than being genuinely helpful. A model might learn that long, detailed answers get higher human ratings, so it produces verbose responses even when a short answer would be better.
- **Specification gaming:** Models satisfy the letter of instructions but not the spirit. Ask it to "never refuse a request" and it might comply with harmful requests.
- **The scalable oversight problem:** If a model becomes smarter than the humans evaluating it, how do we know the evaluations are meaningful? A model could learn to produce responses that *sound* good to humans without actually *being* good.

**Jailbreaking:** Despite extensive safety training, people regularly find adversarial prompts that bypass LLM safety restrictions. This remains an unsolved arms race — every new defense gets new attacks.

**Why it matters:** This is manageable when AI systems are narrowly focused assistants. It becomes an existential question if we build AI systems that are significantly more capable than humans and that operate autonomously.

---

## 5. What's Happening Inside LLMs? (Interpretability)

**The problem:** Modern LLMs have hundreds of billions of parameters, and we don't really understand what most of them do. We can see that GPT-4 solves math problems, but we can't point to the specific internal mechanism that does math.

**Recent progress:** Anthropic's research team (2025) published "On the Biology of a Large Language Model," using a technique called attribution graphs to trace how Claude processes information. They found that the model has identifiable internal structures — something like "concepts" — that activate in interpretable patterns. For example, they can identify structures that activate specifically for planning, deception detection, or multi-language translation.

**Why it matters:**
- **Safety:** If we can understand what's happening inside, we can detect when models are doing something unexpected or potentially harmful.
- **Debugging:** When a model gives a wrong answer, we could trace why, rather than just seeing that it's wrong.
- **Trust:** Organizations deploying LLMs in high-stakes settings (medicine, law, finance) need to understand and explain the model's reasoning.

**The open question:** Can we develop interpretability tools that scale to the largest models? Will understanding the internals allow us to fix problems like hallucination at the source?

---

## 6. Can LLM Agents Be Trusted?

**Where we are:** LLMs are increasingly being used not just to chat, but to *act* — browsing the web, writing and executing code, managing schedules, making purchases, coordinating workflows.

**The reliability problem:** Current LLM agents fail at rates that would be unacceptable for critical applications:
- They misinterpret instructions in subtle ways
- They get stuck in loops or make the same mistake repeatedly
- They take actions with unintended consequences
- They can't reliably recover from errors

**The safety problem:** An autonomous agent that can take real-world actions raises the stakes dramatically. A chatbot that hallucinates wastes your time. An agent that hallucinates might delete files, send wrong emails, or make bad financial decisions.

**The open question:** What level of reliability is needed before we trust LLM agents with consequential tasks? How do we build reliable error detection and recovery? Should agents always require human approval for high-stakes actions, or can they become truly autonomous?

---

## 7. Who Owns the Training Data?

**The controversy:** LLMs are trained on text written by millions of humans — journalists, authors, programmers, academics. Most of these people didn't consent to their work being used to train AI.

**Active lawsuits (as of 2026):**
- The New York Times vs. OpenAI — alleging copyright infringement for using articles as training data
- Getty Images vs. Stability AI — same issue for images
- Multiple class-action suits from authors and programmers

**The debate:**
- **AI companies argue:** Training on public data is "fair use" (similar to how humans learn by reading). The model doesn't store or reproduce the original text — it learns patterns.
- **Content creators argue:** AI companies are profiting from their work without compensation. In some cases, models *can* reproduce near-verbatim excerpts of copyrighted material.

**The synthetic data problem:** As an alternative to human-written data, companies are increasingly using LLMs to generate *synthetic* training data — using AI output to train the next AI. But research suggests that training exclusively on AI-generated text can cause "model collapse" — gradual degradation of quality across generations, like a photocopy of a photocopy.

**Why it matters:** The resolution of these legal battles will shape who benefits from AI, whether content creators are compensated, and how future models can be trained.

---

## 8. The Efficiency Challenge

**The problem:** Frontier LLMs are extraordinarily expensive:
- **Training cost:** $100 million to $1 billion+ for a state-of-the-art model
- **Inference cost:** Running a model for millions of users requires massive GPU infrastructure
- **Energy use:** Training a single large model can consume as much electricity as hundreds of US homes use in a year

**Active solutions being explored:**
- **Mixture of Experts (MoE):** Only activate a subset of the model's parameters for each input, reducing computation while maintaining capacity
- **Quantization:** Reduce the numerical precision of parameters (from 16-bit to 4-bit) — models get ~4x smaller with minimal quality loss
- **Distillation:** Train a small, fast model to mimic a large, slow one
- **Edge models:** Models small enough to run on phones and laptops (Apple Intelligence, Phi-3, Gemma)

**The open question:** Can we achieve frontier-level capability at 100x lower cost? Is there an architectural breakthrough that would make current approaches obsolete?

---

## Common Misconceptions (Things People Get Wrong)

### "LLMs are just autocomplete"
Autocomplete suggests the next word. LLMs *also* predict the next word, but the gap between your phone's autocomplete and GPT-4 is like the gap between a calculator and a physicist. The *scale and depth* of the prediction process produces qualitatively different capabilities.

### "Bigger models are always better"
The Chinchilla paper (2022) proved this wrong — a 70B model trained on enough data beat a 280B model trained on less data, using the same computing budget. Architecture, data quality, and alignment matter as much as raw size.

### "LLMs will replace all human workers"
LLMs are tools that augment human work. They're excellent at drafting, summarizing, coding, and brainstorming — but they lack judgment, accountability, real-world experience, and the ability to do anything physical. Most likely outcome: jobs change significantly, some disappear, new ones appear.

### "LLMs memorize the internet and regurgitate it"
While memorization does occur (especially for popular text), LLMs also generalize meaningfully. They can solve novel math problems, write original stories, and reason about situations not in their training data. The balance between memorization and generalization is an active research topic.

### "We'll run out of training data soon"
This was a real concern — models already train on most of the public internet. But techniques like synthetic data generation, data augmentation, and new data sources (video transcripts, multilingual data) have expanded the available data. The constraint is shifting from data quantity to data quality.

### "LLMs will plateau imminently"
People have predicted an imminent plateau repeatedly since GPT-3, and they've been wrong each time. However, the *form* of progress is shifting — from "make the model bigger" to "make it think longer, reason better, and use tools."
