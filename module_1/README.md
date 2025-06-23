# Module 1: Modularizing Tasks for AI Coding

## Focus
Techniques for breaking down complex software tasks into smaller, modular prompts to get better results from AI coding assistants. This module covers prompt engineering strategies that improve controllability, accuracy, and debugging when using AI for coding. Senior engineers will learn to design multi-step workflows where AI handles well-defined subtasks rather than attempting to solve an entire problem at once.

---

## Task Decomposition Strategies
Best practices for splitting a large coding project or feature into discrete prompts or steps. Complex, multi-step requests can confuse AI models; instead, tasks should be segmented into manageable chunks. For example, rather than asking an AI to “build a full financial report generation module,” first prompt it to outline the module’s components, then implement each component sequentially. This approach aligns with the “first commandment” of effective prompting: break problems into smaller parts.

---

## Prompt Chaining and Iteration
How to use chain-of-thought prompting or iterative queries, where the output of one AI prompt becomes the input for the next. We will demonstrate chaining with a real scenario – e.g., using ChatGPT to plan a feature, then refining each part step-by-step. This enhances the AI’s performance on each subtask, ensuring that nothing is overlooked along the way.

---

## Example Application: Modular AI Workflow for a Risk Scoring Feature

### Objective
Use ChatGPT to modularly develop a `riskScore(user)` function that:
- Fetches user profile data
- Computes a risk score based on age, credit history, and account activity
- Returns a structured JSON response

---

## BSC Expectations: Decomposition is Design, Not Delegation  
At BSC, modularizing a problem for AI is a **design skill**, not a shortcut. Engineers are expected to demonstrate:

- An understanding of **how each prompt fits** into the larger system  
- A clear mental model of **dependencies, inputs, and expected outputs**  
- Strategic decomposition that anticipates **future extension and refactoring**

AI should not be handed vague, unstructured tasks. If you’re not thinking through how the pieces connect, you’re not engineering — you’re just delegating. The value isn’t in asking AI to build something *quick* — it’s in using your experience to *guide* AI precisely, building maintainable, auditable, and aligned code from the start.

---

### Step-by-Step Prompts with Good and Bad Examples

---

### Step 1 – **Plan the Workflow**

#### ✅ Good Prompt
```
Break down a function that calculates a financial risk score into logical components.
The function should take a user ID and return a score.
List each component and what it does.
```

Claude's output from prompt
```python
def calculate_financial_risk_score(user_id: str) -> float:
    """
    Calculates a comprehensive financial risk score for a user.
    
    Args:
        user_id: Unique identifier for the user
    
    Returns:
        Financial risk score (0-100, higher = riskier)
    """
    # Component 1: Data Retrieval
    user_data = fetch_user_financial_data(user_id)  # Gets credit/transaction history
    
    # Component 2: Credit History Analysis
    credit_score = calculate_credit_subscore(
        user_data['payment_history'],
        user_data['credit_utilization']
    )
    
    # Component 3: Transaction Behavior Analysis
    transaction_risk = analyze_transaction_patterns(
        user_data['transaction_frequency'],
        user_data['large_transactions']
    )
    
    # Component 4: Account Stability Assessment
    stability_score = assess_account_stability(
        user_data['account_age'],
        user_data['balance_volatility']
    )
    
    # Component 5: External Risk Factors
    market_risk = get_market_risk_indicator()  # External economic data
    
    # Component 6: Weighted Aggregation
    return (
        0.4 * credit_score +
        0.3 * transaction_risk +
        0.2 * stability_score +
        0.1 * market_risk
    )
```

#### ❌ Bad Prompt
```
Write a risk scoring function.
```

Claude's output from prompt
```python
def calculate_risk_score(likelihood: float, impacts: list, method: str = 'highest') -> float:
    """
    Calculates risk score using likelihood and impact assessments.
    
    Args:
        likelihood: Probability of risk occurring (0-1 scale or 1-5 ordinal scale).
        impacts: List of impact scores for different categories (e.g., [financial, operational]).
        method: Aggregation method for impacts: 'highest', 'average', or 'average_individual'.
    
    Returns:
        Computed risk score (higher = more severe).
    
    Raises:
        ValueError: For invalid methods or empty impacts.
    """
    if not impacts:
        raise ValueError("At least one impact score required")
    
    # Impact aggregation methods
    if method == 'highest':
        overall_impact = max(impacts)
    elif method == 'average':
        overall_impact = sum(impacts) / len(impacts)
    elif method == 'average_individual':
        individual_scores = [likelihood * impact for impact in impacts]
        overall_impact = sum(individual_scores) / len(individual_scores)
    else:
        raise ValueError("Invalid method. Use 'highest', 'average', or 'average_individual'")
    
    return likelihood * overall_impact
```

#### Why is the output better from the `Good Prompt`?

1. Domain-Specific Design
2. Tightly integrates with actual financial metrics: credit history, transactions, stability, external market conditions.
3. Modular and Extensible
4. Each component (e.g. calculate_credit_subscore, analyze_transaction_patterns) is decoupled, enabling:
5. Unit testing
6. Swappable logic for each subscore
7. Auditability and compliance review
8. Realistic Aggregation
9. Uses weighted scoring, which is how most real-world financial risk engines operate.
10. Easy to adjust weights or incorporate additional factors (e.g., fraud risk, employment history).
11. Traceable and Explainable
12. Each part can be traced for explainability — crucial in regulated environments.
13. Supports compliance requirements like model governance and bias audits.

---

### Step 2 – **Fetch User Data (mock)**

#### ✅ Good Prompt
```
Write a Python function called `fetch_user_data(user_id)` that returns a mock dictionary with this structure:
{
  "name": "Jane Doe",
  "age": 35,
  "credit_score": 700,
  "missed_payments": 2,
  "login_frequency": 15,
  "transaction_volume": 5000
}
Use static data for now.
```

#### ❌ Bad Prompt
```
Make a function to get user info.
```

---

### Step 3 – **Analyze Credit History**

#### ✅ Good Prompt
```
Given the fields `credit_score` and `missed_payments`, write a function `analyze_credit_history(data)` that returns a float between 0.0 (low risk) and 1.0 (high risk).
Use a simple scoring formula.
```

#### ❌ Bad Prompt
```
Analyze credit risk.
```

---

### Step 4 – **Analyze Account Activity**

#### ✅ Good Prompt
```
Write a function `analyze_account_activity(data)` that uses `login_frequency` and `transaction_volume` to return a float between 0.0 (low risk) and 1.0 (high risk).
More logins and higher volume == less risk.
```

#### ❌ Bad Prompt
```
Tell me if the user is risky based on usage.
```

---

### Step 5 – **Compute Final Score**

#### ✅ Good Prompt
```
Create a function `compute_risk_score(credit_risk, behavior_risk)` that returns a weighted average risk score.
Use 60% weight for credit and 40% for behavior.
```

#### ❌ Bad Prompt
```
Combine the risks into a score.
```

---

### Step 6 – **Final Assembly**

#### ✅ Good Prompt
```
Write a function `riskScore(user_id)` that calls all the helper functions and returns this JSON structure:

{
  "user": "Jane Doe",
  "riskScore": 0.64,
  "details": {
    "creditRisk": 0.55,
    "behaviorRisk": 0.72
  }
}
Assume the helper functions already exist and return floats.
```

#### ❌ Bad Prompt
```
Write the whole thing that calculates the risk.
```

---

## Summary

This module demonstrates the value of **prompt chaining** and **task decomposition** in AI-assisted coding. Rather than asking for a complete solution in one go, we decompose the work, iterate on each step, and **preserve control** while speeding up development. You stay the architect — AI handles the grunt work.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                                                  | ❌ **Don’t**                                                                 |
|--------------------------------------------------------------------|------------------------------------------------------------------------|
| Break complex work into small, modular subtasks and provide those pieces to the AI one at a time. | Don’t feed the AI a huge, monolithic problem. Overly broad requests confuse the model and produce unpredictable code. |
| Iteratively refine the AI’s output by building on previous results. | Don’t skip intermediate steps. If the AI’s first answer is off, refine the prompt and try again instead of giving up. |
| Clearly isolate parts of the code (e.g. separate frontend vs. backend). This helps the AI focus and not break unrelated code. | Don’t allow changes to “sneak” into unrelated modules. Protect stable code boundaries so AI edits stay in the intended scope. |
