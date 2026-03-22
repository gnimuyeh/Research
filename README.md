# Research Learning Agent

A Claude Code agent that produces structured, factual learning materials for any topic you give it.

## How It Works

Give the agent any topic, and it follows a 3-step research framework:

1. **Trace the Path** — Uses web search to find the foundational figures, seminal papers, and key works that shaped the field. All citations are verified, never fabricated.

2. **Build Structured Knowledge** — Organizes findings into a progressive learning curriculum: core concepts in dependency order, a step-by-step learning path, and connections to related fields.

3. **Cross-Validate and Deepen** — Reviews materials for gaps, verifies accuracy across sources, identifies current frontiers and open problems, and ensures the path is followable by a beginner.

## Output

For each topic, the agent produces:

| File | Contents |
|------|----------|
| `01-overview.md` | Field overview, motivation, and big questions |
| `02-foundational-papers.md` | Seminal works with full citations and summaries |
| `03-key-concepts.md` | Core concepts in learning order |
| `04-learning-path.md` | Step-by-step curriculum with specific resources |
| `05-open-questions.md` | Current frontiers, debates, and active research |

All materials are saved to `topics/<topic-slug>/` and also printed in the conversation.

## Usage

```
Give me a topic: reinforcement learning
```

The agent will research, organize, and produce the full set of learning materials.
