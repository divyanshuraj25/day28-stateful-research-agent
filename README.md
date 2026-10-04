# Day 28 — Stateful Multi-Step Agent Workflow

## 🎯 Focus Area

**Stateful Multi-Step Agent Workflows**

Real-world AI tasks often require multiple sequential steps rather than a single LLM call. This project implements a stateful research workflow where each step updates a shared state and saves a checkpoint, allowing the workflow to resume from the last completed step after a failure.

---

## 🧠 Project Overview

This project builds a **4-step AI research workflow** using Python and Google's Gemini API.

The workflow takes a research topic and processes it through:

1. **Search Sources** — Finds relevant web information using Gemini with Google Search grounding.
2. **Extract Key Points** — Extracts important facts and findings from the retrieved sources.
3. **Synthesize Findings** — Combines the extracted information into a coherent research synthesis.
4. **Format Report** — Generates a structured final research report.

A `WorkflowState` dataclass carries the workflow data between all four steps.

---

## 🔄 Workflow

```text
Research Topic
      ↓
┌──────────────────────┐
│ 1. Search Sources    │
└──────────┬───────────┘
           ↓
      Checkpoint
           ↓
┌──────────────────────┐
│ 2. Extract Key Points│
└──────────┬───────────┘
           ↓
      Checkpoint
           ↓
┌──────────────────────┐
│ 3. Synthesize        │
│    Findings          │
└──────────┬───────────┘
           ↓
      Checkpoint
           ↓
┌──────────────────────┐
│ 4. Format Report     │
└──────────┬───────────┘
           ↓
      Final Report
