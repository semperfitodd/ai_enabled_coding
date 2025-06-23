# Module 2: Prompt Engineering Techniques

**Focus**  
How to craft clear, structured prompts to get the best results from AI coding assistants. This module covers advanced prompt engineering techniques like providing specific context, example-driven instructions, and “meta-prompting” that dramatically improve the accuracy and relevance of AI-generated code. Senior engineers will learn to shape AI outputs by refining how they ask questions – including using personas and iterative prompting – to achieve more consistent, context-aware solutions.

---

## Structured Prompting Strategies
Clear, well-structured prompts drastically improve an AI assistant’s output quality. Always be specific about what you want the code to do and include any necessary context. For example, instead of asking *“Can you help with this code?”*, specify the task and requirements: *“In Python, write a function that parses a log file for error entries and returns a summary of error counts.”* Include details like programming language, libraries or frameworks, and any constraints (performance, format, etc.). It often helps to break complex requests into bullet points or numbered requirements **within** your prompt – this structure ensures the AI addresses each aspect of your request methodically. Additionally, providing an example of input and expected output (a one-shot example) in the prompt can anchor the assistant’s response to a clear target. The more guidance you give (desired output format, edge cases to consider, etc.), the less the AI has to guess, and the more accurate your result will be. Keep in mind that for tools like GitHub Copilot (which generates code based on your current file context), structured prompting means writing descriptive function names, comments, and TODOs – these serve as implicit prompts that guide Copilot to produce the intended code.

---

## Meta-Prompting and Prompt Iteration
**Meta-prompting** involves instructing the AI *how* to approach the task or adopting a specific persona in your prompt. By setting a role or context for the assistant, you prime it to produce more relevant and targeted output. For example, beginning a prompt with *“You are a senior backend engineer well-versed in security best practices…”* can lead to responses that emphasize secure coding and robustness. This technique lets you impose a perspective or standard: you can ask the AI to follow a certain coding style, adhere to company guidelines, or step through its reasoning. Don’t hesitate to explicitly tell the model the format of answer you need (e.g. “provide the code only, with comments explaining each step”). A well-crafted meta-prompt can significantly adjust the tone and depth of the answer you get.

**Prompt iteration** is the process of refining prompts based on the AI’s output, treating the interaction as an iterative dialogue. Rather than expecting a perfect solution in one go, senior engineers should review the AI’s first answer and then identify how to improve it. If the solution isn’t accurate or misses a requirement, you can follow up with a clarified prompt or additional instructions. For instance, if an AI-generated function works but isn’t optimal, you might prompt: *“Great, now optimize this function’s performance and add error handling for null inputs.”* The AI will then incorporate those refinements. This iterative prompting (sometimes called chain-of-thought prompting when guiding the AI step-by-step) leverages the conversation history to converge on a better solution. Remember that models like ChatGPT and Claude maintain context in a session, so you can build on each result with further tweaks. Always be willing to re-prompt with more detail or break a problem into sub-prompts if the initial attempt isn’t on target – iteration is key to honing the AI’s output.

---

## BSC Expectations: Prompts Reflect Your Thinking  
At BSC, we expect engineers to write prompts that reflect **intentionality, clarity, and expertise**. The quality of your AI output mirrors the quality of your thinking — lazy prompts create lazy results. We don’t prompt like consumers; we prompt like engineers.

That means:

- Prompts should show your understanding of the **system constraints, standards, and goals**  
- Meta-prompts must align with **how we write, think, and build** — not just generic best practices  
- Iteration isn’t optional — it’s a **core part of the workflow**, not a fallback when the first try fails  

If your prompt lacks detail, structure, or awareness of how it fits into the broader system, it’s not BSC-quality. You’re expected to train the AI like you’d mentor a junior dev: with **precision, structure, and follow-through**.

---

## Example Application
*Using ChatGPT and Copilot for Secure API Integration*  
In this example, an engineer is developing a utility function to retrieve customer data from a web API, with strict requirements for error handling and security. Initially, they ask ChatGPT a generic question and receive a simplistic answer. Recognizing improvement is needed, the engineer applies prompt engineering techniques: they re-prompt ChatGPT with a structured request that specifies the API details (endpoints, parameters) and the need for robust error handling. They also include a persona instruction, telling ChatGPT to act as a security-conscious senior developer, which leads to output that avoids insecure practices (like hard-coding API keys or ignoring exceptions). For each refinement, the code suggestions become more aligned with the enterprise’s standards. After a few prompt iterations, ChatGPT produces a well-structured Python function with proper error checking, logging, and comments. The engineer then uses GitHub Copilot in the IDE to integrate the suggested code into the codebase, leveraging Copilot’s quick in-line completions for minor improvements (such as adding type hints and formatting). This scenario demonstrates how thoughtful prompting and iterative refinement guide the AI to generate code that is reliable and compliant with organizational guidelines, instead of a one-shot naive solution.

## Step-by-Step Prompts with Good and Bad Examples
To illustrate the evolution of a prompt, consider the API integration task above. The following sequence shows how the engineer’s prompts improved through iteration:

#### ❌ Bad Prompt
```bash
Write a Python function to fetch user data from an API.
```
*Issue:* This prompt is underspecified. It doesn’t mention which API or what “fetch user data” entails, and it provides no context about error handling or output format. The AI might return a generic function with placeholder logic, insufficient for real needs.

#### ✅ Better Prompt
```bash
Write a Python function using the requests library to fetch user details from ExampleCo’s REST API given a user ID.
It should send a GET request to the /users/{id} endpoint and return the response data as a JSON object.
Include basic error handling for network issues or non-200 HTTP responses.
```
*Improvement:* Here the task is defined more clearly – the API endpoint is specified, along with the library to use and expected output format. The assistant’s response to this prompt is more relevant, producing workable code. However, the result may still lack some enterprise-level details (no logging, no security considerations like timeouts or avoiding sensitive data exposure).

#### ✅ Better Prompt
```bash
You are a senior Python developer focused on reliability and security.
Write a Python function using the requests library to fetch user details from ExampleCo’s /users/{id} API endpoint.
The function should take a user_id and return the JSON response.
Include robust error handling (network timeouts, non-200 statuses) and use secure coding practices (for example, don’t hard-code the API key—assume it’s passed in securely).
```
*Improvement:* This version adds a meta-prompt persona and emphasizes security and robustness. By instructing the AI to act as a seasoned, security-conscious developer, the generated code now avoids bad practices (e.g., no hard-coded credentials, proper exception handling). The function is more robust, though it might still be missing documentation or strict type hints that the team requires.

#### ✅ Better Prompt
```bash
You are a senior Python developer focused on reliability and security.
Write a Python function get_user_data(user_id, api_key) that uses the requests library to GET https://api.example.com/users/{user_id} and returns the result as a JSON object.
For example, if user_id="12345", it should GET .../users/12345. Handle timeouts and HTTP errors by raising exceptions with clear messages.
Include a brief docstring explaining the function and use type hints for the parameters and return value.
```
*Improvement:* Now an example usage is provided (`user_id="12345"`) to concretely illustrate the expected behavior and URL format. Additional formatting instructions (docstring and type hints) are given to ensure the output aligns with the team’s coding standards. The prompt is very specific about function signature and error handling. The AI’s answer to this prompt is a well-documented, type-annotated function that meets all the stated requirements.

#### ✅ Better Prompt
```bash
You are a senior Python developer focused on reliability and security.
Write a Python function get_user_data(user_id: str, api_key: str) -> dict that retrieves a user’s data from ExampleCo’s REST API.
It should send a GET request to https://api.example.com/users/{user_id} with proper authorization (use the api_key in a header), and return the response body as a JSON dictionary.
Include a docstring explaining the function’s purpose and parameters.
Handle network timeouts, JSON parsing errors, or non-200 HTTP responses by raising a custom ApiError exception with an informative message.
Ensure no sensitive data (like the API key) is logged or exposed.  
```
*Result:* This final prompt combines all improvements – precise details about the function’s purpose and interface, an example of the endpoint and usage of the API key, required error handling, and a security-conscious stance. The AI now returns a comprehensive solution that includes everything: proper request setup with headers, careful error handling and exceptions, a clear docstring, and no insecure practices. The code is ready to be reviewed and integrated, having been shaped significantly by the engineer’s prompt refinements.

---

## Summary
- **Clarity is king:** The more specific and structured your prompt, the better the AI’s output. Always include relevant details – context, constraints, and desired output format – instead of making the model infer them.  
- **Guide with examples:** When possible, provide sample inputs and outputs or use cases in your prompt. A concrete example focuses the AI and reduces ambiguity in its response.  
- **Use personas and instructions:** Don’t hesitate to tell the assistant *how* to think or what role to assume (e.g. *“You are an expert in X”*). Setting a persona or giving process guidance can align the response with certain standards or depth of explanation.  
- **Iterate to elevate:** Treat prompt crafting as an iterative process. If the first answer isn’t what you need, refine your prompt and try again. Incrementally add details or new instructions (like “now optimize this part” or “explain why you chose this approach”) to steer the AI toward the ideal solution.  
- **Adapt to the tool:** Leverage the strengths of each AI coding assistant. For interactive models like ChatGPT or Claude, you can have a back-and-forth conversation, adding context or corrections in each prompt. For in-IDE tools like Copilot, ensure your code comments and function names clearly describe the next chunk of code you want – this context guides the AI just as a written prompt would.

---

## ✅ Do / ❌ Don’t

| ✅ **Do**                                 | ❌ **Don’t**                   |
| ------------------------------------------------------------ | ---------------------------------------------------- |
| Be specific and detailed in your prompts. Provide context, requirements, and even sample input/output so the AI knows exactly what you expect. | Don’t ask overly broad or vague questions. *“Generate some code for this”* without specifics will lead to generic or often irrelevant output. |
| Use meta-prompting and give the AI a role or persona (e.g. “You are a senior C# developer familiar with our coding standards…”). Tailor the tone and depth of the answer by clarifying how it should respond. | Don’t leave the AI on autopilot with default behavior if it’s giving poor results. If the output isn’t right, avoid simply retrying the same prompt – instead, adjust the prompt’s wording, add a guiding persona, or split the task into smaller prompts. |
| Break complex tasks into multiple prompts or steps. Tackle one aspect at a time and use prompt chaining (feed the output of one step into the next) to maintain clarity and control. | Don’t cram multiple unrelated requests into one prompt. Asking for too much at once (e.g. “Create a function and write unit tests and update the documentation”) can confuse the model and yield disjointed results. |
| Emphasize important constraints or standards in the prompt. If performance, security, or style matters, mention those explicitly (e.g. “ensure the solution uses O(n) time” or “follow OWASP security guidelines”). | Don’t assume the AI knows your internal standards or the context if you haven’t stated them. Failing to mention critical constraints or company-specific rules can lead to outputs that violate expectations (e.g. using disallowed functions or licenses). |
