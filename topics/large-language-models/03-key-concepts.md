# Key Concepts Explained — From the Ground Up

Each concept is explained fully with analogies and examples. Read them in order — each section builds on the previous ones.

---

## 1. Tokens: How LLMs Read Text

You and I read words. LLMs read **tokens**.

A token is a chunk of text — sometimes a whole word, sometimes part of a word, sometimes just a punctuation mark. Before an LLM processes any text, it breaks it into tokens.

**Example:**
```
"ChatGPT is amazing!" → ["Chat", "G", "PT", " is", " amazing", "!"]
```

Why not just use whole words? Because there are too many possible words (including names, slang, typos, other languages). Instead, LLMs use a fixed vocabulary of common chunks — typically 32,000 to 128,000 tokens. Rare words get split into smaller pieces the model does recognize.

**A useful rule of thumb:** 1 token ≈ ¾ of a word in English. So 1,000 words ≈ 1,333 tokens.

This matters for a practical reason: every LLM has a **context window** — the maximum number of tokens it can process at once. Early models could handle ~2,000 tokens (about 1,500 words). Modern models handle up to 1 million tokens (about 750,000 words — that's several novels at once).

---

## 2. Embeddings: Meaning as Numbers

Computers don't understand words — they understand numbers. So how do we turn words into numbers in a meaningful way?

**The naive approach:** Assign each word a random ID. "Cat" = 1, "Dog" = 2, "Democracy" = 3. But this is useless — the numbers tell the computer nothing about meaning. "Cat" and "Dog" are much more similar than "Cat" and "Democracy," but the numbers don't reflect this.

**The embedding approach:** Represent each word as a *list* of numbers (called a "vector"), where the numbers capture aspects of meaning. For example (simplified to 3 numbers):

```
"Cat"   → [0.9, 0.1, 0.8]   (animate, not-royal, small)
"Dog"   → [0.9, 0.1, 0.7]   (animate, not-royal, small)  ← close to Cat!
"King"  → [0.8, 0.9, 0.5]   (animate, royal, medium)
"Table" → [0.0, 0.0, 0.5]   (not animate, not-royal, medium) ← far from Cat
```

In reality, LLM embeddings have 768 to 12,288 numbers per word, capturing subtle dimensions of meaning that humans can't easily name. But the principle holds: **similar meanings = similar numbers**.

The famous example from Word2Vec (2013):
> **King - Man + Woman ≈ Queen**

This works because "Man" and "Woman" differ mainly on a "gender direction" in the number space. Subtract the male direction from King, add the female direction, and you land near Queen. The model learned this entirely from reading text — no one told it about gender.

---

## 3. The Transformer: The Engine Inside Every LLM

The Transformer (2017) is the architectural design inside every modern LLM. Here's how it works, using an analogy.

### Analogy: The Study Group

Imagine a study group of students sitting in a circle. Each student represents a word in a sentence. The study session works like this:

1. **Every student looks around the room** and decides which other students have information relevant to them.
2. **They ask those students questions** and gather relevant information.
3. **Each student updates their own understanding** based on what they gathered.
4. **This process repeats** multiple rounds. Each round, students develop deeper understanding.

This is essentially what a Transformer does. Let's make it concrete.

### How Attention Works

Consider the sentence: *"The bank by the river was steep."*

When the Transformer processes the word "bank":
- It needs to figure out what "bank" means here (river bank? financial bank?)
- It looks at every other word and computes a **relevance score** (attention weight)
- "river" gets a high score — it's the most useful for understanding "bank"
- "the" and "was" get low scores — not very helpful

The Transformer then creates a new representation of "bank" that incorporates information from "river" and "steep." Now "bank" is understood in context as a river bank, not a financial institution.

### Multi-Head Attention: Seeing Multiple Things at Once

The Transformer doesn't just compute attention once — it computes it multiple times in parallel using different "heads." Think of each head as looking for a different type of relationship:

- **Head 1** might focus on grammatical relationships (subject → verb)
- **Head 2** might focus on meaning relationships (bank → river)
- **Head 3** might focus on nearby context (what word came just before)

A typical LLM has 32 to 128 attention heads running simultaneously. Together, they capture a rich picture of how every word relates to every other word.

### Why This Beat Everything Before

Before the Transformer, models processed text one word at a time (using LSTMs). This was:
- **Slow:** You had to wait for word 1 to be processed before starting word 2
- **Forgetful:** By the time you reached word 500, information from word 1 was faded

The Transformer processes all words **simultaneously** and every word can attend to every other word **directly**, regardless of distance. Word 1 and word 500 are equally accessible. This made models both faster to train and better at understanding long-range relationships.

### Layers: Depth of Understanding

A Transformer stacks many identical layers on top of each other (typically 32 to 80 layers in modern LLMs). Each layer refines the understanding further:

- **Early layers** tend to capture basic things: word types, simple grammar
- **Middle layers** capture meaning, relationships, and context
- **Late layers** capture high-level abstractions: tone, intent, complex reasoning

By the time text has passed through all the layers, each token's representation has been enriched with deep contextual understanding.

---

## 4. How LLMs Generate Text

LLMs generate text **one token at a time**, left to right. Here's the process:

1. You give the model a prompt: *"The capital of France is"*
2. The model processes the entire prompt through its Transformer layers
3. At the end, it produces a probability distribution over its entire vocabulary — a score for every possible next token:
   - "Paris" → 92%
   - "Lyon" → 1.5%
   - "the" → 0.8%
   - "banana" → 0.0001%
   - ... (scores for all 50,000+ tokens)
4. It picks one token (usually the highest-probability one) → **"Paris"**
5. Now the input becomes *"The capital of France is Paris"*
6. Repeat from step 2 to generate the next token
7. Continue until the model produces a stop signal or reaches a length limit

### Temperature: Controlling Creativity

When picking the next token, you can adjust the **temperature**:

- **Low temperature (0.0–0.3):** The model almost always picks the highest-probability token. Output is predictable, consistent, and "safe." Good for factual questions.
- **High temperature (0.7–1.0):** The model is more willing to pick lower-probability tokens. Output is more creative, varied, and surprising. Good for creative writing, brainstorming.
- **Temperature = 0:** The model *always* picks the highest-probability token. Same input → always same output.

Think of temperature as a "creativity dial."

---

## 5. Pre-training: Learning from the Internet

Pre-training is the first and most expensive phase of building an LLM.

### What Happens
The model reads an enormous amount of text and learns to predict the next word, billions of times. Every time it predicts wrong, it adjusts its internal parameters slightly to do better next time. Over weeks of training on thousands of GPUs, it develops an understanding of language, facts, reasoning patterns, and more.

### The Training Data
Modern LLMs are trained on datasets containing trillions of words:
- Web pages (from crawls of the internet)
- Books
- Wikipedia
- Code repositories (GitHub)
- Academic papers
- Social media and forums

The data is heavily filtered and cleaned — removing duplicates, low-quality content, personally identifiable information, and (to varying degrees) toxic content.

### The Scale
- **GPT-3** was trained on ~300 billion tokens
- **Llama 3** (2024) was trained on ~15 trillion tokens — 50x more
- Training a frontier LLM costs **$50–500 million** in compute
- It runs on thousands of GPUs simultaneously for weeks or months

### What the Model Learns
Through next-word prediction, the model implicitly learns:
- Grammar and syntax
- Facts and world knowledge
- Reasoning patterns
- Common sense
- Multiple languages
- Code structure
- Mathematical patterns

Nobody teaches it these things explicitly. It learns them because they're useful for predicting what comes next in text.

---

## 6. Fine-Tuning: Teaching Specific Skills

After pre-training, the model is knowledgeable but not particularly useful as an assistant. It might continue your question with another question, or generate rambling text instead of a concise answer.

**Fine-tuning** gives it specific skills. There are two main approaches:

### Supervised Fine-Tuning (SFT)
Show the model thousands of examples of ideal behavior:

```
Prompt: "What's the capital of Japan?"
Ideal response: "The capital of Japan is Tokyo."

Prompt: "Explain photosynthesis simply."
Ideal response: "Photosynthesis is how plants convert sunlight,
water, and carbon dioxide into food (glucose) and oxygen..."
```

The model adjusts its parameters to produce responses more like these examples. Human writers create these examples, and quality matters enormously — a model is only as good as its training examples.

### RLHF (Reinforcement Learning from Human Feedback)

SFT gets you most of the way, but the model still sometimes produces unhelpful, offensive, or incorrect responses. RLHF is a technique for further refining the model by learning from human preferences.

**How it works, step by step:**

1. Give the model a prompt and have it generate several different responses
2. Have a human ranker sort the responses from best to worst
3. Use these rankings to train a separate "reward model" — a model that learns to predict what humans prefer
4. Use the reward model to further train the LLM: generate a response → the reward model scores it → adjust the LLM to get higher scores

**Analogy:** Imagine teaching a dog to do tricks. SFT is like showing the dog exactly what to do (demonstration). RLHF is like the dog trying different things, and you saying "good boy!" or "no, try again" — it learns from your feedback over many rounds.

The result is an LLM that's much more helpful, polite, safe, and aligned with what users actually want.

---

## 7. Retrieval-Augmented Generation (RAG): Giving LLMs a Reference Library

### The Problem
LLMs know a lot, but their knowledge has a cutoff date (they don't know about events after their training) and they sometimes hallucinate (make things up confidently). They also can't access your private documents, company data, or the latest news.

### The Solution: Let Them Look Things Up
RAG works like this:

1. You ask a question
2. A search system finds the most relevant documents from a database (company docs, knowledge base, web, etc.)
3. Those documents are inserted into the LLM's prompt as context
4. The LLM generates an answer *based on the retrieved documents*

**Analogy:** Imagine an open-book exam vs. a closed-book exam. Without RAG, the LLM is taking a closed-book exam — it can only use what it memorized during training. With RAG, it's an open-book exam — it can look up the relevant information before answering.

### Why It Matters
- **Reduces hallucination:** The model can cite real sources instead of making things up
- **Stays up to date:** The document database can be updated, even though the model itself isn't retrained
- **Works with private data:** You can feed it your company's internal documents
- **Cheaper than retraining:** Updating a database is much cheaper than retraining a multi-billion dollar model

RAG is how most real-world LLM applications work today — from customer support bots to enterprise search to coding assistants.

---

## 8. Prompting Techniques: Getting Better Answers

The way you ask an LLM a question dramatically affects the quality of the answer. Here are the main approaches:

### Zero-Shot Prompting
Just ask the question directly:
> "What causes rainbows?"

The model answers based purely on its training. Works well for straightforward questions.

### Few-Shot Prompting
Provide a few examples of the pattern you want before asking your actual question:

> **Example 1:** "Translate 'hello' to Spanish" → "hola"
> **Example 2:** "Translate 'goodbye' to Spanish" → "adiós"
> **Now translate 'thank you' to Spanish** → "gracias"

By showing examples, you teach the model the exact format and behavior you expect. This was the key finding of the GPT-3 paper (2020).

### Chain-of-Thought (CoT) Prompting
Ask the model to think step by step:

> "Roger has 5 tennis balls. He buys 2 cans of 3 tennis balls each. How many tennis balls does he have now? **Let's think step by step.**"

Without CoT, the model might jump to a wrong answer. With CoT, it reasons:
> "Roger starts with 5 balls. He buys 2 cans × 3 balls = 6 balls. 5 + 6 = 11 balls."

This simple trick (discovered in 2022) improved math accuracy by up to 18% on large models. It works because it forces the model to show intermediate reasoning rather than jumping to conclusions.

### System Prompts
Instructions that set the model's overall behavior:

> "You are a helpful medical assistant. Answer health questions clearly, but always remind the user to consult a doctor for medical advice."

System prompts shape the model's persona, expertise, and boundaries for an entire conversation.

---

## 9. Hallucination: When LLMs Make Things Up

**What it is:** An LLM generates text that sounds confident and plausible but is factually wrong. Examples:
- Citing a research paper that doesn't exist
- Confidently stating false historical dates
- Fabricating statistics or quotes

**Why it happens:** LLMs are trained to produce *probable-sounding* text, not *true* text. If the training data contains patterns like "According to a 2019 study in Nature..." the model learns to generate text that *looks like* a citation, even when no such study exists. It's generating the *form* of knowledge without necessarily having the *substance*.

**Analogy:** Imagine someone who's read thousands of encyclopedia articles. They've learned what encyclopedia entries *sound like* — the tone, structure, and phrasing — so they can generate new entries that sound authoritative. But they might confuse details, merge facts from different articles, or fill in gaps with plausible-sounding inventions.

**How to mitigate it:**
- **RAG:** Give the model access to real sources (see above)
- **Ask for citations:** Then verify them
- **Use lower temperature:** More deterministic output = fewer creative fabrications
- **Cross-check important facts:** Don't trust an LLM as a sole source of truth

Hallucination remains one of the biggest unsolved problems in LLM research.

---

## 10. Agentic AI: LLMs That Take Action

The most recent frontier: LLMs that don't just talk, but *do things*.

### What is an AI Agent?
A traditional LLM interaction is like texting an expert — you ask questions, they answer. An **AI agent** is more like hiring an assistant who can actually do tasks:

- Browse the web and find information
- Write and run computer code
- Read and edit files
- Send emails or messages
- Coordinate with other AI agents
- Make multi-step plans and execute them

### How It Works
The LLM is given access to **tools** — functions it can call. When it decides it needs to search the web, it outputs a special command like `search("latest iPhone specs")`, the system executes that search, feeds the results back, and the LLM continues its work.

**The ReAct framework** (2023) formalized this as a loop:
1. **Think:** "I need to find the current stock price of Apple"
2. **Act:** Call the search tool with "Apple stock price today"
3. **Observe:** Receive the search results
4. **Think:** "The price is $198.50. Now I need to calculate..."
5. Repeat until the task is complete

### Why It Matters
Agentic AI is the bridge between "AI that knows things" and "AI that does things." By 2028, analysts predict a third of enterprise applications will include autonomous AI agents. This is the active frontier of LLM development as of 2026.

---

## Concept Map: How Everything Connects

```
TOKENS (how LLMs read)
    ↓
EMBEDDINGS (meaning as numbers)
    ↓
TRANSFORMER (the engine)
    ├── Attention (understanding relationships)
    ├── Multi-head attention (multiple perspectives)
    └── Layers (depth of understanding)
         ↓
PRE-TRAINING (learn from internet)
         ↓
FINE-TUNING (learn to be helpful)
    ├── SFT (learn from demonstrations)
    └── RLHF (learn from human preferences)
         ↓
    USABLE LLM (ChatGPT, Claude, etc.)
         ↓
    ┌────┼────────┐
    ↓    ↓        ↓
  RAG  Prompting  Agents
(look  (ask it   (let it
things  better)   do things)
up)
```
