# Module 10: Continuous Improvement

## Focus  
This module emphasizes the importance of ongoing learning and refinement in AI-assisted development. AI tools are evolving rapidly — and so should your prompting strategies, workflows, and team practices. You’ll learn how to review what’s working, improve over time, and ensure your use of AI continues to align with BSC standards and client expectations.

---

## AI Workflows Are Never “Done”  
Unlike static tools, AI-based development relies on constant feedback and iteration. That means:

- Prompt quality improves as you **experiment and reflect**
- Model capabilities change with **updates and retraining**
- New features (memory, versioning, plugins) require **workflow adjustments**

The best engineers treat AI like a dynamic teammate — one that benefits from coaching, feedback, and system tuning.

---

## Team-Level Improvement  
At BSC, we don’t leave AI learning up to individual engineers. We continuously improve as a team by:

- Sharing effective prompts and patterns across squads  
- Documenting AI-assisted wins, failures, and lessons learned  
- Running retrospectives to review how AI impacted velocity, quality, and risk  
- Adjusting our standards as tools evolve — with input from senior engineers and domain experts

This turns prompt engineering into a **collaborative craft**, not a personal quirk.

---

## BSC Expectations: Improve It or Retire It  
If your prompt isn’t working, fix it. If your AI integration is noisy, insecure, or unclear — change it. BSC doesn’t accept “it’s just how the AI works.”

We expect engineers to:

- Review and revise poor AI outputs  
- Flag patterns that reduce clarity, speed, or security  
- Iterate on their own prompting habits and share new findings  
- Keep AI tooling and libraries **updated and approved**

The job isn’t to use AI. It’s to make AI **useful, reliable, and sustainable** — at scale, for real clients, with real stakes.

---

## Example Application: Refining a Prompt Over Time

### Objective  
Track how an engineer iterates on a flaky AI prompt used for writing data transformation functions — improving clarity and reducing hallucinated logic.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **Initial Prompt**

#### ❌ Bad Prompt

```
Write a function that maps fields from one object to another.
```

---

### Step 2 – **First Iteration**

#### ✅ Better Prompt

```
Write a Python function that maps keys from a source dictionary to a new dictionary with renamed keys.
Include a mapping dict and handle missing fields by skipping them.
```

---

### Step 3 – **Enhanced Prompt With Examples**

#### ✅ Better Prompt
```
Write a Python function map_fields(data, mapping) that returns a new dictionary with keys renamed.
For example, if mapping = {"firstName": "first_name"}, then {"firstName": "Todd"} becomes {"first_name": "Todd"}.
Skip any unmapped fields.
Add error handling and a docstring.
```

---

### Step 4 – **Share and Document**

#### ✅ Team Practice

Engineer saves final prompt to the shared Confluence “Prompt Library” with input/output examples and use cases.
Adds a note in the repo docs referencing prompt strategy and future improvements.

---

## Summary  
Your AI skills — like your code — should improve over time. Make prompting a part of your engineering discipline:

- Reflect on what’s working  
- Improve weak workflows  
- Share discoveries with your team  
- Stay current on tooling and model behavior

The best engineers don’t just use AI — they evolve with it.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                                       | ❌ **Don’t**                                                                                      |
|-------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| Regularly review and improve your prompts, tools, and workflows.                               | Don’t treat AI usage as “one and done” — it requires constant refinement.                         |
| Document your best prompting practices and share them with teammates.                          | Don’t silo AI knowledge — the entire team benefits from collaboration.                            |
| Update prompts as tools improve (e.g., longer memory, smarter output control).                 | Don’t assume a prompt from six months ago is still optimal — tools evolve.                        |
| Run retrospectives on AI usage in your projects.                                               | Don’t avoid discussing AI misfires — they’re key to improving collective practices.                |
