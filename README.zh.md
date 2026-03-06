# effectorHQ 工作区模板

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/effectorHQ/workspace-templates/pulls)
[![effectorHQ](https://img.shields.io/badge/effectorHQ-250K%2B%20Stars-blue.svg)](https://github.com/openclaw/openclaw)

[中文文档](./README.zh.md) | [English](./README.md)

为 [OpenClaw](https://github.com/openclaw/openclaw) 提供现成的**工作区即内核**配置 - 个人AI助手，已有250K+星标。

## 什么是工作区模板?

OpenClaw 使用"工作区即内核"的模式，其中 `~/.openclaw/workspace/` 中的markdown文件定义AI代理的行为、自我认知和可用工具：

- **SOUL.md** — 个性、语气、行为指南和决策模式
- **AGENTS.md** — 代理定义和特定能力
- **TOOLS.md** — 可用工具、技能和集成
- **IDENTITY.md** — 代理身份、名称、角色和品牌
- **HEARTBEAT.md** — 健康检查、监控配置和状态端点

本仓库提供了经过实战验证的模板，您可以直接使用或针对特定工作流进行自定义。

## 快速开始

### 安装

选择下面的模板，然后复制到您的工作区：

```bash
cp -r templates/devops-bot/* ~/.openclaw/workspace/
# 或
cp -r templates/code-reviewer/* ~/.openclaw/workspace/
# 或任何其他模板...
```

然后重启您的OpenClaw实例：

```bash
openclaw restart
```

### 自定义工作区

要创建您自己的自定义工作区：

1. 选择最接近您使用场景的模板作为起点复制
2. 编辑 `SOUL.md` 定义您代理的个性和行为
3. 更新 `AGENTS.md` 添加您特定的代理能力
4. 修改 `TOOLS.md` 添加/删除您的代理将使用的工具
5. 使用您的品牌信息自定义 `IDENTITY.md`
6. 使用 `openclaw test` 增量测试

## 可用模板

### 1. DevOps 机器人
一个以生产为中心的DevOps工程师代理，擅长基础设施管理。

**适用于：** 基础设施团队、Kubernetes操作员、云工程师、CI/CD自动化

**能力：**
- 容器编排（Docker、Kubernetes）
- 基础设施即代码（Terraform、CloudFormation）
- 云提供商CLI（AWS、GCP、Azure）
- 包管理器和部署工具（Helm、Ansible）
- 健康监控和日志分析

**代理个性：** 精确、谨慎、爆炸范围感知。永远不会在没有明确确认的情况下运行破坏性命令。通过清晰的状态更新进行沟通。

```bash
cp -r templates/devops-bot/* ~/.openclaw/workspace/
```

---

### 2. 代码审查员
一个彻底的代码审查代理，提供建设性的、具体的反馈。

**适用于：** 工程团队、拉取请求自动化、代码质量、初级开发人员指导

**能力：**
- 多语言代码分析
- 风格和linting检查
- 性能优化检测
- Bug和安全模式识别
- 可操作的改进建议

**代理个性：** 彻底、建设性、永远不会尖刻。专注于正确性、可读性和性能。总是引用相关模式和最佳实践。

```bash
cp -r templates/code-reviewer/* ~/.openclaw/workspace/
```

---

### 3. 个人助手
一个温暖、主动的通用助手，用于日常生产力。

**适用于：** 个人专业人士、生产力自动化、上下文管理、日程安排

**能力：**
- 日历和日程管理
- 邮件分类和优先级排序
- 笔记和知识捕获
- 任务管理和提醒
- 网络研究和信息收集

**代理个性：** 温暖、主动、有上下文意识。在采取行动前提出澄清问题。跨对话记住上下文。

```bash
cp -r templates/personal-assistant/* ~/.openclaw/workspace/
```

---

### 4. 安全审计员
一个专注于威胁检测和漏洞评估的安全代理。

**适用于：** 安全团队、DevSecOps、合规性审计、漏洞扫描

**能力：**
- 漏洞扫描和评估
- 配置审计
- 密钥检测和防护
- 依赖分析
- 严重程度分类和报告

**代理个性：** 设计上偏执，假设敌对环境。使用清晰的严重程度级别（Critical/High/Medium/Low）报告发现。永远不会忽视警告。

```bash
cp -r templates/security-auditor/* ~/.openclaw/workspace/
```

---

## 目录结构

```
workspace-templates/
├── README.md
├── README.zh.md
├── LICENSE
├── CHANGELOG.md
└── templates/
    ├── devops-bot/
    │   ├── SOUL.md
    │   ├── AGENTS.md
    │   ├── TOOLS.md
    │   ├── IDENTITY.md
    │   └── HEARTBEAT.md
    ├── code-reviewer/
    │   ├── SOUL.md
    │   ├── AGENTS.md
    │   ├── TOOLS.md
    │   ├── IDENTITY.md
    │   └── HEARTBEAT.md
    ├── personal-assistant/
    │   ├── SOUL.md
    │   ├── AGENTS.md
    │   ├── TOOLS.md
    │   ├── IDENTITY.md
    │   └── HEARTBEAT.md
    └── security-auditor/
        ├── SOUL.md
        ├── AGENTS.md
        ├── TOOLS.md
        ├── IDENTITY.md
        └── HEARTBEAT.md
```

## 文件说明

### SOUL.md
定义您代理的核心个性和决策行为。这是最重要的文件 — 它决定了您的代理如何思考、优先级划分、处理边界情况和交流。

SOUL.md中的示例主题：
- 核心性格特征和语气
- 决策框架和优先级
- 错误处理和恢复策略
- 沟通风格和响应速度
- 风险厌恶和安全考虑
- 上下文管理和记忆模式

### AGENTS.md
声明代理的特定能力和操作范围。此文件定义代理擅长的领域和可以做出的贡献。

示例部分：
- 代理名称和专业领域
- 具体能力和专长
- 已知限制和免责声明
- 与其他代理的协作模式
- 成功指标和性能目标

### TOOLS.md
列出所有可用工具和集成，代理可以调用。每个工具都包括代理何时以及如何使用它。

示例格式：
```markdown
## Docker
- **目的：** 容器构建、运行、调试
- **何时使用：** 构建镜像、部署容器、调试运行时问题
- **风险等级：** 高（可修改系统状态）
```

### IDENTITY.md
代理的品牌和身份信息。包括名称、角色、头像描述和联系信息。

### HEARTBEAT.md
健康检查配置、监控设置和状态报告端点。

## 贡献

我们欢迎贡献！以下是方法：

1. **Fork** 仓库
2. **创建特性分支** (`git checkout -b feature/my-template`)
3. **添加您的模板**，遵循上述结构
4. **全面测试** 您的使用场景
5. **提交PR** 并描述何时/为什么您的模板有用

### 模板提交指南

- 模板应该是自包含的，复制后立即可用
- SOUL.md应该详细（最少30-50行）并包含具体的行为指南
- TOOLS.md应该列出与代理领域相关的工具
- 即使很少也包含HEARTBEAT.md
- 在提交之前在真实的OpenClaw实例中充分测试模板
- 在README.md中添加您的模板并提供清晰的描述

## 许可证

所有工作区模板均在MIT许可证下许可。详见 [LICENSE](./LICENSE)。

版权所有 (c) 2026 effectorHQ 贡献者

## 支持

- **文档：** [OpenClaw文档](https://docs.openclaw.dev)
- **问题：** [GitHub Issues](https://github.com/effectorHQ/workspace-templates/issues)
- **讨论：** [GitHub Discussions](https://github.com/effectorHQ/workspace-templates/discussions)
- **主项目：** [OpenClaw仓库](https://github.com/openclaw/openclaw)

## 致谢

这些模板由effectorHQ社区维护，灵感来自OpenClaw在全球DevOps团队、工程组织和安全团队的生产部署。
