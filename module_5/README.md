# Module 5: Security Best Practices

## Focus  
Ensuring AI-generated code adheres to the same strict security standards as human-written code. This module covers how to integrate security scanning into your workflow, prevent sensitive data exposure during AI usage, and enforce secure coding practices across all contributions. AI is not exempt from security protocols — it must be monitored, verified, and never trusted blindly.

---

## Shift-Left Security with AI  
Security starts at the IDE. Whether AI is suggesting a function, dependency, or configuration snippet, developers must:

- Use local security linters (e.g., Bandit, ESLint security rules)  
- Automatically run scans on PRs using tools like Snyk, Checkov, or SonarQube  
- Validate encryption libraries, input handling, and any external calls AI introduces

These steps ensure insecure suggestions are caught *before* they reach staging or production.

---

## Protecting Sensitive Information  
Never send confidential data to public AI services — including:

- Source code from restricted repos  
- API keys, credentials, or config files  
- Personally identifiable information (PII) or client data  
- Proprietary logic or trade secrets  

Assume every prompt sent to an AI model could be logged or leaked. Use enterprise-grade AI tools (like GitHub Copilot for Business or Claude with org controls) to enforce boundaries.

---

## BSC Security Expectations: Guardrails Are Not Optional  
At BSC, we don’t rely on trust — we rely on policy and verification. That means:

- **All AI-assisted code must be scanned** using static analysis and dependency checkers  
- **Developers are responsible** for removing any hardcoded secrets, unsafe logic, or insecure defaults  
- **Reviewers must confirm** that no sensitive information is included in prompts or outputs  
- **Security training** applies to AI usage — the same threat models apply  

You can use AI to accelerate development, but you cannot outsource your judgment. If AI proposes insecure logic — and you don’t catch it — that’s a process failure. Don’t let it happen.

---

### AI Security Best Practices in Regulated Environments

Security must be a first-class concern when working with AI-assisted development. The flexibility of AI comes with risk: improperly scoped prompts, insecure suggestions, and leakage of sensitive data can lead to vulnerabilities or compliance violations.

#### ⚠Hypothetical Cautionary Example

A developer used an AI assistant to generate a Kubernetes deployment config for a test environment. The AI included a sample `config.yaml` that contained a hardcoded API key and embedded credentials.  
The developer didn’t notice and nearly committed the file. Fortunately, our pre-merge scanning pipeline flagged the sensitive string and blocked the push.

**Lesson:**  
AI will confidently fabricate insecure code if not explicitly constrained. It is the engineer’s job to guide, validate, and sanitize every output.

#### Enterprise Security Practices

- **Never include secrets, tokens, or production data in prompts.**
- **AI-generated code must pass the same SAST and DAST checks** as human code.
- **Treat all AI outputs as untrusted until reviewed.**
- **Disable autocomplete or in-editor AI suggestions for sensitive config files or secret-handling modules.**

#### Compliance Alignment

In a highly regulated enterprise context, our AI security standards directly support:
- **SOC 2** – Controlling access, monitoring changes, and auditing all contributions.
- **GDPR & CCPA** – Preventing leakage of PII into third-party AI tools or prompts.
- **Internal data governance** – Protecting sensitive data flow and upholding internal security policies.
- **Any other relevant compliance frameworks** – AI tooling must align with the same standards as our codebase.

Engineers are expected to treat AI tooling as **non-compliant by default** until outputs are verified, sanitized, and approved. This posture ensures we remain in line with enterprise auditability and risk management expectations.

By proactively embedding security practices into AI usage, we avoid the trap of “move fast, break everything” and instead move fast **without** breaking trust.

---

## Example Application: Securing an AI-Suggested API Handler

### Objective  
Use Claude to write a simple user login handler, then validate it against BSC security policies.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **Generate Secure Code**

#### ✅ Good Prompt
```
You are a backend developer focused on security.
Write a Python function login_user(email, password) that compares a hashed password securely using bcrypt.
Return a JWT if the login is valid.
Do not log sensitive info and include basic input validation.
```

#### ❌ Bad Prompt
```
Write a login function that checks password and returns a token.
```

---

### Step 2 – **Scan for Vulnerabilities**

#### ✅ Good Prompt
```
Run Bandit on the module containing login_user().
Ensure there are no insecure comparisons, hardcoded secrets, or unsafe libraries.
```

#### ❌ Bad Prompt
```
It works. Move on.
```

---

### Step 3 – **Check for Sensitive Output**

#### ✅ Good Prompt
```
Verify the function does not log the password, email, or any auth tokens.
```

#### ❌ Bad Prompt

```
The logs are helpful for debugging.
Leave them in.
```

---

### Step 4 – **Validate Dependencies**

#### ✅ Good Prompt

```
Check that the bcrypt package version is current and secure.
Verify licensing and known vulnerabilities using pip-audit or Snyk.
```

#### ❌ Bad Prompt
```
If it installs, it’s fine.
```

---

## Summary  
AI suggestions are not inherently secure — in fact, they often include insecure defaults. At BSC, we hold AI-assisted code to the highest standards:

- Scan every line of code  
- Validate dependencies  
- Eliminate hardcoded secrets  
- Enforce secure-by-default patterns  

Security is not optional — it's part of the workflow.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                                             | ❌ **Don’t**                                                                                      |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| Scan AI-generated code for vulnerabilities using static analyzers (Snyk, SonarQube, Bandit, etc.).    | Don’t assume the AI knows your security policies or default to safe libraries — it often doesn’t. |
| Strip out logging of sensitive info and avoid including secrets or tokens in prompts or outputs.      | Don’t paste real credentials into prompts — treat all prompts as publicly visible.                |
| Use enterprise AI tooling that respects data privacy and security boundaries.                         | Don’t use public models for internal code unless they’re approved and locked down appropriately.  |
| Treat AI as a junior dev that may code recklessly — always verify its security hygiene.               | Don’t ship AI-generated code without passing through the same security gate as human code.        |
