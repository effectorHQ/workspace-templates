# effectorHQ Workspace Templates

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache-2.0-yellow.svg)](https://opensource.org/licenses/Apache-2.0)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/effectorHQ/workspace-templates/pulls)
[![effectorHQ](https://img.shields.io/badge/effectorHQ-250K%2B%20Stars-blue.svg)](https://github.com/openclaw/openclaw)

[中文文档](./README.zh.md) | [English](./README.md)

Ready-made **Workspace-as-Kernel** configurations for [OpenClaw](https://github.com/openclaw/openclaw), the personal AI assistant with 250K+ stars.

## What are Workspace Templates?

OpenClaw uses a "Workspace-as-Kernel" pattern where markdown files in `~/.openclaw/workspace/` define how your AI agent behaves, what it knows about itself, and what tools it can use:

- **SOUL.md** — Personality, tone, behavioral guidelines, and decision-making patterns
- **AGENTS.md** — Agent definitions and specific capabilities
- **TOOLS.md** — Available tools, skills, and integrations for execution
- **IDENTITY.md** — Agent identity, name, role, and branding
- **HEARTBEAT.md** — Health check, monitoring config, and status endpoints

This repository provides battle-tested templates that you can use immediately or customize for your specific workflows.

## Quick Start

### Installation

Choose a template below, then copy it to your workspace:

```bash
cp -r templates/devops-bot/* ~/.openclaw/workspace/
# or
cp -r templates/code-reviewer/* ~/.openclaw/workspace/
# or any other template...
```

Then restart your OpenClaw instance:

```bash
openclaw restart
```

### Custom Workspace

To create your own custom workspace:

1. Copy a template that's closest to your use case as a starting point
2. Edit `SOUL.md` to define your agent's personality and behavior
3. Update `AGENTS.md` with your specific agent capabilities
4. Modify `TOOLS.md` to add/remove tools your agent will use
5. Customize `IDENTITY.md` with your agent's branding
6. Test incrementally with `openclaw test`

## Available Templates

### 1. DevOps Bot
A production-focused DevOps engineer agent that excels at infrastructure management.

**Best for:** Infrastructure teams, Kubernetes operators, cloud engineers, CI/CD automation

**Capabilities:**
- Container orchestration (Docker, Kubernetes)
- Infrastructure-as-Code (Terraform, CloudFormation)
- Cloud provider CLIs (AWS, GCP, Azure)
- Package managers and deployment tools (Helm, Ansible)
- Health monitoring and log analysis

**Agent Personality:** Precise, cautious, blast-radius aware. Never runs destructive commands without explicit confirmation. Communicates in clear status updates.

```bash
cp -r templates/devops-bot/* ~/.openclaw/workspace/
```

---

### 2. Code Reviewer
A thorough code review agent that provides constructive, specific feedback.

**Best for:** Engineering teams, pull request automation, code quality, junior dev mentoring

**Capabilities:**
- Multi-language code analysis
- Style and linting checks
- Performance optimization detection
- Bug and security pattern recognition
- Actionable improvement suggestions

**Agent Personality:** Thorough, constructive, never mean-spirited. Focuses on correctness, readability, and performance. Always cites relevant patterns and best practices.

```bash
cp -r templates/code-reviewer/* ~/.openclaw/workspace/
```

---

### 3. Personal Assistant
A warm, proactive general-purpose assistant for daily productivity.

**Best for:** Individual professionals, productivity automation, context management, scheduling

**Capabilities:**
- Calendar and scheduling management
- Email triage and prioritization
- Note-taking and knowledge capture
- Task management and reminders
- Web research and information gathering

**Agent Personality:** Warm, proactive, contextually aware. Asks clarifying questions before taking actions. Remembers context across conversations.

```bash
cp -r templates/personal-assistant/* ~/.openclaw/workspace/
```

---

### 4. Security Auditor
A security-focused agent designed for threat detection and vulnerability assessment.

**Best for:** Security teams, DevSecOps, compliance audits, vulnerability scanning

**Capabilities:**
- Vulnerability scanning and assessment
- Configuration auditing
- Secret detection and prevention
- Dependency analysis
- Severity classification and reporting

**Agent Personality:** Paranoid by design, assumes hostile environments. Reports findings with clear severity levels (Critical/High/Medium/Low). Never dismisses warnings.

```bash
cp -r templates/security-auditor/* ~/.openclaw/workspace/
```

---

## Directory Structure

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

## File Descriptions

### SOUL.md
Defines the core personality and decision-making behavior of your agent. This is the most important file—it determines how your agent thinks, prioritizes decisions, handles edge cases, and communicates.

Example topics in a SOUL.md:
- Core personality traits and tone
- Decision-making frameworks and priorities
- Error handling and recovery strategies
- Communication style and responsiveness
- Risk aversion and safety considerations
- Context management and memory patterns

### AGENTS.md
Declares the agent's specific capabilities and operational scope. This file defines what the agent is an expert at and where it can contribute.

Example sections:
- Agent name and expertise areas
- Specific capabilities and specializations
- Known limitations and disclaimers
- Collaboration patterns with other agents
- Success metrics and performance goals

### TOOLS.md
Lists all available tools and integrations the agent can invoke. Each tool includes when and how the agent should use it.

Example format:
```markdown
## Docker
- **Purpose:** Container building, running, debugging
- **When to use:** Building images, deploying containers, debugging runtime issues
- **Risk level:** High (can modify system state)
```

### IDENTITY.md
Branding and identity information for the agent. Includes name, role, avatar description, and contact information.

### HEARTBEAT.md
Health check configuration, monitoring setup, and status reporting endpoints.

## Contributing

We welcome contributions! Here's how:

1. **Fork** the repository
2. **Create a feature branch** (`git checkout -b feature/my-template`)
3. **Add your template** following the structure above
4. **Test thoroughly** with your use case
5. **Submit a PR** with description of when/why your template is useful

### Template Submission Guidelines

- Templates should be self-contained and work immediately after copying
- SOUL.md should be detailed (30-50 lines minimum) with concrete behavior guidelines
- TOOLS.md should list tools relevant to the agent's domain
- Include a HEARTBEAT.md even if minimal
- Test the template in a real OpenClaw instance before submitting
- Add your template to the README.md with a clear description

## License


This project is currently licensed under the Apache 2.0 License 。

All workspace templates are licensed under the Apache License 2.0. See [LICENSE](./LICENSE) for details.

Copyright (c) 2026 effectorHQ Contributors

## Support

- **Documentation:** [OpenClaw Docs](https://docs.openclaw.dev)
- **Issues:** [GitHub Issues](https://github.com/effectorHQ/workspace-templates/issues)
- **Discussions:** [GitHub Discussions](https://github.com/effectorHQ/workspace-templates/discussions)
- **Main Project:** [OpenClaw Repository](https://github.com/openclaw/openclaw)

## Acknowledgments

These templates are maintained by the effectorHQ community and inspired by production deployments of OpenClaw across DevOps teams, engineering organizations, and security teams worldwide.
