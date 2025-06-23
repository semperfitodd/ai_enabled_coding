# Module 7: Testing & Debugging with AI

## Focus  
This module shows how to use AI tools like ChatGPT, Claude, and Copilot to assist in testing and debugging software. You’ll learn how to prompt AI to generate effective unit and edge-case tests, help identify bugs, and explain stack traces — all while maintaining responsibility for final validation and coverage quality.

---

## AI-Generated Tests  
AI tools can significantly speed up test creation by:

- Generating **unit tests** for existing functions  
- Providing **edge-case scenarios** that developers may overlook  
- Supporting **test-driven development (TDD)** by suggesting tests before code is written

However, AI does not guarantee test relevance, coverage, or correctness. All generated tests should be reviewed and adapted.

---

## Debugging Assistance  
AI can be prompted to:

- Explain confusing error messages or stack traces  
- Suggest fixes for known issues  
- Refactor problematic code sections  
- Recommend logging or assertions to narrow down issues

When stuck, AI can act as a rubber duck — but with suggestions.

---

## BSC Expectations: You Still Own the Bugs  
At BSC, test quality is not optional — and AI doesn’t get a free pass. That means:

- AI-generated tests must be **validated, expanded, and documented**  
- Test coverage must reflect **real application risk**, not just “green” checkboxes  
- AI can help you **understand bugs**, but you are expected to **fully trace and resolve them**  
- Every test added must have **clear intent, coverage rationale, and maintainable structure**

Debugging is not outsourcing. If you don’t understand the issue, don’t accept the fix. If the test doesn’t explain *why it exists*, don’t ship it. Use AI to get smarter and faster — not to offload the hard parts.

---

### I-Assisted Debugging with Human Oversight

AI tools can accelerate the debugging process—but **never replace engineering judgment**. When fixing bugs or resolving test failures, engineers must stay in full control of the review, validation, and verification process.

#### Iterative Debugging in Practice

A developer encountered a failing unit test related to an edge case in a financial calculation. They prompted an AI assistant for help, which returned a potential fix involving a boundary check.  
Rather than accepting the suggestion outright, the developer:

1. Reviewed the generated diff to ensure business logic was preserved.
2. Cross-checked the logic against the original test case and edge condition.
3. Ran the full test suite to confirm all scenarios passed, including performance benchmarks.
4. Documented the change and tagged it as AI-assisted in the PR description.

This process exemplifies **augmented debugging**—AI may point the way, but the engineer steers the wheel.

#### Testing Tool Integrations

To scale this responsibly, we encourage integration with modern testing frameworks that support AI-enhanced development:

- **IDE plugins** (e.g. GitHub Copilot, Amazon Q Developer): for writing or suggesting tests inline.
- **CI/CD AI hooks**: suggesting missing edge cases based on coverage gaps.
- **Static analysis tools**: flagging AI-generated code for deeper inspection.
- **Model-specific test suites**: ensuring repeatable validation of LLM-generated code against business rules.

#### 💡 Forward-Thinking Practice

By blending AI tooling into an auditable, human-driven testing process, we:
- **Accelerate quality assurance**, without bypassing controls.
- **Maintain trust and traceability**, even with LLMs in the loop.
- **Reinforce engineering ownership** of test-driven development.

In high-compliance environments, our stance is simple:
> **AI can assist, but engineers remain accountable for every test, every assertion, and every bug fix.**

---

## Example Application: Testing a Price Calculation Function

### Objective  
Use ChatGPT to generate and validate tests for a `calculate_discounted_price()` function.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **Test Generation**

#### ✅ Good Prompt
```
Write `unittest` test cases for the `calculate_discounted_price(price, discount)` function.
Cover normal use (100, 0.2), edge cases (0, 1), invalid input (negative price), and discount over 1.0.
```

#### ❌ Bad Prompt
```
Test this function.
```

---

### Step 2 – **Test Explanation**

#### ✅ Good Prompt
```
For each test, include a short comment explaining what it validates (e.g., "test full discount returns 0").
```

#### ❌ Bad Prompt
```
Just make tests — I’ll figure them out later.
```

---

### Step 3 – **Debugging a Failing Case**

#### ✅ Good Prompt
```
Here's the function and a failing test. Why is `calculate_discounted_price(100, 1.2)` not raising an error?
```

#### ❌ Bad Prompt
```
It broke. Fix it.
```

---

### Step 4 – **Refactoring With AI**

#### ✅ Good Prompt
```
Refactor `calculate_discounted_price()` to raise a ValueError if discount is not between 0.0 and 1.0.
Include type hints and a docstring.
```

#### ❌ Bad Prompt
```
Make this work better.
```

---

## Summary  
AI is great at speeding up test writing and debugging — but not at validating code quality or intent. You must:

- Guide the AI with complete context  
- Review all tests for correctness and maintainability  
- Own the resolution of all bugs and test failures  

AI helps you reason, but **you stay accountable**.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                                          | ❌ **Don’t**                                                                                         |
|----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Use AI to generate unit, edge-case, and regression tests based on detailed prompt inputs.          | Don’t blindly accept test code that passes — validate test logic and what is (or isn’t) being tested. |
| Ask AI to explain errors, suggest assertions, or refactor failing logic — then verify manually.    | Don’t trust AI to fully understand business logic — always test assumptions and boundary conditions.  |
| Refine test coverage by prompting AI to generate missing scenarios.                                | Don’t settle for “just enough” coverage to pass CI — cover critical paths, edge cases, and failure modes. |
| Use AI to help fix bugs faster, but fully trace and test the resolution yourself.                   | Don’t ship an AI-suggested fix you don’t fully understand or that introduces new blind spots.         |
