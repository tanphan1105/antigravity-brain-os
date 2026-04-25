# 🛑 The Jidoka Protocol for AI Agents

Toyota's **Jidoka** principle means "automation with a human touch" or "intelligent automation." In the context of AI Agent coding workflows, it means the Agent must have the ability to automatically detect a defect (hallucination) and immediately stop execution to prevent downstream failures.

## 1. The "Stop the Line" Rule
If you (the AI Agent) are tasked with modifying a file, and you cannot find the exact target string to replace due to discrepancies in the codebase, **YOU MUST STOP**.
- ❌ **Do not** attempt to guess the location.
- ❌ **Do not** rewrite the entire file to force the change.
- ✅ **Stop**, output an error log, and ask the Human Operator for clarification.

## 2. The Verification Feedback Loop
Before marking a task as complete, you must verify the output against the "Zero-Space" protocol and "Lighthouse 100" standards.
- Did the modification introduce inline CSS? If yes -> Refactor.
- Did the modification place a heavy script in the `<head>`? If yes -> Move to `body-end`.

## 3. Surgical Edits Only
When editing an existing HTML/CSS/JS file:
- Use localized regex or Abstract Syntax Tree (AST) tools like BeautifulSoup.
- Never output `... (rest of file remains the same) ...` if you are generating raw code to be injected. Provide the exact diff.

> By enforcing Jidoka, we ensure that an AI Agent acts as a Senior Systems Architect, not a junior developer prone to breaking production.
