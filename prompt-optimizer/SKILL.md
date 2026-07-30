---
name: prompt-optimizer
description: Analyze and rewrite prompts for coding, content, research, design, and agentic tasks. Use when the user asks to optimize, polish, generalize, strengthen, restructure, or critique a prompt, or wants a vague goal turned into clear roles, constraints, workflows, validation criteria, and output formats.
---

# Prompt Optimizer

## Purpose

Turn a high-level request into an executable prompt without changing the user's intended outcome. Preserve useful ambition and domain context, but replace ambiguity with scope, priorities, observable acceptance criteria, and an appropriate execution loop.

Match the user's language unless they request another language. Do not assume that a longer prompt is a better prompt.

## Workflow

### 1. Extract the prompt contract

Identify the following before rewriting:

- **Outcome**: what must be produced, changed, decided, or learned.
- **Context**: audience, users, existing assets, background, references, and starting state.
- **Inputs**: files, data, links, examples, APIs, or information the agent may use.
- **Constraints**: technology, platform, format, style, compatibility, time, budget, and safety boundaries.
- **Quality bar**: benchmarks, priorities, examples, and non-negotiable requirements.
- **Deliverables**: exact artifacts, locations, formats, and explanation expected at the end.
- **Validation**: how to determine that the result works or is good enough.
- **Stopping rule**: when to finish, what to do when blocked, and any iteration or resource limit.

Separate must-haves, preferences, and motivational rhetoric. Preserve must-haves; convert useful preferences into priorities; replace rhetoric with testable requirements.

### 2. Diagnose the original prompt

Briefly assess:

- What is already strong: target benchmark, decomposition, role separation, iteration, independent review, technical constraints, or clear deliverables.
- What is underspecified: scope, inputs, platform, output format, dependencies, definition of done, or failure handling.
- What is not measurable: words such as *perfect*, *AAA*, *best*, *beautiful*, or *high quality*.
- What is infeasible or unsupported: infinite work, unavailable commands, inaccessible references, impossible parity claims, or capabilities the runtime does not provide.
- What may conflict: broad scope versus deadline, quality versus performance, or multiple incompatible constraints.

Do not criticize ambition merely because it is ambitious. Explain which parts need operational definitions.

### 3. Design the improved prompt

Use only the sections that help the task. For a complex task, prefer this order:

1. **Role** — define the agent's relevant expertise and responsibility.
2. **Objective** — state the primary outcome in one or two sentences.
3. **Context and inputs** — identify what is known, available, or missing.
4. **Scope and priorities** — distinguish must-have, should-have, stretch, and explicit non-goals.
5. **Constraints** — state tools, technology, platform, style, compatibility, and resource limits.
6. **Plan and work breakdown** — split the work into coherent tracks or phases; parallelize only independent work and only when the runtime supports it.
7. **Execution loop** — define an actionable cycle such as `implement → inspect → critique → fix → retest`.
8. **Validation rubric** — specify observable checks, thresholds, test cases, reference comparisons, or reviewer questions.
9. **Stopping and escalation** — define the pass condition, maximum useful iteration, blocker handling, and what to report when the target cannot be reached.
10. **Deliverables and final response** — state the files, formats, verification evidence, and concise handoff expected.

For a simple task, collapse these into a short, direct prompt. Do not add agent teams, loops, or elaborate rubrics when they would create overhead without improving the result.

### 4. Make quality executable

Translate subjective standards into a small, prioritized rubric. For example:

- Replace “make it AAA” with named dimensions such as visual hierarchy, material fidelity, lighting, animation quality, interaction feedback, performance, accessibility, and consistency.
- Replace “make it perfect” with a pass threshold, prioritized defects, and a bounded review loop.
- Replace “compare it to the best product” with a stated reference, comparison dimensions, test conditions, and a rule for recording gaps.
- Replace “keep going until wowed” with “continue until all must-have checks pass; then report remaining lower-priority gaps.”

Use measurable criteria where possible: frame rate, latency, test coverage, error rate, supported browsers, required sections, visual review questions, or a checklist with pass/fail outcomes. Use qualitative criteria only when accompanied by examples or reviewer guidance.

### 5. Make orchestration conditional and honest

Use sub-agents, tools, loops, or special commands only if they are actually available and useful. If availability is unknown, write conditional instructions such as:

> If independent agents are available, assign them to isolated workstreams and have one reviewer evaluate the integrated result. Otherwise, perform the same passes sequentially.

Never invent a command such as `/loop` or `ultracode` as if it were a guaranteed runtime feature. Express the underlying behavior explicitly: repeat the review-fix-test cycle, use the available tools, and stop at the defined threshold.

Separate builders from reviewers when independent validation matters. Give reviewers the rubric and the artifact, not the builder's self-assessment. Require evidence for claims of completion.

### 6. Preserve feasibility and boundaries

Keep the user's reference products, examples, and technical choices when they clarify intent, but avoid promising exact parity with inaccessible or much larger systems. Turn an oversized request into a staged plan:

- **Core deliverable**: the smallest complete result that satisfies the main goal.
- **Quality pass**: the highest-impact refinements.
- **Stretch items**: optional improvements if time and resources permit.

State assumptions only when they are low-risk. Ask for clarification when an unresolved choice would materially change the task. Otherwise, make a reasonable assumption and expose it in the final notes.

## Default output

Unless the user requests a different format, return:

1. **优化后的 Prompt** — put the ready-to-copy prompt in a code block first.
2. **关键改动** — explain the most important improvements in a short list.
3. **假设与待确认项** — include only decisions that materially affect execution.

When the user asks only for diagnosis, provide the diagnosis without silently rewriting the prompt. When the user asks for several variants, provide a full version and a compact version, and explain the trade-off briefly.

## Ready-to-copy pattern

Adapt this pattern instead of copying every section mechanically:

```text
You are [relevant role].

Objective:
[one concrete outcome]

Context and inputs:
[starting state, references, available files, and assumptions]

Scope and priorities:
- Must have: [non-negotiable outcomes]
- Should have: [important improvements]
- Stretch: [optional work]
- Out of scope: [explicit boundaries]

Constraints:
[technology, platform, format, style, compatibility, resources, and safety limits]

Execution:
1. Inspect the current state and identify risks.
2. Break the work into independent tracks where useful.
3. Implement the highest-priority path first.
4. Review the result against the rubric.
5. Fix the highest-impact failures and retest.

Validation rubric:
- [observable criterion 1]
- [observable criterion 2]
- [test, comparison, or reviewer check]

Definition of done:
[pass threshold, iteration limit, and blocker behavior]

Deliverables:
[exact artifacts, formats, verification evidence, and final summary]
```

## Quality checklist

Before returning an optimized prompt, verify:

- Another capable agent could execute it without guessing the main outcome.
- The requested output and completion condition are explicit.
- Subjective quality terms have examples, dimensions, or a rubric.
- Constraints do not conflict, and the scope is feasible for the stated environment.
- Parallel work is genuinely independent and conditional on available tooling.
- Iteration includes a reviewer, a concrete check, and a stopping rule.
- The prompt preserves the user's intent instead of replacing it with a generic task.
- The final response format is appropriate to the user's request and not overloaded with boilerplate.
