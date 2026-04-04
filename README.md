# Chapter 29: From Wishlist to Working System — Whiteboard Agent Capabilities and Iterative Architecture

**INFO 7375: Prompt Engineering for Generative AI — Take-Home Midterm**

## Core Claim

Agent architecture is discovered iteratively, not designed upfront. The whiteboard exercise — list capabilities, group by data source, derive agents — consistently produces better designs than top-down specification, because real agents reveal their natural boundaries only after the first working version exists.

## Repository Contents

| File | Description |
|---|---|
| `chapter29_prose.md` | Full chapter text — scenario, mechanism, design decision, failure case, exercise |
| `chapter29_demo.ipynb` | Runnable Jupyter Notebook demo with AI scaffold, Human Decision Node, and triggerable failure case |
| `authors_note.md` | 3-page Author's Note: design choices, tool usage, self-assessment |
| `README.md` | This file |

## How to Run the Demo

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/chapter29-whiteboard-agents.git
cd chapter29-whiteboard-agents

# Run the notebook (no GPU needed, no external dependencies)
jupyter notebook chapter29_demo.ipynb
```

Run each cell top-to-bottom with `Shift + Enter`. The notebook uses only Python standard library — no pip installs required.

## What the Demo Shows

1. **Head-to-Head Comparison**: Top-down (by role, coupling=0.58) vs. Whiteboard (by data affinity, coupling=0.37)
2. **AI Scaffold + Human Decision Node**: An LLM proposes semantic clustering (retrieval/action/analysis). The human rejects it because semantic similarity ≠ data affinity.
3. **Triggerable Failure Case**: Progressive boundary degradation (Levels 0–3) shows coupling density driving latency explosion.
4. **Load Test**: 100 concurrent tasks demonstrate how boundary errors compound nonlinearly under contention.

## The Failure Mode

When agent boundaries are drawn around job roles instead of data dependencies, CRM read and write operations get split across agents. Every customer task pays a cross-agent communication tax. Under concurrent load, this tax compounds through queue contention — p95 latency increases by 2.5x at maximum fragmentation. No model upgrade fixes this. Only redrawing the agent graph does.

## Video

[YouTube link — unlisted](YOUR_VIDEO_LINK_HERE)

## Master Argument

**Architecture is the leverage point, not the model.** Same capabilities, same tasks, same model. The only variable is where we draw agent boundaries. That single architectural decision determines whether the system scales or collapses.
