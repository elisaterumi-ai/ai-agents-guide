# Tools, Knowledge Bases, and Orchestration

## Why Do These Components Matter?

An agent needs to interact with systems and data to carry out tasks that go beyond simple text generation.

> Tools, knowledge bases, and orchestration turn intent into an executable process.

## Tools

Tools are interfaces to external operations, such as querying an API, searching data, accessing a file system, or performing an authorized transaction.

The model may recommend using a tool, but the application is responsible for validating parameters, enforcing permissions, and executing the operation.

A well-designed tool should have a clear purpose, defined inputs, predictable outputs, and minimum necessary privileges.

Through these integrations, an agent turns decisions into environmental actions — such as checking product availability or scheduling an appointment on a calendar.

> Remember: Actions with significant real-world consequences should often require human confirmation.

### How a Tool is Used

The application registers tools alongside descriptive metadata outlining their functions and required schemas.

Based on its objective and current context, the model selects an appropriate tool and populates the invocation arguments.

The application validates the request, executes the call, and returns the output. This result becomes part of the context available for the agent's next step.

For this reason, tool descriptions must be unambiguous.

The system needs to distinguish, for example, between an operation that merely retrieves an order status and one that cancels the order.

### Handling Errors

Tools can fail, receive invalid parameters, or return incomplete responses.

The agent must handle these situations gracefully to decide whether to retry, explore an alternative path, or notify the user that the task is blocked.

When dealing with state-changing operations, retrying requires caution. If creating a calendar event times out without a response, that does not mean the event was not created.

Before retrying, the application should inspect current state to prevent duplication.

Similarly, tool output must be interpreted in context.

A failure while checking inventory does not prove a product is out of stock; it simply means the information could not be retrieved.

## Knowledge Bases and RAG

LLMs are trained on massive datasets, but the knowledge acquired during training has limitations.

It can become outdated and does not automatically include private internal documents or organizational records.

When a task depends on such information, the application must query external sources, which can include documents, databases, APIs, or enterprise software.

### What is RAG?

**RAG**, or *Retrieval-Augmented Generation*, is an approach combining information retrieval with response generation.

Rather than relying strictly on the model's parametric knowledge, the application fetches relevant content from external stores and injects it as context.

The model then utilizes these excerpts to formulate its response.

Imagine an assistant answering questions about company policies. When asked about reimbursement rules, it retrieves the relevant passages and references them to explain the policy.

This grounds the response in verified organizational documents.

✨ Read more about RAG:

- [Building Chatbots with RAG Using LangChain](https://exploringartificialintelligence.substack.com/p/creating-chatbots-with-rag-using)
- [Qwen3 Embedding: A New Benchmark for Semantic Search and RAG](https://exploringartificialintelligence.substack.com/p/qwen3-embedding-a-new-milestone-for)
- [Multimodal RAG in Practice with Open-Source Models](https://exploringartificialintelligence.substack.com/p/multimodal-rag-in-practice-with-open)
- [How to Build Your Own Local RAG with Wikipedia and LEANN](https://exploringartificialintelligence.substack.com/p/how-to-build-your-own-local-rag-with)

### How Retrieval Works

Documents must be structured to allow efficient querying.

A common pattern divides material into chunks and uses vector embeddings to find passages semantically similar to the user's question.

Keyword search or hybrid search strategies can also be combined depending on the use case and data format.

Response quality depends as much on retrieval accuracy as on generative fluency.

If search returns an incomplete excerpt or an outdated version, the model may produce an incorrect answer. Source lineage, update frequency, and access controls are therefore essential.

### What Changes with Agentic RAG?

In standard, fixed RAG pipelines, the application dictates exactly when and how search occurs. In **Agentic RAG**, the agent determines retrieval strategy dynamically during execution.

It can pick between multiple knowledge sources, reformulate queries, or trigger secondary searches upon realizing that initial findings are insufficient.

For instance, when examining a travel reimbursement rule, the agent might first query general company policy, and subsequently look up international travel exceptions.

The second search emerges from insights gained during execution.

This adaptability accommodates multi-step queries, but also introduces additional decision steps, cost, and latency.

✨ Read more: [Do You Know the Difference Between RAG and Agentic RAG?](https://exploringartificialintelligence.substack.com/p/do-you-know-the-difference-between)

### Evaluating External Knowledge

RAG improves grounding, but does not completely eliminate hallucinations.

A model can still misinterpret retrieved excerpts or draw conclusions unsupported by the text.

It is crucial to verify whether retrieved content actually answers the prompt and whether the final response faithfully adheres to facts.

When evidence is lacking, the system should acknowledge that limitation clearly.

## Orchestration

Orchestration governs execution flow.

It dictates when to call the model, when to execute a tool, how to handle exceptions, how many loop iterations are allowed, and when to conclude the task.

Without explicit boundaries, an agent can get stuck in endless loops, inflate costs, or leave tasks unresolved.

Stopping criteria and fallback strategies are core design imperatives.

## Example Workflow

1. Receive the user goal.
2. Identify missing information.
3. Retrieve documents or invoke an authorized tool.
4. Interpret output and assess whether additional actions are needed.
5. Validate results against completion criteria.
6. Return response, request clarification, or escalate to human review.

This is an illustrative flow, not a rigid sequence required for every agent.

## Essential Safeguards

- Restrict tools strictly to required capabilities.
- Validate inputs and outputs.
- Handle exceptions and unexpected payloads cleanly.
- Define boundaries for time, budget, and iteration count.
- Log significant events without recording unnecessary sensitive data.
- Require human approval prior to executing sensitive actions.

## Key Concepts

- Tools allow agents to act on external systems.
- Knowledge bases supply reference information.
- RAG enriches context with retrieved data, but does not eliminate hallucinations on its own.
- Orchestration directs execution steps and enforces stopping conditions.
- Permissions and validations must be handled outside the model.

## Questions for Reflection

1. What is the difference between retrieving information and executing an action?
2. What happens if an agent lacks explicit stopping conditions?
3. Which tools should require confirmation prior to execution?

## Next Step

Proceed to [Reasoning and execution loop](../03-reasoning-patterns/06-reasoning-and-execution-loop.md).

## Reference

Educational summary based on *Introduction to AI Agents: Fundamentals, Architectures, and Applications*, by Elisa Terumi Rubel Schneider.
