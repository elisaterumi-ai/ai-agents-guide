# LLMs, Prompts, Memory, and Context

## The Role of the LLM

A Large Language Model (LLM) processes natural language and produces outputs based on its input and provided context.

Within an agent, it helps interpret goals, weigh options, and propose the next action.

The model does not automatically execute external operations: that capability depends on tools and the system's execution harness.

## Prompts and Instructions

The system prompt describes the agent's expected role, goals, and constraints. Effective instructions tend to be explicit about:

- The task and expected outcome;
- Allowed information sources;
- Permitted and prohibited actions;
- When to ask for clarification;
- When to halt execution;
- How to convey uncertainty and format results.

Prompts help guide behavior, but they should never serve as the sole security boundary.

Permissions, input/output validation, and execution caps must also be enforced at the engineering layer.

## Context

Context is the set of information provided to the model for a given execution step.

It can include the current user query, instructions, relevant history, tool outputs, and excerpts retrieved from documents.

Excessive or irrelevant context increases costs and makes it harder for the model to isolate crucial information.

Therefore, context construction must prioritize relevance, freshness, and reliability.

✨ Read more: [What Every AI Engineer Should Know About Context Engineering](https://exploringartificialintelligence.substack.com/p/what-every-ai-engineer-should-know)

## Memory

Memory enables retaining useful information beyond a single execution step. Depending on the architecture, it can be:

- **Short-term:** Information needed during the current interaction or active task.
- **Persistent (Long-term):** Information that must remain available across future sessions.

Memory is not synonymous with complete chat history.

The system must define what data is worth keeping, how it can be updated or deleted, who is allowed to access it, and its retention policy.

## How These Elements Relate

The LLM interprets input using the available context and instructions.

If the agent needs extra information, orchestration can retrieve documents or invoke a tool. The resulting output is then injected into the context to inform subsequent decisions.

## Important Limitations

- Models can generate incorrect statements or unsupported inferences.
- Ambiguous instructions produce inconsistent behavior.
- Outdated data stored in memory can lead to flawed decisions.
- Sensitive data requires strict protection and compliance policies.
- A well-phrased, convincing response does not prove that a task was executed correctly.

## Best Practices

1. Formulate clear, testable instructions.
2. Provide only necessary context.
3. Distinguish retrieved facts from model inferences.
4. Validate outputs before triggering impactful actions.
5. Treat memory as a governed resource, not an unbounded dump.
6. Test behavior with ambiguous inputs and adversarial edge cases.

## Key Concepts

- The LLM contributes interpretation and decision-making capabilities.
- Prompts and context serve distinct yet complementary functions.
- Memory preserves information across steps or sessions.
- None of these elements eliminates the need for external validation and security controls.

## Questions for Reflection

1. Which information belongs in the context for a given task?
2. When is persistent memory useful — and when does it introduce risks?
3. Why shouldn't a prompt be considered a sufficient security barrier?

## Next Step

Read [Tools, knowledge bases, and orchestration](05-tools-knowledge-bases-and-orchestration.md).

## Reference

Educational summary based on *Introduction to AI Agents: Fundamentals, Architectures, and Applications*, by Elisa Terumi Rubel Schneider.
