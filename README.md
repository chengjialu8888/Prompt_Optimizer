# Prompt Optimizer

[![GitHub](https://img.shields.io/badge/GitHub-chengjialu8888%2FPrompt__Optimizer-181717?logo=github)](https://github.com/chengjialu8888/Prompt_Optimizer)
[![Skill](https://img.shields.io/badge/Codex%20Skill-prompt--optimizer-6f42c1)](prompt-optimizer/SKILL.md)

Turn ambitious, vague prompts into clear, executable, and measurable instructions.

[English](#english) · [中文](#中文)

## English

### Why this exists

Many prompts sound ambitious but leave the agent to guess what “excellent” means. Phrases such as “make it perfect,” “build it at AAA quality,” or “keep iterating until it feels right” communicate intent, but they do not define scope, evidence, or completion.

`prompt-optimizer` turns that ambition into an operational contract: what to do, what constraints to respect, how to validate the result, and when to stop.

### Why it is needed

High-quality work depends less on motivational language and more on reducing execution ambiguity. A strong prompt should answer:

- What outcome must be produced?
- What context, inputs, and tools are available?
- Which requirements are must-have, should-have, or optional?
- How should the work be split and iterated?
- What independent checks determine whether it is good enough?
- What should happen when the task is blocked or the target is infeasible?

Without these answers, agents commonly over-scope the task, optimize one visible detail, self-approve weak results, or continue indefinitely without a meaningful stopping rule.

### Core differentiation

`prompt-optimizer` is not a collection of generic “prompt tips.” It is a reusable optimization workflow built around four principles:

1. **Quality becomes testable** — Replace subjective adjectives with dimensions, examples, thresholds, checklists, and reviewer questions.
2. **Iteration becomes a closed loop** — Make the cycle explicit: `implement → inspect → critique → fix → retest`.
3. **Validation is independent** — Separate the builder from the reviewer when self-assessment is unreliable, and require evidence for completion claims.
4. **Orchestration stays honest** — Use sub-agents and loops when they are available and useful; never pretend unsupported commands or infinite execution are guaranteed.

The result preserves the original intent while making the task more feasible, scoped, and controllable.

### How to use it immediately

#### 1. Install the skill

Clone this repository, then place the `prompt-optimizer` directory in your Codex skills directory:

```bash
git clone https://github.com/chengjialu8888/Prompt_Optimizer.git
cp -R Prompt_Optimizer/prompt-optimizer ~/.codex/skills/
```

Restart or refresh your Codex session if the skill list is already open.

#### 2. Invoke it explicitly

```text
Use $prompt-optimizer to improve the following prompt while preserving my intent:

[paste your prompt here]
```

You can also ask for a specific output:

```text
Use $prompt-optimizer to:
1. diagnose the strengths and gaps in this prompt;
2. rewrite it into a ready-to-copy version;
3. add measurable acceptance criteria and a bounded iteration loop.
```

#### 3. Use it for common tasks

It is suitable for prompts involving:

- software and web application development;
- design, visual quality, and creative production;
- research and analysis;
- content and documentation;
- multi-agent workflows;
- testing, review, and quality assurance.

### What the skill produces

Unless another format is requested, it returns:

1. an optimized, ready-to-copy prompt;
2. a concise explanation of the key changes;
3. only the assumptions or decisions that materially affect execution.

For complex requests, the optimized prompt can include a role, objective, context, scope, constraints, work breakdown, execution loop, validation rubric, definition of done, blocker handling, and deliverables.

### Repository structure

```text
prompt-optimizer/
├── SKILL.md              # Core workflow and optimization rules
└── agents/
    └── openai.yaml       # Skill metadata for Codex interfaces
```

The skill is intentionally dependency-free. It does not require an API key, runtime package, or external service.

### Example transformation

Instead of:

> Make it perfect and keep going until it looks AAA.

The skill guides the agent toward:

> Evaluate the result across visual hierarchy, material fidelity, lighting, animation, interaction feedback, performance, and consistency. Fix must-have failures first, retest after each pass, and stop when all required checks pass. Record lower-priority gaps instead of iterating indefinitely.

### Contributing

Suggestions and pull requests are welcome. When proposing a change, include a concrete before/after prompt example and explain which ambiguity or failure mode the change addresses. See the [skill source](prompt-optimizer/SKILL.md) and open an [issue](https://github.com/chengjialu8888/Prompt_Optimizer/issues) for discussion.

### License

No license has been added yet. Add a license before redistributing the project or accepting external contributions.

## 中文

### 1 / 为什么做

很多 Prompt 看起来目标宏大，却把关键判断留给了 Agent：什么叫“完美”、哪些部分最重要、如何证明完成、什么时候应该停止。

像“做到 AAA 质量”“视觉上惊艳”“一直迭代到完美”这类表达能够传达愿望，却不能直接转化为稳定的执行标准。

[`prompt-optimizer`](prompt-optimizer/SKILL.md) 的目标，是把这种高层意图转成一份可执行的任务契约：明确目标、上下文、约束、拆解方式、验收依据和停止条件，同时尽量保留原始 Prompt 的野心与方向。

### 2 / 为什么需要

一个真正可执行的 Prompt，至少应该回答：

- 最终要产出什么？
- Agent 能使用哪些输入、文件和工具？
- 哪些是必须完成，哪些只是优化项？
- 任务应该如何拆解、并行和迭代？
- 用什么客观检查判断结果是否合格？
- 如果目标不可行、工具不可用或任务被阻塞，应该怎么办？

缺少这些信息时，常见结果是：范围无限扩大、只优化表面效果、Agent 自我验收、使用不存在的工具，或者持续循环却没有真正的完成标准。

### 3 / 核心差异化

这不是一份泛泛的 Prompt 小技巧清单，而是一套可复用的优化流程：

1. **把质量变成可验证标准**：将“完美”“高级”“漂亮”等形容词拆成维度、示例、阈值、检查表和评审问题。
2. **把迭代变成闭环**：明确执行 `实现 → 检查 → 批评 → 修复 → 回归验证`，而不是只要求“继续优化”。
3. **引入独立验证**：在自我评价不可靠时，分离实现者和审查者，并要求用证据支持“已完成”的判断。
4. **保持编排诚实**：只有在工具真实可用且确实有收益时才使用子 Agent、并行和循环；不会把 `/loop`、`ultracode` 等不确定命令假设成必然存在。

因此，它不是简单地把 Prompt 写得更长，而是让 Prompt 更清晰、更可测量、更可控、更容易交付。

### 4 / 如何立刻开用

#### 第一步：安装

通过 [GitHub 仓库](https://github.com/chengjialu8888/Prompt_Optimizer) 克隆项目，并将 skill 放进 Codex 的 skill 目录：

```bash
git clone https://github.com/chengjialu8888/Prompt_Optimizer.git
cp -R Prompt_Optimizer/prompt-optimizer ~/.codex/skills/
```

如果当前已经打开了 Codex 的 skill 列表，请重启或刷新会话。

#### 第二步：显式调用

```text
Use $prompt-optimizer to improve the following prompt while preserving my intent:

[粘贴你的 Prompt]
```

也可以直接指定你希望得到的结果：

```text
Use $prompt-optimizer to:
1. 分析这段 Prompt 的优点和缺口；
2. 改写成可以直接复制使用的版本；
3. 补充可衡量的验收标准和有边界的迭代流程。
```

#### 第三步：查看输出

默认会得到：

1. 一份可直接复制的优化后 Prompt；
2. 关键修改点说明；
3. 只保留真正影响执行的假设和待确认事项。

对于复杂任务，还会按需补充角色、目标、上下文、范围、约束、任务拆解、执行循环、验证标准、完成定义、阻塞处理和交付物说明。

### 适用场景

- [软件和 Web 应用开发](prompt-optimizer/SKILL.md)；
- [视觉设计和创意生产](prompt-optimizer/SKILL.md)；
- [研究、分析和写作](prompt-optimizer/SKILL.md)；
- [多 Agent 协作](prompt-optimizer/SKILL.md)；
- [测试、评审和质量保证](prompt-optimizer/SKILL.md)。

### 项目结构

```text
prompt-optimizer/
├── SKILL.md              # 核心工作流与优化规则
└── agents/
    └── openai.yaml       # Codex skill 元数据
```

项目本身没有运行时依赖，不需要 API Key、额外安装包或外部服务。你可以从 [`SKILL.md`](prompt-optimizer/SKILL.md) 查看完整规则，也可以通过 [Issues](https://github.com/chengjialu8888/Prompt_Optimizer/issues) 提交建议。

### 贡献

欢迎提交 [Issue](https://github.com/chengjialu8888/Prompt_Optimizer/issues) 或 [Pull Request](https://github.com/chengjialu8888/Prompt_Optimizer/pulls)。建议每次改动都附带一个具体的 Prompt 前后对比，并说明它解决了哪一种歧义或失败模式。

### 许可证

当前仓库尚未添加许可证。如果准备重新分发项目或接受外部贡献，请先补充合适的开源许可证。
