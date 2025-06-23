# Module 8: Collaboration & Documentation

## Focus  
This module teaches how to use AI tools to streamline collaborative development and documentation workflows. From drafting commit messages to writing technical documentation, AI can accelerate team communication — but only when used with human oversight. You’ll learn how to prompt AI to generate clear summaries, useful PR descriptions, and maintainable docs that align with BSC’s quality standards.

---

## AI in Collaborative Workflows  
AI can assist with:

- Generating **commit messages** and **pull request summaries**  
- Drafting **technical documentation** from code  
- Creating **Confluence pages** and inline comments  
- Translating developer thoughts into clear, structured text

This reduces the burden on engineers and keeps documentation fresh — but only if the content is reviewed and curated.

---

## AI-Assisted Docs Still Need Human Review  
Don’t treat AI like a documentation engine. It’s a drafting assistant. Everything it produces should be:

- **Reviewed for accuracy, tone, and completeness**  
- **Updated to reflect actual business logic or decisions**  
- **Formatted consistently** with team and client standards

A good AI draft gets you 70% there. The last 30% — clarity, trust, precision — comes from you.

---

## BSC Expectations: Docs Are Just as Important as Code  
At BSC, we don’t treat documentation as an afterthought — it’s a deliverable. That means:

- AI-generated documentation must **explain intent, constraints, and edge cases**  
- Commit messages and PRs must be **useful to reviewers** — not vague or generic  
- Confluence pages, onboarding guides, and design docs should be **clean, structured, and editable**  
- All AI-generated text should be **treated like a first draft**, not a final product

If you wouldn’t sign your name to it, don’t merge it. If a teammate wouldn’t understand it six months from now, rewrite it. Use AI to write faster — not lower the bar.

---

## Example Application: Writing a PR Summary with AI

### Objective  
Use ChatGPT to write a pull request description summarizing logic, intent, and testing details — then refine it for team use.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **Commit Message Drafting**

#### ✅ Good Prompt
```
Generate a concise Git commit message for adding a function `sanitize_input()` that strips HTML tags and escapes special characters.
```

#### ❌ Bad Prompt
```
Write a commit message.
```

---

### Step 2 – **Pull Request Summary**

#### ✅ Good Prompt
```
Draft a PR summary that explains the purpose of `sanitize_input()`, the validation logic, and links to the related Jira ticket.
Mention the edge cases covered by new tests.
```

#### ❌ Bad Prompt
```
Summarize my code.
```

---

### Step 3 – **Technical Doc Creation**

#### ✅ Good Prompt
```
Generate a draft Confluence page describing the new input sanitation module.
Include function purpose, input/output examples, and notes on XSS prevention strategy.
```

#### ❌ Bad Prompt
```
Write the docs for this thing.
```

---

### Step 4 – **Review and Edit**

#### ✅ Good Prompt
```
Review this AI-generated PR summary and update any inaccurate or unclear sections before merging.
Ensure tone and format match BSC documentation standards.
```

#### ❌ Bad Prompt
```
Looks fine. Merge it.
```

---

## Summary  
AI can reduce the burden of writing documentation — but you still own the outcome. Use it to:

- Speed up commit and PR drafting  
- Convert code into readable, useful documentation  
- Keep docs up to date without spending hours writing from scratch

But always review, revise, and clarify before publishing.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                                          | ❌ **Don’t**                                                                                      |
|----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| Use AI to help write commit messages, PR summaries, and docs — then review them like any deliverable. | Don’t treat AI-generated documentation as final — it needs editing to match voice and standards.   |
| Provide context when prompting AI to summarize logic or explain decisions.                         | Don’t use vague prompts like “write docs for this” and expect clear results.                       |
| Align AI-generated output to your audience: engineers, clients, or auditors.                       | Don’t assume one format fits all — tailor the message to the use case and stakeholder.             |
| Use AI to reduce writing overhead while increasing documentation coverage.                         | Don’t neglect docs because “AI will do it later” — documentation is part of your engineering scope. |
