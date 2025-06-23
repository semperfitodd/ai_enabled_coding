# Module 9: Responsible AI Use

## Focus  
This module outlines how to use AI coding tools ethically, securely, and in compliance with BSC standards and client expectations. AI is powerful, but also risky — especially in regulated environments. You’ll learn how to protect data, avoid misuse, and enforce responsible boundaries when prompting and using AI-generated output.

---

## Privacy and Data Sensitivity  
AI tools, especially public ones, are not safe places for sensitive data. At BSC, treat every AI tool as if it’s **external and untrusted by default**, unless you’re using an enterprise-approved, secured version.

**Never include:**

- Client data (PII, account numbers, credentials)
- Proprietary algorithms or configs
- Source code from restricted repos
- Anything marked confidential or internal-only

Always assume your input could be logged or leaked — even if the AI vendor says otherwise.

---

## Legal and Ethical Constraints  
Responsible AI use also means:

- **Respecting copyright and licensing** – Don’t allow AI to insert GPL-licensed or unattributed code into proprietary projects  
- **Avoiding bias and unfair outputs** – Be mindful of AI-suggested names, logic, or comments that might be inappropriate or discriminatory  
- **Being transparent** – If AI helped build a module or write logic, note that in the PR or documentation

You’re still accountable for the code — including how it was created.

---

## BSC Expectations: If You Wouldn’t Say It in Public, Don’t Prompt It  
At BSC, we hold AI usage to the same standard as production engineering. That means:

- Prompts are written **professionally**, without jokes, bias, or shortcuts  
- Output is **auditable**, reviewable, and explainable  
- Engineers are responsible for **removing all traces of client or internal identifiers**  
- We **log and disclose** material AI assistance on projects, so clients and auditors are never surprised

This isn’t about covering your tracks — it’s about building a culture of trust, transparency, and care.

---

### ⚖️ Responsible AI Use: Caution and Traceability

Our stance on AI is clear: it must be used responsibly, with guardrails, and in alignment with our ethical and regulatory standards. That includes **knowing when not to use it**, and ensuring that when we do, it's fully auditable.

#### What-If Scenario

Imagine an engineer debugging a rare edge case involving the behavior of a proprietary pricing engine used in FX trades. To get help from an AI assistant, they paste a chunk of log output—including internal error codes and obscure product identifiers—into the prompt.

Unbeknownst to them, the error code structure and identifiers are **internally classified**, representing patterns not publicly documented. In some jurisdictions, even this metadata can constitute **regulated business logic** under financial secrecy laws.

This is exactly the seemingly innocuous data that **must never be shared** with external AI systems.

Even anonymized inputs can leak business logic, platform architecture, or internal naming conventions—any of which could pose a **security, IP, or compliance risk** if exposed.

---

### Auditability: Trust Through Traceability

To meet enterprise-grade governance standards, engineers must maintain traceability of AI contributions.

#### Required Practices

- **Tag all AI-assisted PRs.**  
  Include a note in the pull request or commit message such as:  
  `"AI-assisted: ChatGPT used to generate error handling logic"`

- **Log the prompts used for major changes.**  
  For significant contributions (e.g., code generation, test design, or documentation), include the prompt as a comment block or attach it in the PR description.

- **Use project-level changelogs or wikis** to track AI tool usage patterns, lessons learned, and adjusted guardrails over time.

- **Automate where possible.**  
  Teams are encouraged to explore tooling that detects AI-generated code blocks or prompts engineers to tag contributions at commit time.

---

### Why This Matters

Responsible AI use isn’t just an engineering issue—it’s a **trust issue**. Our clients operate in highly regulated industries. They expect:

- A full audit trail of how software was developed.
- Clarity on where generative AI influenced logic or documentation.
- Confidence that **sensitive data and business logic never left our boundary of control**.

By hardening our AI development practices with traceability and caution, we not only protect our clients—we demonstrate that **we lead by example** in secure, ethical, and forward-thinking AI enablement.

---

## Example Application: Secure Use of AI in a Compliance Module

### Objective  
Use Claude to draft logic for a financial compliance rule, while maintaining strict boundaries around sensitive logic and regulatory expectations.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **General Logic Request**

#### ✅ Good Prompt
```
Write a Python function that checks if a transaction amount exceeds a dynamic threshold set by region.
Use placeholder values and document where logic will be inserted later.
```

#### ❌ Bad Prompt
```
Here’s the client’s real rule set for overdraft limits — write this logic exactly.
```

---

### Step 2 – **Avoiding Leakage**

#### ✅ Good Prompt
```
Use example account IDs and generic transaction metadata.
Do not reference real client fields, schema names, or business logic.
```

#### ❌ Bad Prompt
```
Use the actual client schema we discussed: "acct_id", "risk_class", and "sub_threshold_amt".
```

---

### Step 3 – **Licensing Check**

#### ✅ Good Prompt
```
If any code block is sourced from open libraries, assume we must verify it’s MIT or Apache licensed before using.
```

#### ❌ Bad Prompt
```
It came from AI — just use it.
```

---

### Step 4 – **Documentation and Disclosure**

#### ✅ Good Prompt
```
Note in the PR that AI was used to draft the function’s skeleton. All logic and validation added by engineer.
```

#### ❌ Bad Prompt
```
Ship it. Nobody needs to know how it was created.
```

---

## Summary  
Using AI responsibly means protecting data, respecting copyright, and being transparent. At BSC, this is non-negotiable.

- Treat prompts like public communications  
- Avoid sharing client logic, PII, or internal code  
- Validate licensing and remove bias  
- Own the result — and document how you got there

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                                             | ❌ **Don’t**                                                                                              |
|--------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| Treat prompts like external-facing messages. Write them with care, without internal or client detail. | Don’t paste sensitive data or proprietary business logic into AI tools — even temporarily.                |
| Use secured, approved enterprise AI tools when working with client-facing or internal projects.       | Don’t assume public tools are safe — if you’re unsure, ask your lead or switch to a vetted AI platform.   |
| Validate all AI-suggested code for IP risk and ethical implications.                                  | Don’t let the AI “sneak” in code from unclear origins — if it looks too perfect, investigate.             |
| Be transparent about AI assistance in documentation, code comments, and PRs.                          | Don’t hide that AI was used or assume clients don’t care — trust is built through disclosure.             |
