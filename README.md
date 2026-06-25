# Agent Workflow Governance

![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
![Skill](https://img.shields.io/badge/skill-Codex%20Skill-111827.svg)
![Agents](https://img.shields.io/badge/agents-Codex%20%7C%20Claude%20Code%20%7C%20Cursor%20%7C%20Gemini-2563eb.svg)

> English version: [README.en.md](README.en.md)

一个用于 AI 辅助工程开发的轻量级工作流治理 Skill。

它面向 Codex、Claude Code、Cursor、Gemini CLI 等 AI 编码 Agent，帮助团队在真实工程改动中保持更稳定、更可复盘、更可交接的协作过程。

这个 Skill 解决的是：

```text
Agent 应该如何工作？
```

它不解决：

```text
Agent 应该记住什么、上下文属于哪里、未来如何恢复上下文？
```

这些属于更高层的上下文治理问题，不放在这个公开 Skill 中。

## 为什么需要它

AI 编码 Agent 已经很擅长写代码。但在长期项目和多人团队中，真正容易出问题的往往不是“代码能不能写出来”，而是：

- 改错了工作区；
- 分支状态不清楚；
- 没有保护用户已有改动；
- 重要决策没有留下记录；
- 改动影响了旧行为但没有检查；
- 验证证据不足；
- 交接时只剩一句模糊总结，后续很难继续。

Agent Workflow Governance 提供一套通用、克制、可复用的工作流护栏，让 Agent 在重要工程任务中先确认边界，再执行改动，最后清楚收尾。

## 适合谁使用

适合以下团队或个人：

- 正在使用 Codex、Claude Code、Cursor、Gemini CLI 等 AI 编码 Agent；
- 有多个仓库、多个工作区或多个分支；
- 希望 Agent 不覆盖用户已有改动；
- 希望每次重要任务结束后有清楚的验证、风险和交接状态；
- 希望重要决策、风险和后续事项能进入项目已有的记录体系；
- 不希望通用 Agent 擅自发明发布、部署或生产环境流程。

典型场景：

- 功能开发；
- Bug 修复；
- 重构；
- 依赖升级；
- 配置变更；
- API 或集成改动；
- 事故复盘后的规则沉淀；
- 人类与 Agent 之间的任务交接。

## 这个 Skill 会做什么

启用后，Agent 应该：

1. 识别真正负责该行为的仓库或工作区；
2. 判断是否需要持久化记录，例如 OpenSpec、ADR、Issue、设计文档或项目说明；
3. 修改前检查 Git 状态；
4. 保护用户已有改动和无关脏文件；
5. 有意识地选择分支；
6. 让改动范围保持聚焦；
7. 执行与任务相关的验证；
8. 检查是否影响已有行为；
9. 在任务结束时说明分支、提交、验证、风险、未完成事项和交接状态。

## 这个 Skill 不会做什么

它不会：

- 定义你的发布流程；
- 部署到生产环境；
- 替代 OpenSpec、ADR、Issue 或项目文档；
- 写入长期 Agent 记忆；
- 推断 Kubernetes、GitLab CI、镜像、回滚或客户数据处理流程；
- 替你决定公司内部合规规则。

如果任务涉及发布、回滚、CI/CD、共享环境、客户数据或生产操作，请使用你项目自己的发布或运维清单。

## 30 秒开始

克隆仓库：

```bash
git clone https://github.com/echopath-labs/agent-workflow-governance.git
cd agent-workflow-governance
```

把 Skill 链接到 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
ln -s "$(pwd)/skills/agent-workflow-governance" ~/.codex/skills/agent-workflow-governance
```

如果你不想使用软链接，也可以复制：

```bash
mkdir -p ~/.codex/skills
cp -R skills/agent-workflow-governance ~/.codex/skills/agent-workflow-governance
```

安装后重启 Codex 会话，让 Codex 重新发现 Skill。

## 如何触发

直接调用：

```text
$agent-workflow-governance
```

或者对 Agent 说：

```text
这次 Bug 修复请使用 Agent Workflow Governance。
```

```text
使用 $agent-workflow-governance，并在结束时说明分支、验证、风险和交接状态。
```

```text
修改前先使用 Agent Workflow Governance，确认工作区归属、Git 状态和相关持久化记录。
```

## 使用流程

Skill 会引导 Agent 按以下顺序工作：

1. 确认工作区和仓库边界；
2. 判断任务是否需要持久化记录；
3. 检查 Git 状态；
4. 确认分支策略；
5. 读取最小必要上下文；
6. 执行聚焦改动；
7. 做已有行为影响检查；
8. 运行必要验证；
9. 更新项目已有记录；
10. 输出清晰收尾状态。

## 持久化记录怎么选

优先使用仓库已经采用的记录系统，不要因为这个 Skill 提到了某个工具，就自动引入新的工具。

| 记录系统 | 适合记录什么 |
| --- | --- |
| OpenSpec | 结构化功能变更、需求、设计、任务、验收标准、规格演进 |
| Spec Kit | 已经采用 constitution/spec-driven 工作流的项目原则、规格和实现计划 |
| ADR | 架构决策、技术取舍、为什么选择 A 而不是 B |
| Issue | Bug、执行状态、优先级、分派、里程碑和交付管理 |
| Design Doc | 大范围方案、问题分析、跨团队评审、实现前设计 |
| Runbook | 可重复操作流程、事故处理、部署检查、回滚步骤 |
| README / Project Notes | 轻量使用说明、迁移说明、项目说明、人类可读指南 |

如果仓库没有任何持久化记录系统，Agent 不应该静默初始化 OpenSpec、Spec Kit 或 ADR 目录。它应该先说明建议写到哪里、为什么写到那里，并等待用户确认。

详细判断规则见 `skills/agent-workflow-governance/references/durable-record-decision.md`。

## 适合 / 不适合

适合：

- 多人协作项目；
- 长期维护项目；
- 需要分支、提交和验证纪律的工程任务；
- 希望 Agent 输出可审计工作状态的团队；
- 希望把“怎么让 Agent 做事”标准化的团队。

不适合：

- 一次性闲聊；
- 纯只读问答；
- 没有文件系统权限的普通 Chatbot；
- 需要完整发布、部署、生产操作治理的场景；
- 需要长期上下文记忆或项目认知系统的场景。

## 平台支持

| 平台 | 状态 | 说明 |
| --- | --- | --- |
| Codex | 支持 | 使用 Codex Skill 目录安装 |
| Claude Code | 可适配 | 可作为自定义 Skill 或项目规则迁移 |
| Cursor | 可适配 | 可迁移为项目规则或自定义指令 |
| Gemini CLI | 可适配 | 可迁移为可复用工作流说明 |
| 普通 Chatbot | 不推荐 | 缺少文件系统、Git 和验证能力时价值有限 |

## 仓库结构

```text
skills/
  agent-workflow-governance/
    SKILL.md
    agents/
      openai.yaml
    references/
      durable-record-decision.md
      git-lifecycle.md
      impact-review.md
      risk-and-context.md
```

### `SKILL.md`

Skill 主入口，包含触发描述和核心工作流。

### `agents/openai.yaml`

Codex Skill 列表和界面展示用的元数据。

### `references/`

按需加载的参考资料：

- `durable-record-decision.md`：判断是否需要持久化记录，以及记录归属。
- `git-lifecycle.md`：分支、提交、合并和主分支对齐。
- `impact-review.md`：已有行为影响检查。
- `risk-and-context.md`：高风险操作和上下文较重任务的处理。

## 开源边界

这个仓库只包含通用工作流治理，不包含私有项目治理体系。

请不要提交：

- 公司内部流程；
- 客户名称；
- 生产凭证；
- 私有仓库名称；
- 部署专用规则；
- 内部项目记忆；
- 私有上下文治理数据。

如果你要在团队内部扩展这个 Skill，建议在私有 fork 或私有工作区中维护项目专属规则。

## 贡献

见 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 安全

见 [SECURITY.md](SECURITY.md)。

## 开源协议

本项目采用 MIT 协议，见 [LICENSE](LICENSE)。
