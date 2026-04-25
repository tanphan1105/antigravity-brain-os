<div align="center">
  <h1>🧠 Antigravity Brain OS</h1>
  <p><strong>The System Prompt Architecture to enforce Zero-Defect, Zero-Hallucination behavior on LLM Agents.</strong></p>
  
  <p>
    <img src="https://img.shields.io/badge/Agent_Architecture-V3.1-blueviolet?style=for-the-badge" alt="Version">
    <img src="https://img.shields.io/badge/Toyota-Jidoka-red?style=for-the-badge" alt="Jidoka">
    <img src="https://img.shields.io/badge/First_Principles-Engineered-black?style=for-the-badge" alt="Engineered">
  </p>
</div>

---

## 😫 The Pain Point
Are you tired of AI coding agents (like Cursor, Claude, or ChatGPT) destroying your codebase?
* Do they arbitrarily rewrite your 1000-line HTML files just to change a CSS class?
* Do they hallucinate parameters and inject technical jargon that ruins your B2B SEO?
* Do they fail to understand CMS restrictions (like WordPress `wpautop`) and output code that breaks in production?

## 💊 The Solution: Antigravity OS
This repository contains the **System Prompts and Audit Checklists** derived from a highly disciplined, enterprise-grade AI workflow. By injecting these rules into your AI, you upgrade it from a "junior coder" into a **Senior Systems Architect**.

### ✨ Core Philosophies
1. **Karpathy Coding Discipline:** Strict guardrails preventing full-file overwrites. Enforces **Surgical Edits** using AST parsing and localized regex.
2. **Toyota Jidoka:** "Automation with a human touch." The Agent is programmed to **Stop the Line** if a discrepancy is found, rather than guessing and causing cascading failures.
3. **Inversion Thinking:** The prompts force the AI to define how a piece of code could catastrophically fail *before* it writes the solution.

## 🚀 Quick Start
1. Navigate to the `system-prompts/` directory.
2. Copy the contents of `global_agent_rules.yaml`.
3. Paste it directly into your Cursor Rules (`.cursorrules`), your custom ChatGPT Instructions, or your LangChain System Prompt.
4. Watch your AI immediately start executing surgical, highly-disciplined edits.

## 🗂 Repository Structure
* `/system-prompts/`: YAML and MD files containing the core OS logic.
* `/audit-checklists/`: Protocols like `jidoka_protocol.md` and `zero-space-deploy.md` to verify AI output quality.

> "To tame the machine, you must first engineer the mind."
