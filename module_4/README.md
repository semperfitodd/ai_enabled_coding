# Module 4: Code Review & Validation

## Focus  
Establishing rigorous code review and validation practices for AI-generated code. This module reinforces that AI outputs must meet the same quality, security, and readability standards as human-written code. Engineers will learn to systematically inspect, test, and secure AI contributions before integration, ensuring that nothing enters production unchecked.

---

## Human-in-the-Loop Review  
AI code is still code — it must go through the same review pipeline:

- Peer code review for logic, maintainability, and intent
- Automated testing for correctness and regressions
- Static analysis for security vulnerabilities and style compliance

AI suggestions can introduce subtle issues — like off-by-one errors, security misconfigurations, or incorrect business logic — that only human context can catch.

---

## Use Static Analysis and Linters  
Always apply automated validation tools on AI outputs. These include:

- **Linters** (e.g., ESLint, Flake8) for syntax and formatting
- **Static analyzers** (e.g., SonarQube, Snyk, Fortify) for vulnerabilities and code smells
- **Type checkers** (e.g., mypy, TypeScript) to catch inconsistencies

These tools should run locally (in your IDE) and in CI pipelines. AI-generated code is not exempt from any gatekeeping mechanism.

---

## BSC Review Culture: Go Deep or Don’t Submit  
At BSC, we don’t just look at whether the code *works* — we care about **how** it fits, **why** it’s written a certain way, and **what it will mean** for future maintainers. That means:

- Pull requests must reflect *deep contextual understanding* — both of the system and the problem being solved.  
- Submitters must demonstrate how the new code integrates with existing logic, follows best practices, and anticipates future code evolution.  
- Reviewers are expected to evaluate not only correctness, but *intent*, *clarity*, and *fit*.  

Lazy AI outputs will not be accepted. You can use AI to generate code — but not to **replace thoughtfulness**. If your PR is just a pasted AI blob, it will be rejected. If your PR shows how you used AI to accelerate routine work while applying experience, design judgment, and system-level thinking — that’s the bar we expect.

---

### 🔍 AI Code Accountability and Verification

All AI-generated code **must be treated with the same rigor, scrutiny, and standards as human-written code**. There is **zero tolerance** for skipping validation steps simply because code was written or suggested by an AI tool.

#### Mandatory Review Practices

- **Every AI-generated contribution must undergo full code review.**  
  This includes functionality, logic correctness, security posture, and test coverage.

- **AI output must never be blindly accepted.**  
  Regardless of source (ChatGPT, Copilot, Claude, etc.), engineers are accountable for understanding and verifying the behavior of every line before it is committed.

- **Engineers retain full ownership.**  
  If AI contributes to a module, the engineer reviewing the changes is responsible for its quality, correctness, and impact.

- **Same standards. No exceptions.**  
  Linting, testing, performance benchmarking, and security reviews all apply equally to AI-suggested code. There is no “AI shortcut” to production.

#### Why This Matters

AI is an accelerator, not a replacement for engineering judgment. Our clients, especially in regulated financial sectors, rely on us to ship secure, high-quality code. That means:
- No AI code bypasses our validation gates.
- Engineers are accountable for what ships.
- We apply the **same standards, every time, regardless of source**.

This uncompromising stance ensures quality, builds trust, and reflects the engineering discipline expected from a Fortune 500-grade cloud partner.

---

## Example Application: Reviewing an AI-Written Utility Function

### Objective  
Use GitHub Copilot to write a utility function, then manually validate correctness, run automated tests, and perform a static code scan.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **Generate Code**

#### ✅ Good Prompt
```
Write a Python function `convert_seconds_to_hms(seconds)` that returns a string formatted as "HH:MM:SS".
Handle edge cases (e.g. negative input, values > 24 hours).
```

#### ❌ Bad Prompt
```
Convert seconds to time.
```

---

### Step 2 – **Write Tests**

#### ✅ Good Prompt
```
Write unit tests for `convert_seconds_to_hms()` using `unittest`. Include edge cases like 0, 59, 3600, 86399, and invalid input (-5).
```

#### ❌ Bad Prompt
```
Test it.
```

---

### Step 3 – **Validate Logic and Behavior**

#### ✅ Good Prompt
```
Check if the AI function handles negative input gracefully (e.g. raises ValueError).
If not, update it to include validation.
```

#### ❌ Bad Prompt
```
Just assume it works.
```

---

### Step 4 – **Static Analysis**

#### ✅ Good Prompt
```
Run Flake8 and mypy on the module containing `convert_seconds_to_hms()` and review any warnings or errors.
```

#### ❌ Bad Prompt
```
Deploy it.
It looks fine.
```

---

## Summary  
AI-generated code must be validated like any other. Pair it with:

- Peer review for logic and business alignment
- Automated testing for correctness
- Static analysis for vulnerabilities

Engineers remain accountable — AI only accelerates part of the pipeline, not the responsibility.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                                   | ❌ **Don’t**                                                                              |
|---------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| Treat AI code like junior dev code — review it for intent, structure, and edge case logic.  | Don’t assume the AI got everything right. Look for subtle bugs or context mismatches.     |
| Run all standard tests, linters, and security tools. Automate these checks in CI pipelines. | Don’t skip validation just because the code compiles or passes one test.                  |
| Leave clear comments if adjusting AI code — explain *why* it changed to maintain intent.    | Don’t make silent changes to AI code — always preserve clarity for the next reviewer.     |
