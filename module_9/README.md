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
