# The Story of How LLMs Were Invented

You don't need to read any of the papers mentioned here. This tells the story in plain English — what was invented, by whom, why it mattered, and how each breakthrough led to the next. If you *do* want to go deeper on any topic, the paper reference is there for you.

---

## Chapter 1: Teaching Computers to Remember (1990s)

### The Problem
In the early 1990s, researchers wanted computers to process language — translate sentences, predict the next word, understand text. But language is sequential: the meaning of a word often depends on words that came *before* it, sometimes many sentences earlier.

Early neural networks had no memory. They saw each piece of input independently, like reading a book by looking at random single words.

### The Breakthrough: Recurrent Neural Networks and LSTM

Researchers built **Recurrent Neural Networks (RNNs)** — networks that could loop information back into themselves, giving them a form of memory. But RNNs had a critical flaw: they forgot things quickly. By the time they reached the end of a long sentence, they'd forgotten the beginning.

In **1997**, Sepp Hochreiter and Jürgen Schmidhuber (in Germany) invented **Long Short-Term Memory (LSTM)** networks. LSTMs added a clever "gating" mechanism — think of it like a notebook the network could write to and read from, deciding what to remember and what to forget. This solved the forgetting problem and LSTMs became the go-to tool for processing text for nearly 20 years.

---

## Chapter 2: Words as Numbers (2003–2013)

### The Problem
Computers can't read words — they only understand numbers. The simple approach was to assign each word an arbitrary ID number ("cat" = 4,521, "dog" = 7,832). But this tells the computer nothing about meaning. The numbers for "cat" and "dog" are just as far apart as "cat" and "democracy."

### The Breakthrough: Word Embeddings

In **2003**, Yoshua Bengio (Montreal, Canada) proposed a radical idea: what if we represent each word as a *list of numbers* (a "vector") where the numbers actually capture meaning? Words with similar meanings would have similar numbers.

This idea fully blossomed in **2013** when Tomas Mikolov at Google created **Word2Vec**. He trained a simple model on enormous amounts of text and discovered something magical: the resulting word vectors captured *relationships*. You could do math with meaning:

> **"king" - "man" + "woman" = "queen"**

This wasn't programmed — the model figured it out from patterns in text. The idea that meaning could be represented as a point in mathematical space was foundational. Every LLM today still represents words as vectors at its core.

---

## Chapter 3: The Attention Revolution (2014–2017)

### The Problem
By 2014, researchers were using LSTMs to build translation systems. The approach: read an entire English sentence, compress it into a single fixed-size numerical summary, then generate the French translation from that summary.

It worked, but the "compress everything into one summary" step was a bottleneck. For long sentences, crucial information got lost — like trying to summarize a whole book in a single tweet and then reconstructing it.

### The First Breakthrough: Attention (2014)

Dzmitry Bahdanau (working with Yoshua Bengio in Montreal) asked a simple question: **why compress everything? Why not let the translator look back at the original sentence while translating?**

He invented the **attention mechanism**: when generating each word of the translation, the model computes a relevance score for every word in the original sentence, then focuses on the most relevant ones.

Translating "Le chat est sur le tapis" → when generating "cat," the model pays *attention* to "chat." When generating "mat," it pays *attention* to "tapis." Different output words focus on different input words.

This was a huge improvement. But the model still processed the input one word at a time (using LSTMs), which was slow.

### The Big Breakthrough: The Transformer (2017)

In **June 2017**, eight researchers at Google published a paper with a bold title: **"Attention Is All You Need."**

Their insight: what if we throw away LSTMs entirely and build a model using *only* attention? The result was the **Transformer** — a design that:

1. **Processes all words simultaneously** (not one at a time), making it massively faster
2. **Lets every word attend to every other word**, capturing relationships regardless of distance
3. **Uses "multi-head" attention** — multiple independent attention patterns running in parallel, each capturing different types of relationships (grammar, meaning, context)

The Transformer was initially just better at translation. Nobody knew it would become the foundation of the entire AI revolution. But that's exactly what happened.

**Fun facts about the paper:**
- The title is a play on the Beatles' "All You Need Is Love"
- The name "Transformer" was chosen because one of the authors (Jakob Uszkoreit) liked how the word sounded
- All eight authors later left Google to start their own companies or join competitors

---

## Chapter 4: The Pre-training Revolution (2018)

### The Problem
Before 2018, if you wanted an AI to detect spam emails, answer medical questions, or translate French, you had to build a separate model for each task, trained on task-specific data. This was expensive, slow, and required labeled data for every new task.

### The Breakthrough: Pre-train Once, Use Everywhere

In **2018**, three landmark models arrived within months of each other:

**ELMo** (February 2018, Allen Institute): Showed that training a language model on a large text corpus produces word representations that capture context — the word "bank" gets a different representation in "river bank" vs. "bank account." Previous embeddings like Word2Vec gave each word a single fixed representation regardless of context.

**GPT-1** (June 2018, OpenAI): Alec Radford and team took a Transformer and trained it with a beautifully simple approach:
1. Give it billions of words from the internet
2. Train it to predict the next word
3. Then adapt ("fine-tune") it for specific tasks

This **pre-train → fine-tune** approach worked shockingly well. A single pre-trained model, after minor fine-tuning, could do text classification, question answering, similarity detection — all better than models built specifically for those tasks.

**BERT** (October 2018, Google): Jacob Devlin took a different approach: instead of predicting the *next* word, BERT randomly hid words in a sentence and trained the model to fill in the blanks — like a cloze test. This let it read in *both* directions (left-to-right AND right-to-left), giving it deeper understanding.

BERT dominated nearly every NLP benchmark and became the most-used AI model in production systems for years. But for *generating* text (writing, chatting), GPT's approach — predicting the next word, left to right — ultimately won out. That's why ChatGPT, Claude, and most modern LLMs use the GPT approach, not the BERT approach.

---

## Chapter 5: Scale Changes Everything (2019–2020)

### GPT-2: The Model They Were Afraid to Release (2019)

OpenAI scaled up GPT-1 to **1.5 billion parameters** (10x larger) and called it **GPT-2**. They found that it could do tasks it was *never trained on* — translation, summarization, question answering — just by being given the right prompt. No fine-tuning needed.

OpenAI was so worried about misuse (generating fake news, spam) that they initially refused to release the full model. This was the first major moment where AI safety became a public conversation.

### GPT-3: The Few-Shot Wonder (2020)

Then came **GPT-3**: **175 billion parameters**, the biggest model ever at the time, trained on 300 billion words. The paper's title said it all: **"Language Models are Few-Shot Learners."**

The discovery: if you give GPT-3 just a few examples of a task in its prompt, it can learn to do that task on the fly — without any retraining. Show it three examples of English-to-French translation, and it becomes a translator. Show it three examples of code with comments, and it becomes a programmer.

This **in-context learning** ability was an emergent behavior — it wasn't explicitly designed. Nobody fully understands why it works.

GPT-3 marked the beginning of the modern LLM era. It proved that scale itself could unlock new capabilities.

### Scaling Laws (2020)

Meanwhile, Jared Kaplan and colleagues at OpenAI discovered that LLM performance follows remarkably predictable mathematical patterns (**scaling laws**). Make the model 10x bigger → performance improves by a predictable amount. Use 10x more data → another predictable improvement.

This was like discovering a recipe: if you want a model that's X% better, you need Y more parameters and Z more data. It turned LLM development from an art into something closer to engineering — and it set off a massive compute arms race.

---

## Chapter 6: Making LLMs Actually Helpful (2022)

### The Problem
GPT-3 was impressive but often unhelpful. Ask it a question and it might:
- Continue your question with another question instead of answering it
- Generate toxic or offensive content
- Make up fake facts with complete confidence
- Ignore your instructions and go on a tangent

Raw LLMs are trained to predict text, not to be *helpful*. The internet contains plenty of rude, wrong, and harmful text, and the model learned to produce that too.

### The Breakthrough: RLHF — Learning from Human Preferences

In **2022**, OpenAI published the **InstructGPT** paper, introducing a method called **Reinforcement Learning from Human Feedback (RLHF)**:

1. **Step 1 — Fine-tune on demonstrations:** Show the model examples of humans answering questions helpfully. The model learns to imitate.

2. **Step 2 — Train a "judge" model:** Have humans rank multiple model responses from best to worst. Train a separate "reward model" that learns to predict what humans prefer.

3. **Step 3 — Optimize with the judge:** Let the LLM generate responses, have the judge score them, and gradually adjust the LLM to produce responses the judge rates highly.

The result was stunning: a **1.3 billion parameter** InstructGPT was preferred by humans over the **175 billion parameter** GPT-3 — a model 100x larger. Alignment (teaching the model *what* to say) turned out to be more powerful than scale (giving it *more capacity*).

This RLHF approach is now used to train virtually every AI assistant — ChatGPT, Claude, Gemini, and others.

### Chain-of-Thought: Teaching LLMs to Think Step by Step

Also in **2022**, Jason Wei and colleagues at Google discovered that you could dramatically improve LLM reasoning by simply asking it to **show its work**.

Instead of asking:

> "If Roger has 5 tennis balls and buys 2 cans of 3, how many does he have?"

...and getting a wrong answer, you show the model an example where the answer includes intermediate steps:

> "Roger started with 5. He bought 2 cans of 3 = 6 balls. 5 + 6 = 11. The answer is 11."

This **chain-of-thought prompting** improved accuracy on math problems by up to 18%. It only works in large models (100B+ parameters) — smaller models don't benefit. The technique spawned an entire research area on LLM reasoning.

### ChatGPT: The Moment the World Noticed (November 2022)

OpenAI combined all these advances — the Transformer, massive scale, RLHF alignment — into **ChatGPT**, a conversational AI released in November 2022. It became the fastest-growing consumer application in history, reaching 100 million users in two months.

ChatGPT wasn't a fundamental breakthrough in technology — it was the culmination of the breakthroughs above, packaged in an accessible chat interface. But it changed the world by showing billions of people what LLMs could do.

---

## Chapter 7: The Open Frontier (2023–2026)

After ChatGPT, the field exploded:

- **Meta released Llama** (2023), an open-source LLM that anyone could download, study, and modify. This democratized LLM development and led to thousands of community-built models.
- **Google launched Gemini**, a multimodal model that can understand images, audio, and video alongside text.
- **Anthropic released Claude**, trained with Constitutional AI — a method where the AI critiques its own outputs against a set of principles, reducing the need for human labelers.
- **Mistral released Mixtral** (2024), a model that doesn't use all its parameters for every input — only the relevant "expert" subnetworks activate, making it faster and cheaper.
- **DeepSeek released R1** (2025), showing that smaller open-source models could match or beat proprietary models on reasoning tasks at a fraction of the cost.
- **Agentic AI** (2025–2026): LLMs that don't just answer questions but actually take actions — browsing the web, writing and running code, managing workflows, coordinating with other AI agents.

The field is moving from "AI that talks" to "AI that acts" — and the implications are still unfolding.

---

## The Lineage at a Glance

```
Word Embeddings (2003, 2013)
       ↓
Attention Mechanism (2014)
       ↓
The Transformer (2017)      ← The architectural breakthrough
       ↓
   ┌───┴───┐
  GPT-1   BERT (2018)       ← Pre-training revolution
   ↓
  GPT-2 (2019)              ← Zero-shot abilities emerge
   ↓
  GPT-3 (2020)              ← Few-shot learning, scaling laws
   ↓
  InstructGPT/RLHF (2022)   ← Alignment breakthrough
   ↓
  ChatGPT (2022)            ← The world takes notice
   ↓
  GPT-4, Claude, Llama,     ← Open-source, multimodal,
  Gemini, DeepSeek (2023+)     reasoning, agents
```
