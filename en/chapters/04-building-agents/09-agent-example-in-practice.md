# Agent Example in Practice

## Scenario

Imagine an agent assisting a corporate team by answering questions based on internal documentation. Its objective is to provide well-grounded answers anchored in authorized documents, explicitly flagging whenever sufficient evidence is unavailable.

This example is conceptual: it does not prescribe a specific framework or imply that any agent inherently achieves these abilities without proper integration and configuration.

## Goal and Boundaries

**Goal:** Answer the user's question using authorized documents and cite the referenced sources.

**Boundaries:** Never access out-of-scope files, never fabricate citations, and never leak data the requesting user is unauthorized to view. If evidence is lacking, the agent must acknowledge this limitation or prompt the user for clarification.

## Candidate Architecture Components

- An LLM to interpret the query and compose responses.
- A system prompt outlining behavior, style, and safety boundaries.
- A document retrieval pipeline.
- A tool interface to query the authorized document store.
- An orchestration layer to sequence execution stages.
- Access control mechanisms, telemetry logging, and test suites.

## Execution Flow

1. **Receive the query:** Interpret what the user wants to know.
2. **Verify scope:** Ensure the request respects user authorization and system permissions.
3. **Retrieve sources:** Fetch relevant excerpts from authorized document stores.
4. **Evaluate evidence:** Determine if retrieved passages are sufficient and relevant.
5. **Draft response:** Synthesize the finding, explicitly referencing source documents.
6. **Validate output:** Verify that assertions are factually supported by sources and that sensitive data is protected.
7. **Complete or escalate:** Deliver the answer, request clarification, or route to human review.

## Failure Modes to Consider

- Search fails to retrieve the correct document.
- Documents are obsolete, incomplete, or mutually contradictory.
- The model misinterprets an excerpt.
- The user requests content outside their permissions.
- The retrieval tool times out or crashes.

The system must anticipate these outcomes. For example, it should report that evidence is insufficient rather than filling gaps with plausible hallucinations.

## How to Evaluate

Curate a representative benchmark dataset of questions and establish evaluation metrics such as:

- Factual accuracy;
- Alignment between the generated answer and retrieved sources;
- Citation quality;
- Graceful handling of unanswerable questions;
- Adherence to access control policies;
- Latency and token cost;
- Robustness against adversarial prompts or ambiguity.

Evaluation should combine automated metrics, spot checks, and human domain-expert reviews.

## Variations

If the use case requires real-time information, the agent can query a live, authorized API. If it involves actions with real-world side effects, such as sending emails or updating records, that operation must enforce strict input validations and explicit human confirmation policies.

## Key Concepts

- A use case requires a clear goal, defined scope, and measurable completion criteria.
- Tools must be authorized and failure modes anticipated.
- Outputs must be anchored in verified knowledge sources.
- Evaluation and security are architectural pillars, not optional final steps.

## Questions for Reflection

1. How should the agent respond when evidence is insufficient?
2. Which controls are necessary to safeguard internal enterprise documents?
3. How can you programmatically verify that citations actually support the claims made?

## Next Step

Read [Fundamentals of multi-agent systems](../05-multi-agent-systems/10-multi-agent-systems-fundamentals.md).

## Reference

Educational summary based on *Introduction to AI Agents: Fundamentals, Architectures, and Applications*, by Elisa Terumi Rubel Schneider.
