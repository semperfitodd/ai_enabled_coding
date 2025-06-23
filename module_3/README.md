# Module 3: Leveraging AI’s Strengths

## Focus  
Understanding where AI coding tools like ChatGPT, Claude, and Copilot excel — and where they fall short. This module teaches engineers to delegate low-complexity, repetitive, or boilerplate tasks to AI while retaining control over architecture, design, and nuanced business logic. You’ll learn how to match task type to tool capability and avoid misuse of AI on high-risk or ambiguous work.

---

## Where AI Excels  
AI is great at high-speed output, low-risk generation, and repetitive code structures. Let it generate:

- Boilerplate setup (e.g., data access layers, DTOs, logging wrappers)
- Code scaffolding and test case generation
- Simple transformation or parsing logic
- Documentation drafts and commit messages

AI is also valuable for rapid iteration and ideation — for example, asking for multiple ways to solve a common programming challenge. In these cases, AI helps unblock development or accelerate routine tasks.

---

## Where AI Should Not Replace You  
Critical thinking is still your job. AI is not a solution architect, domain expert, or production owner. Avoid using AI as the lead on:

- System architecture or major design decisions
- Security-sensitive logic (e.g., auth, encryption)
- Performance-critical code without review
- Legal or regulated workflows (e.g., financial algorithms)

Instead, use AI as a **coding assistant**, not an engineer. You own the output. You vet the result.

---

## BSC Expectations: AI Is Your Intern, Not Your Lead Engineer  
At BSC, we treat AI like a **sharp junior developer** — fast, but not yet wise. That means:

- You don’t just accept what AI gives you — you **evaluate it in the context of existing systems**  
- AI-generated code must reflect **your architectural intent**, not just “what works”  
- If AI scaffolds a solution, your job is to **refactor, extend, and align it** with BSC standards and long-term maintainability  

We expect engineers to use AI for acceleration, not delegation. You own the system. You own the decision. Use AI to do more, faster — but only if you keep it pointed in the right direction.

---

## Example Application: Accelerating CRUD Service Development

### Objective  
Use ChatGPT and Copilot to scaffold a simple user service with CRUD operations, while ensuring design and validation are still handled manually by the engineer.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **Scaffold the Service**

#### ✅ Good Prompt
```
Write a Python class `UserService` that includes CRUD methods: `create_user`, `get_user`, `update_user`, and `delete_user`.
Each method should use a dictionary as a mock database.
Include docstrings and error handling.
```

#### ❌ Bad Prompt
```
Make a class that manages users.
```

---

### Step 2 – **Generate Input Validation Logic**

#### ✅ Good Prompt
```
Write a helper function `validate_user_input(data: dict)` that checks if the dictionary includes keys: `"name"` (string), `"email"` (valid email), and `"age"` (integer > 0).
Return a boolean and raise a `ValueError` if invalid.
```

#### ❌ Bad Prompt
```
Make sure user info is valid.
```

---

### Step 3 – **Generate Tests**

#### ✅ Good Prompt
```
Write unit tests using `unittest` for each method in the `UserService` class.
Cover cases for valid input, missing fields, and invalid updates.
```

#### ❌ Bad Prompt
```
Test this service.
```

---

### Step 4 – **Review & Refactor**

#### ✅ Good Prompt
```
Now optimize the `update_user` method to prevent updates if no fields change.
Add logging to each method to indicate action type (create, read, etc.).
```

#### ❌ Bad Prompt
```
Improve the code.
```

---

## Summary  
AI coding assistants shine when used for repetitive tasks, boilerplate generation, and scaffolding. These tools multiply your speed — but only when you steer the process. Let AI handle the grunt work. You handle the judgment.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                                      | ❌ **Don’t**                                                                                   |
|------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Use AI to generate boilerplate, test stubs, CRUD logic, and docs — then review it critically. | Don’t use AI to design complex systems or write business-critical logic without your review.  |
| Use AI to brainstorm multiple implementations of a simple function.                           | Don’t blindly pick the first AI output — especially if you don’t understand how it works.     |
| Keep control of architecture and integration logic. Use AI as a code-writing assistant.       | Don’t let AI introduce silent side effects into critical paths — always verify the behavior.  |
