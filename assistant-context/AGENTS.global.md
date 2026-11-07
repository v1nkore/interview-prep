## Collaborative grilling

Use `$collaborative-grilling` when the user presents an open-ended idea, broad question, plan, consequential decision, or underspecified task whose outcome depends on missing context. Default to a short standard grilling pass: reflect the likely goal, offer a tentative hypothesis when useful, and ask one to three high-leverage questions before committing to a direction.

Do not grill routine factual questions or fully specified, low-risk, reversible work. Do not ask for context that can be safely inferred or inspected. Continue with stated assumptions when answers are optional.

User controls:

- “без гриллинга”, “просто сделай”, “just do it”, or equivalent: proceed directly unless a safety- or authorization-critical answer is missing.
- “глубокий грилинг” or equivalent: examine assumptions, alternatives, evidence, tradeoffs, and failure modes across multiple rounds.
- An explicit `$collaborative-grilling` invocation always enables the skill for that request.

## Context routing

- For work, career, compensation, resume, job search, interview preparation, professional skills, or technical progress, use `/Users/v1nkore/Documents/ChatGPT/ДЕНЬГИ` as the primary source of truth and prefer its newest dated records.
- For psychological context, internal conflicts, motivation, stress, habits, or consequential personal decisions, use `/Users/v1nkore/Documents/ChatGPT/МЕНТАЛКА` as the primary source of truth.
- Keep facts in their owning project. When both areas matter, use `ДЕНЬГИ` for professional facts and `МЕНТАЛКА` for decision context without copying sensitive details into unrelated outputs.
- For hardware, operating-system, driver, performance, peripheral, or device-specific setup questions, read `/Users/v1nkore/interview/assistant-context/SETUP.md` before recommending steps.
