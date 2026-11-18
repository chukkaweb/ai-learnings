# Claude Code – Complete Notes

A practical guide to Claude Code covering terminal commands, usage, keyboard shortcuts, skills, subagents, rules, prompt engineering, workflows, and productivity tips.

## Table of Contents

1. [Introduction](#1-introduction)
2. [Claude Code Fundamentals](#2-claude-code-fundamentals)
3. [Installation and Setup](#3-installation-and-setup)
4. [Terminal Commands](#4-terminal-commands)
5. [Slash Commands](#5-slash-commands)
6. [Keyboard Shortcuts](#6-keyboard-shortcuts)
7. [Claude Code Core Concepts](#7-claude-code-core-concepts)
8. [CLAUDE.md – Project Instructions](#8-claudemd--project-instructions)
9. [Rules](#9-rules)
10. [Skills](#10-skills)
11. [Subagents](#11-subagents)
12. [Skills vs Agents vs Rules](#12-skills-vs-agents-vs-rules)
13. [Prompt Engineering](#13-prompt-engineering)
14. [Useful Prompts for Developers](#14-useful-prompts-for-developers)
15. [Claude Code Workflows](#15-claude-code-workflows)
16. [Pro Tips and Best Practices](#16-pro-tips-and-best-practices)
17. [Security and Permissions](#17-security-and-permissions)
18. [Troubleshooting](#18-troubleshooting)
19. [Interview Questions and Answers](#19-interview-questions-and-answers)
20. [Official References](#20-official-references)

---

# 1. Introduction

## What is Claude Code?

Claude Code is an agentic coding tool developed by Anthropic that works directly with your codebase through the terminal, IDE, and other supported environments.

It can understand project structure, read and modify files, execute commands, debug issues, run tests, and perform code reviews.

Unlike traditional AI chat interfaces, Claude Code can interact with your development environment and perform multi-step coding tasks using available tools and permissions.

### Real-world use cases

- Generate new components and features.
- Understand an existing codebase.
- Refactor legacy code.
- Identify bugs and security vulnerabilities.
- Generate unit tests.
- Review pull requests.
- Debug application issues.
- Generate technical documentation.
- Automate repetitive development tasks.
- Execute multi-step development workflows.

### Example

Instead of manually asking:

"How do I create an Angular component?"

You can ask Claude Code:

"Analyze my Angular project and create a reusable user-profile component following the existing project architecture and coding standards."

Claude can inspect the existing code, understand the conventions, and implement the component.

## Claude Code vs Claude Chat

| Feature | Claude Chat | Claude Code |
|---|---|---|
| General questions | Yes | Yes |
| Code explanations | Yes | Yes |
| Read project files | Through uploaded files/connectors | Directly from working directory |
| Modify source files | No direct local editing | Yes, with permissions |
| Execute terminal commands | No direct local terminal access | Yes, with permissions |
| Run tests | No direct local execution | Yes |
| Multi-step coding tasks | Limited | Yes |
| Project-level instructions | Conversation context | CLAUDE.md |
| Custom agents and skills | Product-dependent | Yes |

---

# 2. Claude Code Fundamentals

## How Claude Code works

Claude Code uses an agentic workflow.

1. Understand the user's request.
2. Analyze the existing project.
3. Identify relevant files and dependencies.
4. Create an execution plan when needed.
5. Use available tools to perform the task.
6. Review the changes.
7. Run tests and validate the implementation.
8. Report the results.

### Basic architecture

```text
Developer
    |
    v
Claude Code CLI
    |
    v
User Prompt
    |
    v
Claude Model
    |
    v
Agentic Decision Making
    |
    +----------------+
    |                |
    v                v
Read/Edit Files   Execute Commands
    |                |
    v                v
Code Changes     Test Execution
    |                |
    +----------------+
             |
             v
      Final Response
```

### Important concepts

| Concept | Description |
|---|---|
| Model | AI model responsible for understanding and generating responses |
| Context Window | Information available to the model during a session |
| Tools | Capabilities such as reading files, editing files, and executing commands |
| Agentic Workflow | Model decides which actions to perform to complete a task |
| Skills | Reusable instructions and workflows |
| Subagents | Specialized agents that work on specific tasks |
| Rules | Persistent instructions that guide coding behavior |
| MCP | Model Context Protocol for connecting external tools and data |
| Hooks | Automation triggered by specific lifecycle events |
| Permissions | Controls that determine which actions require approval |

---

# 3. Installation and Setup

## Prerequisites

- macOS, Linux, or supported Windows environment.
- Internet connection.
- Supported authentication method.
- Node.js 18+ for the npm installation method.

## Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

Modern Note: Anthropic also provides native installation options. Check the official installation guide for the recommended method for your operating system.

## Verify installation

```bash
claude --version
```

## Check installation health

```bash
claude doctor
```

## Navigate to your project

```bash
cd my-project
```

## Start Claude Code

```bash
claude
```

Complete the authentication process when prompted.

## Update Claude Code

```bash
claude update
```

## Basic setup workflow

```text
Install Claude Code
       |
       v
Verify Installation
       |
       v
Authenticate
       |
       v
Navigate to Project
       |
       v
Run claude
       |
       v
Start Development
```

---

## 3. Authentication & API Key Configuration

Claude Code supports different authentication methods:

| Authentication | Description |
|---|---|
| Claude subscription | Sign in using an eligible Claude account |
| Anthropic API key | Authenticate using an Anthropic Console API key |
| Company AI gateway | Use organization-provided credentials and gateway configuration |
| Cloud providers | Integrate with supported providers such as AWS Bedrock and Google Vertex AI |

### Configure Anthropic API Key

For a standard Anthropic API key:

```bash
export ANTHROPIC_API_KEY='your-api-key'
```

Verify that the variable is configured without printing the secret:

```bash
if [ -n "$ANTHROPIC_API_KEY" ]; then
  echo "API key configured"
else
  echo "API key missing"
fi
```

### Configure API Key Permanently (macOS Zsh)

Add the following line to `~/.zshrc`:

```bash
export ANTHROPIC_API_KEY='your-api-key'
```

Reload the shell configuration:

```bash
source ~/.zshrc
```

**Security best practices:**
- Never commit API keys to Git.
- Never share API keys in screenshots or chat.
- Never print API keys in terminal logs.
- Use company-approved credentials.
- Follow company security policies.
- Avoid storing company secrets in shell configuration if your organization requires managed secret storage.

> Important: Company gateway keys may require additional configuration such as `ANTHROPIC_BASE_URL`. Confirm the required endpoint and authentication method with DevOps before configuring them.

## 4. Start Claude Code

Navigate to your project directory:

```bash
cd /path/to/your/project
```

Start Claude Code:

```bash
claude
```

Claude Code starts an interactive terminal session and can access the current project directory.

### Start Claude with a prompt

```bash
claude "Explain the architecture of this project"
```

### Continue the previous conversation

```bash
claude --continue
```

### Resume a previous conversation

```bash
claude --resume
```

## 5. Most Used Terminal Commands

| Command | Description |
|---|---|
| `claude` | Start Claude Code |
| `claude --version` | Display installed version |
| `claude update` | Update Claude Code |
| `claude doctor` | Diagnose installation and configuration |
| `claude --help` | Display CLI help |
| `claude "prompt"` | Start with an initial prompt |
| `claude --continue` | Continue the most recent conversation |
| `claude --resume` | Resume a previous conversation |
| `claude -p "prompt"` | Execute a prompt in non-interactive mode |

## 10. Official Documentation

- [Claude Code Documentation](https://code.claude.com/docs)
- [Installation Guide](https://code.claude.com/docs/en/setup)
- [Authentication Guide](https://code.claude.com/docs/en/authentication)
- [CLI Reference](https://code.claude.com/docs/en/cli-reference)
- [Interactive Mode](https://code.claude.com/docs/en/interactive-mode)

## Useful CLI flags

### 1. Print mode

Execute a prompt without starting the interactive interface.

```bash
claude -p "Explain the application architecture"
```

### 2. Continue previous conversation

```bash
claude -c
```

Continue with a new prompt:

```bash
claude -c -p "Now explain the backend API"
```

### 3. Resume a specific session

```bash
claude --resume
```

Resume using a session ID:

```bash
claude --resume SESSION_ID
```

### 4. Select a model

```bash
claude --model sonnet
```

```bash
claude --model opus
```

Available models and aliases depend on account access and the current release.

### 5. Start in Plan Mode

```bash
claude --permission-mode plan
```

Use this when you want Claude to analyze the project and prepare an implementation plan before making changes.

### 6. Verbose output

```bash
claude --verbose
```

Useful for debugging and understanding tool execution.

### 7. Restrict the number of turns

```bash
claude -p --max-turns 5 "Analyze this project"
```

### 8. JSON output

```bash
claude -p "Explain this project" --output-format json
```

Useful when integrating Claude Code output into automation scripts.

### 9. Add additional directories

```bash
claude --add-dir ../shared ../common
```

Allows Claude to access additional working directories.

### 10. Debug mode

```bash
claude --debug
```

Useful for investigating issues with Claude Code execution.

### 11. Skip permission prompts

```bash
claude --dangerously-skip-permissions
```

WARNING: This bypasses permission checks. Avoid using it in normal development, especially with production credentials or sensitive repositories.

## Non-interactive mode example

```bash
claude -p "Review the current git changes and identify potential bugs"
```

Use cases:

- CI/CD automation.
- Automated code review.
- Build verification.
- Script-based workflows.
- Repository analysis.

---

# 5. Slash Commands

Slash commands are special commands available inside the Claude Code interactive session.

Type `/` to explore available commands and skills.

## Common slash commands

| Command | Purpose |
|---|---|
| `/help` | Show help |
| `/clear` | Clear conversation context |
| `/compact` | Compress conversation context |
| `/context` | Show context window usage |
| `/cost` | Usage/cost information where supported |
| `/usage` | Show usage information |
| `/model` | Select AI model |
| `/effort` | Configure reasoning effort |
| `/config` | Configure Claude Code settings |
| `/status` | Show session and configuration status |
| `/doctor` | Diagnose configuration and setup |
| `/memory` | View and manage auto memory |
| `/permissions` | Manage permissions |
| `/mcp` | Manage MCP servers |
| `/agents` | Review agent configuration guidance |
| `/skills` | Inspect available skills where supported |
| `/init` | Generate project instructions |
| `/review` | Review code changes |
| `/diff` | Review current working-tree changes |
| `/copy` | Copy the previous response |
| `/export` | Export conversation |
| `/resume` | Resume a previous session |
| `/rewind` | Restore an earlier conversation or code state |
| `/rename` | Rename current session |
| `/plan` | Enter planning workflow where supported |
| `/tasks` | View running tasks |
| `/compact` | Reduce context usage |
| `/exit` | Exit Claude Code |
| `/quit` | Exit Claude Code |

Note: Command availability and aliases can change between Claude Code versions. Some commands are bundled skills, while others are built-in commands.

## Useful commands in daily development

### Understand project

```text
/init
```

Generate project-level instructions based on the repository.

### Review code

```text
/review
```

Review relevant code changes and identify issues.

### Check context

```text
/context
```

Understand how much context is being used.

### Reduce context

```text
/compact
```

Summarize the conversation and free context space.

You can also provide focus instructions:

```text
/compact Keep the implementation plan, important decisions, and pending tasks.
```

### Check configuration

```text
/status
```

### Diagnose issues

```text
/doctor
```

---

# 6. Keyboard Shortcuts

Keyboard shortcuts improve productivity when working with Claude Code.

Note: Shortcuts can vary depending on terminal emulator, operating system, and Claude Code version.

## General controls

| Shortcut | Description |
|---|---|
| `Ctrl + C` | Interrupt current operation or clear input |
| `Ctrl + D` | Exit Claude Code |
| `Esc` | Stop current response or close dialog |
| `Esc + Esc` | Clear draft or open rewind menu |
| `Ctrl + L` | Redraw terminal screen |
| `Ctrl + O` | Toggle detailed transcript |
| `Ctrl + R` | Search command history |
| `Ctrl + B` | Background running task |
| `Ctrl + T` | Toggle task checklist |
| `Ctrl + S` | Stash or restore prompt |
| `Ctrl + Z` | Suspend process on Unix |
| `Ctrl + G` | Open prompt in external editor |
| `Ctrl + V` | Paste image from clipboard where supported |
| `Shift + Tab` | Cycle permission modes |
| `Option + P` (Mac) | Switch model |
| `Option + O` (Mac) | Toggle fast mode |
| `Option + T` (Mac) | Toggle extended thinking where supported |

## Text editing shortcuts

| Shortcut | Description |
|---|---|
| `Ctrl + A` | Move cursor to beginning of line |
| `Ctrl + E` | Move cursor to end of line |
| `Ctrl + K` | Delete text to end of line |
| `Ctrl + U` | Delete text before cursor to line start |
| `Ctrl + W` | Delete previous whitespace-delimited word |
| `Ctrl + Y` | Paste previously deleted text |
| `Alt + B` | Move cursor backward one word |
| `Alt + F` | Move cursor forward one word |
| `Alt + D` | Delete next word |
| `Ctrl + _` | Undo last input edit |

On macOS, configure the Option key as Meta in your terminal to use certain Alt-based shortcuts.

## Multiline input

Use:

```text
\ + Enter
```

to continue a prompt on another line in supported terminal configurations.

You can also use:

```text
Option + Enter
```

or:

```text
Shift + Enter
```

depending on terminal configuration.

## Most useful shortcuts to remember

1. `Esc` – Stop Claude's current operation.
2. `Ctrl + C` – Interrupt or clear input.
3. `Ctrl + R` – Search command history.
4. `Ctrl + O` – Inspect detailed tool execution.
5. `Ctrl + T` – View task checklist.
6. `Ctrl + B` – Move long-running work to the background.
7. `Shift + Tab` – Change permission mode.
8. `Ctrl + G` – Edit a long prompt externally.

---

# 7. Claude Code Core Concepts

## 7.1 Context Window

A context window is the amount of information an AI model can consider during a conversation.

It can include:

- User prompts.
- Previous messages.
- Project instructions.
- File contents.
- Tool outputs.
- Code changes.
- Documentation.

### Example

Suppose you ask Claude to analyze an Angular project.

Claude may need:

```text
CLAUDE.md
package.json
angular.json
src/app/
Shared Components
Services
Routing
API Integrations
```

All relevant information contributes to context usage.

### Context management tips

- Avoid reading the entire repository unnecessarily.
- Ask Claude to inspect specific files.
- Use `/context` to monitor usage.
- Use `/compact` when the conversation becomes large.
- Start a fresh session for unrelated tasks.
- Move large research tasks into subagents.

## 7.2 Plan Mode

Plan Mode allows Claude to explore and understand the project before implementing changes.

Example:

```bash
claude --permission-mode plan
```

Prompt:

```text
Analyze the existing authentication module.

Identify:
1. Current architecture.
2. Components and services involved.
3. API integration.
4. Potential issues.
5. Recommended improvements.

Do not modify any files.

Prepare a step-by-step implementation plan.
```

### When to use Plan Mode

- Large feature development.
- Legacy code refactoring.
- Architecture changes.
- Database migrations.
- Authentication implementation.
- Complex bug fixes.

## 7.3 Agentic Workflow

An agentic workflow means the model can decide which tools and actions are required to achieve a goal.

Example:

```text
User: Fix the login issue.

Claude:
    |
    v
Analyze Login Component
    |
    v
Inspect Authentication Service
    |
    v
Check API Response
    |
    v
Identify Root Cause
    |
    v
Modify Code
    |
    v
Run Tests
    |
    v
Report Changes
```

Important: Agentic behavior does not mean unlimited autonomy. Tool permissions, instructions, and environment restrictions still apply.

---

# 8. CLAUDE.md – Project Instructions

## What is CLAUDE.md?

`CLAUDE.md` is a Markdown file used to provide persistent project instructions to Claude Code.

It helps Claude understand:

- Project architecture.
- Technology stack.
- Coding standards.
- Folder structure.
- Naming conventions.
- Testing commands.
- Development workflows.
- Important restrictions.

Instead of repeating the same instructions in every conversation, maintain them in CLAUDE.md.

## Example project structure

```text
my-project/
│
├── CLAUDE.md
│
├── .claude/
│   ├── settings.json
│   ├── rules/
│   ├── agents/
│   └── skills/
│
├── src/
│   ├── app/
│   ├── components/
│   ├── services/
│   └── models/
│
├── package.json
└── README.md
```

## Generate CLAUDE.md

Start Claude Code:

```bash
claude
```

Then execute:

```text
/init
```

Claude analyzes the repository and generates project instructions.

You should review the generated file instead of blindly accepting every instruction.

## Sample CLAUDE.md

```markdown
# Project Instructions

## Project Overview

This project is an Angular application built using
Angular, TypeScript, RxJS, and SCSS.

## Technology Stack

- Angular
- TypeScript
- RxJS
- NgRx
- SCSS
- Bootstrap

## Architecture

- Follow modular architecture.
- Use standalone components where appropriate.
- Keep business logic inside services.
- Use reusable shared components.
- Follow existing project conventions.

## Coding Standards

- Use TypeScript strict typing.
- Avoid unnecessary any types.
- Follow Angular best practices.
- Prefer OnPush change detection where appropriate.
- Use Signals when they simplify state management.
- Avoid duplicate code.
- Keep components focused and maintainable.

## API Integration

- Keep API calls inside services.
- Handle loading, success, and error states.
- Use appropriate RxJS operators.
- Avoid nested subscriptions.

## Testing

- Write unit tests for important business logic.
- Run existing tests after modifications.
- Ensure linting and build checks pass.

## Important Rules

- Do not modify unrelated files.
- Do not introduce unnecessary dependencies.
- Preserve existing application behavior.
- Explain important architectural decisions.
```

## Best practices for CLAUDE.md

1. Keep instructions short and clear.
2. Include only important project-wide information.
3. Mention actual project commands.
4. Document architecture and coding standards.
5. Avoid adding every possible development procedure.
6. Move reusable workflows into Skills.
7. Move file-specific instructions into Rules.

## Different CLAUDE.md scopes

| Location | Scope |
|---|---|
| `~/.claude/CLAUDE.md` | Personal instructions across projects |
| `./CLAUDE.md` | Current project |
| `./.claude/CLAUDE.md` | Project-level instructions |
| `./CLAUDE.local.md` | Local project-specific instructions |

---

# 9. Rules

## What are Rules?

Rules are additional instructions that guide Claude's behavior in specific projects or file types.

Rules are useful when you want different coding standards for different parts of a project.

For example:

- Angular component rules.
- TypeScript coding rules.
- API service rules.
- Testing rules.
- Security rules.

## Rules directory

```text
my-project/
│
├── CLAUDE.md
│
└── .claude/
    └── rules/
        ├── angular.md
        ├── typescript.md
        ├── api.md
        ├── testing.md
        └── security.md
```

## Example 1: Angular rules

File:

`.claude/rules/angular.md`

```markdown
---
paths:
  - "src/app/**/*.ts"
---

# Angular Rules

- Prefer standalone components.
- Use typed inputs and outputs.
- Keep components focused.
- Move reusable business logic into services.
- Avoid direct DOM manipulation.
- Use OnPush where appropriate.
- Clean up subscriptions when necessary.
- Follow existing project architecture.
```

## Example 2: TypeScript rules

File:

`.claude/rules/typescript.md`

```markdown
---
paths:
  - "src/**/*.ts"
---

# TypeScript Rules

- Use strict typing.
- Avoid unnecessary any.
- Prefer interfaces or types where appropriate.
- Handle null and undefined explicitly.
- Avoid duplicate logic.
- Use meaningful variable names.
- Keep functions small and focused.
```

## Example 3: API rules

File:

`.claude/rules/api.md`

```markdown
---
paths:
  - "src/app/services/**/*.ts"
---

# API Integration Rules

- Keep API integration inside services.
- Use typed request and response models.
- Handle HTTP errors.
- Avoid nested subscriptions.
- Use appropriate RxJS operators.
- Keep API configuration centralized.
```

## Example 4: Testing rules

File:

`.claude/rules/testing.md`

```markdown
---
paths:
  - "**/*.spec.ts"
---

# Testing Rules

- Follow the existing testing framework.
- Test success and failure scenarios.
- Mock external dependencies.
- Avoid testing implementation details.
- Keep test cases independent.
- Cover important business logic.
```

## How Rules work

```text
Developer Request
       |
       v
Claude Code
       |
       v
Read Project Instructions
       |
       v
Identify Relevant Files
       |
       v
Load Matching Rules
       |
       v
Generate or Modify Code
       |
       v
Follow Applicable Instructions
```

### Important distinction

Rules provide guidance; they are not guaranteed security enforcement.

For actions that must be blocked regardless of model behavior, use permissions and hooks.

---

# 10. Skills

## What are Skills?

Skills are reusable instructions and workflows that extend Claude Code's capabilities.

A skill contains instructions for performing a particular task.

Instead of explaining the same process repeatedly, create a skill once and reuse it.

### Real-world examples

- Code review.
- Angular component generation.
- Unit test generation.
- API documentation.
- Security review.
- Pull request preparation.
- Database migration.
- Technical documentation.

## Skills folder structure

```text
my-project/
│
└── .claude/
    └── skills/
        ├── code-review/
        │   └── SKILL.md
        │
        ├── angular-component/
        │   └── SKILL.md
        │
        ├── unit-test/
        │   └── SKILL.md
        │
        └── api-documentation/
            └── SKILL.md
```

## Create a Skill

Example: Code Review Skill.

Step 1: Create a directory.

```bash
mkdir -p .claude/skills/code-review
```

Step 2: Create a file.

```bash
touch .claude/skills/code-review/SKILL.md
```

Step 3: Add instructions.

File: `.claude/skills/code-review/SKILL.md`

```markdown
---
name: code-review
description: Reviews source code for bugs, security issues,
performance problems, and maintainability. Use when reviewing
code changes or when the user requests a code review.
---

# Code Review Skill

You are a senior software engineer.

Review the provided code using the following criteria:

1. Code correctness.
2. Potential bugs.
3. Security vulnerabilities.
4. Performance issues.
5. Code readability.
6. Maintainability.
7. Error handling.
8. Best practices.

## Review Guidelines

- Focus on actual issues.
- Avoid reporting speculative problems as confirmed bugs.
- Explain why each issue matters.
- Suggest practical fixes.
- Include file and line references when available.

## Output Format

### Summary

### Critical Issues

### High Priority Issues

### Medium Priority Issues

### Low Priority Suggestions

### Recommended Improvements
```

Step 4: Invoke the skill.

```text
/code-review
```

You can also let Claude invoke a skill automatically when its description matches your request.

## Example 2: Angular component generation skill

File:

`.claude/skills/angular-component/SKILL.md`

```markdown
---
name: angular-component
description: Generates reusable Angular components following
existing project architecture and coding standards.
---

# Angular Component Generator

Act as a senior Angular developer.

Before generating a component:

1. Analyze existing component structure.
2. Identify project Angular version.
3. Understand existing naming conventions.
4. Check shared components and services.

## Implementation Guidelines

- Prefer standalone components.
- Use TypeScript strict typing.
- Use reusable inputs and outputs.
- Use SCSS for styling.
- Follow existing change detection strategy.
- Avoid unnecessary dependencies.
- Write unit tests.

## Output

Explain:

- Component structure.
- Files created.
- Important implementation decisions.
- How to use the component.
- Tests executed.
```

## Example 3: Unit test generation skill

File:

`.claude/skills/unit-test/SKILL.md`

```markdown
---
name: unit-test
description: Generates and improves unit tests for application code.
---

# Unit Test Generator

Analyze the selected source code.

Generate meaningful test cases covering:

1. Successful execution.
2. Error scenarios.
3. Edge cases.
4. Input validation.
5. Dependency interactions.
6. Expected output.

Follow the existing testing framework and project conventions.

Do not modify production code unless requested.

Run the relevant tests and report the results.
```

## Skill frontmatter

Frontmatter is the YAML configuration at the beginning of a SKILL.md file.

Example:

```yaml
---
name: code-review
description: Reviews source code for bugs and security issues.
disable-model-invocation: true
user-invocable: true
---
```

Important fields:

| Field | Purpose |
|---|---|
| `name` | Skill name |
| `description` | Explains when the skill should be used |
| `disable-model-invocation` | Prevents automatic model invocation |
| `user-invocable` | Controls user slash-command invocation |
| `argument-hint` | Shows expected arguments |
| `allowed-tools` | Controls tools available to the skill |
| `context` | Can configure execution context, including subagent execution |
| `agent` | Specifies an agent for supported skill execution |

Only use fields supported by the current Claude Code skill specification.

## Skill locations

| Location | Scope |
|---|---|
| `~/.claude/skills/` | Personal skills across projects |
| `.claude/skills/` | Current project |
| Enterprise skill directories | Organization-managed skills |
| Plugin skill directories | Skills provided by plugins |

## Skills vs custom commands

Modern Note:

Custom slash commands and skills have been unified in the current Claude Code architecture.

Existing `.claude/commands/` files continue to work, but Skills are the recommended approach for reusable workflows that need supporting files or more advanced configuration.

## Best practices for Skills

- Create one skill for one specific workflow.
- Use clear descriptions.
- Avoid very broad skill responsibilities.
- Include expected input and output.
- Provide practical examples.
- Keep reusable reference material in supporting files.
- Test skills with real tasks.
- Review results and improve instructions.

---

# 11. Subagents

## What are Subagents?

Subagents are specialized AI assistants that handle specific tasks independently within a Claude Code session.

Each subagent can have:

- Its own system instructions.
- Its own context window.
- Specific tool access.
- Permission restrictions.
- Model configuration.
- Optional persistent memory.

The main Claude agent can delegate suitable tasks to subagents.

### Real-world examples

- Code Review Agent.
- Security Review Agent.
- Testing Agent.
- Documentation Agent.
- Architecture Analysis Agent.
- Debugging Agent.

## Main Agent vs Subagent

```text
                 Main Agent
                     |
          +----------+----------+
          |          |          |
          v          v          v
       Code       Security    Testing
      Reviewer    Reviewer    Agent
          |          |          |
          v          v          v
       Review     Security    Test
       Results    Findings    Results
          |          |          |
          +----------+----------+
                     |
                     v
              Main Agent
                     |
                     v
               Final Report
```

## Built-in subagents

Claude Code includes built-in subagents such as:

| Agent | Purpose |
|---|---|
| Explore | Explore and search the codebase |
| Plan | Analyze requirements and create plans |
| General-purpose | Handle broader development tasks |
| claude-code-guide | Help explain Claude Code features |

Availability and model selection can vary by release and configuration.

## Create a custom subagent

Example: Code Reviewer Agent.

Step 1: Create the directory.

```bash
mkdir -p .claude/agents
```

Step 2: Create the file.

```bash
touch .claude/agents/code-reviewer.md
```

Step 3: Add agent instructions.

File: `.claude/agents/code-reviewer.md`

```markdown
---
name: code-reviewer
description: Reviews code changes for bugs, security vulnerabilities,
performance problems, and maintainability issues.
tools: Read, Grep, Glob
model: sonnet
---

# Code Reviewer Agent

You are a senior software engineer specializing in code reviews.

Your responsibilities:

1. Analyze source code.
2. Identify actual bugs.
3. Identify security vulnerabilities.
4. Detect performance problems.
5. Check coding standards.
6. Identify maintainability issues.

## Rules

- Do not modify source files.
- Do not report speculative issues as confirmed defects.
- Focus on high-impact problems.
- Explain why each finding matters.
- Suggest practical solutions.

## Output

Provide:

- File name.
- Line number when available.
- Issue description.
- Severity.
- Impact.
- Recommended fix.
```

Step 4: Invoke the agent.

```text
Use the code-reviewer agent to review the authentication module.
```

Claude can delegate matching tasks automatically based on the agent description.

## Example 2: Security Agent

File: `.claude/agents/security-reviewer.md`

```markdown
---
name: security-reviewer
description: Performs security reviews of application code.
tools: Read, Grep, Glob
model: sonnet
---

# Security Reviewer

Act as an application security engineer.

Analyze the code for:

- Authentication issues.
- Authorization problems.
- Injection vulnerabilities.
- Sensitive data exposure.
- Insecure API handling.
- Hardcoded secrets.
- Improper input validation.
- Unsafe dependency usage.

Do not modify files.

Report only evidence-based findings.

For every finding include:

- Severity.
- Affected file.
- Vulnerability.
- Potential impact.
- Recommended remediation.
```

## Example 3: Testing Agent

File: `.claude/agents/testing-agent.md`

```markdown
---
name: testing-agent
description: Analyzes application code and identifies missing test coverage.
tools: Read, Grep, Glob, Bash
model: sonnet
---

# Testing Agent

Act as a senior test automation engineer.

Responsibilities:

1. Analyze existing test coverage.
2. Identify missing test cases.
3. Review edge cases.
4. Identify flaky test patterns.
5. Recommend test improvements.

Follow the existing testing framework.

Run only relevant test commands when authorized.

Return a structured test report.
```

## Agent scope

| Location | Scope |
|---|---|
| `~/.claude/agents/` | Personal agents across projects |
| `.claude/agents/` | Project-specific agents |
| Plugin agents | Agents provided by plugins |

## Agent tools

Common tools include:

- Read
- Edit
- Write
- Bash
- Grep
- Glob
- WebSearch
- WebFetch
- Agent

Tool availability depends on the agent configuration and environment.

### Read-only agent

```yaml
---
name: reviewer
description: Reviews code without modifying files.
tools: Read, Grep, Glob
---
```

### Agent with editing capabilities

```yaml
---
name: developer
description: Implements application changes.
tools: Read, Edit, Write, Bash, Grep, Glob
---
```

Principle: Give agents only the tools they actually need.

## Parallel agents

Independent tasks can be delegated to multiple agents.

Example:

```text
Analyze the authentication module using separate agents.

Agent 1: Review code quality.
Agent 2: Review security.
Agent 3: Analyze test coverage.

Return a consolidated report with prioritized findings.
Do not modify any files.
```

Parallel work can reduce completion time for independent tasks, but consumes additional model usage and needs coordination.

---

# 12. Skills vs Agents vs Rules

These concepts are related but solve different problems.

| Feature | Skills | Subagents | Rules |
|---|---|---|---|
| Main purpose | Reusable workflows | Specialized task execution | Persistent coding guidance |
| Primary use | How to perform a task | Who performs a task | What standards to follow |
| Context | Loaded when used | Separate context window | Loaded when applicable |
| Can have tools | Yes, through configuration | Yes | No independent tool execution |
| Can work independently | Can run in a subagent | Yes | No |
| Example | Code review workflow | Security reviewer | Security coding standards |

## Simple real-world example

Suppose you are developing an Angular application.

**Rules**

```text
Always use strict TypeScript.
Prefer standalone components.
Follow existing architecture.
```

**Skill**

```text
When asked to generate an Angular component,
inspect existing patterns and create a reusable component.
```

**Subagent**

```text
Analyze the Angular application for security issues
without modifying any files.
```

### How they work together

```text
                 Developer
                     |
                     v
                Claude Code
                     |
          +----------+----------+
          |          |          |
          v          v          v
        Rules      Skills     Agents
          |          |          |
          v          v          v
       Standards  Workflow   Specialized
                              Execution
          |          |          |
          +----------+----------+
                     |
                     v
              Implementation
                     |
                     v
                Validation
```

---

# 13. Prompt Engineering

## What is Prompt Engineering?

Prompt Engineering is the practice of designing clear instructions so an AI model can understand the task and generate useful results.

A good prompt reduces ambiguity and improves output quality.

## Prompt structure

A practical prompt can include:

1. Role.
2. Context.
3. Objective.
4. Requirements.
5. Constraints.
6. Expected output.
7. Validation criteria.

### General prompt template

```text
Role:
Act as a senior software engineer.

Context:
I am working on an Angular application.

Objective:
Implement a reusable user profile component.

Requirements:
- Follow existing project architecture.
- Use standalone components.
- Use TypeScript strict typing.
- Use SCSS.

Constraints:
- Do not modify unrelated files.
- Avoid unnecessary dependencies.
- Preserve existing functionality.

Expected Output:
- Implementation.
- Files modified.
- Explanation.
- Tests executed.

Validation:
Run relevant tests and verify the build.
```

## Prompting techniques

### 1. Zero-shot prompting

Providing a task without examples.

```text
Explain Angular Signals with practical examples.
```

### 2. Few-shot prompting

Providing examples to guide the expected output.

```text
Follow this output format.

Example:

Issue:
Missing null validation.

Impact:
Application may throw runtime errors.

Fix:
Add appropriate null checks.

Now review the supplied code using the same format.
```

### 3. Role-based prompting

Assigning a specific professional role.

```text
Act as a Senior Angular Architect.

Review my application architecture and suggest improvements.
```

### 4. Context-based prompting

Providing project-specific information.

```text
This is an Angular 21 application using standalone components,
Signals, RxJS, and SCSS.

Follow the existing architecture while implementing the feature.
```

### 5. Constraint-based prompting

Clearly explaining what should and should not happen.

```text
Refactor the service.

Constraints:
- Do not change API contracts.
- Do not modify component templates.
- Do not introduce new dependencies.
- Preserve existing functionality.
```

### 6. Step-by-step prompting

Breaking a complex task into smaller steps.

```text
First analyze the current implementation.

Then identify the issues.

Next propose a solution.

Wait for my approval before modifying files.
```

### 7. Output-format prompting

Specifying exactly how the result should look.

```text
Return the review in this format:

1. Issue
2. Severity
3. File
4. Explanation
5. Recommended fix
```

## Weak prompt vs Strong prompt

### Weak prompt

```text
Improve my code.
```

### Strong prompt

```text
Act as a senior Angular developer.

Analyze the selected component.

Identify:
- Performance issues.
- Unnecessary subscriptions.
- Change detection problems.
- Code duplication.
- Maintainability issues.

Suggest improvements following Angular best practices.

Do not modify the source code yet.

Provide the findings with explanations and examples.
```

---

# 14. Useful Prompts for Developers

## 14.1 Understand an existing project

```text
Act as a senior software architect.

Analyze the entire project structure.

Explain:

1. Application architecture.
2. Technology stack.
3. Folder structure.
4. Main components.
5. Services and API integrations.
6. Routing.
7. State management.
8. Authentication flow.

Identify the important files and explain how they interact.

Do not modify any files.
```

## 14.2 Understand a specific component

```text
Analyze this component.

Explain:

1. Component responsibility.
2. Inputs and outputs.
3. Lifecycle hooks.
4. Services used.
5. API integration.
6. State management.
7. Dependencies.

Explain the execution flow step by step.

Do not modify the code.
```

## 14.3 Generate a new feature

```text
Act as a senior software engineer.

Implement a new feature based on the existing project architecture.

Before implementation:

1. Analyze similar existing features.
2. Identify reusable components and services.
3. Understand the API contracts.
4. Prepare an implementation plan.

After approval:

1. Implement the feature.
2. Follow coding standards.
3. Add appropriate error handling.
4. Write unit tests.
5. Run relevant tests.

Avoid modifying unrelated files.
```

## 14.4 Code review

```text
Act as a senior software engineer and code reviewer.

Review the current code changes.

Check:

1. Bugs and logical issues.
2. Security vulnerabilities.
3. Performance problems.
4. Error handling.
5. Code readability.
6. Maintainability.
7. Best practices.

Report only actionable findings.

For every finding include:

- Severity.
- File and line number.
- Issue.
- Impact.
- Recommended solution.

Do not modify any files.
```

## 14.5 Refactoring

```text
Act as a senior software engineer.

Analyze the selected code and identify refactoring opportunities.

Focus on:

- Code duplication.
- Separation of concerns.
- Maintainability.
- Performance.
- Reusability.
- Readability.

First provide a refactoring plan.

Do not modify the code until I approve the plan.
```

## 14.6 Bug fixing

```text
Act as a senior debugging engineer.

Investigate the reported issue.

Steps:

1. Reproduce or inspect the issue.
2. Analyze relevant files.
3. Trace the execution flow.
4. Identify the root cause.
5. Explain why the issue occurs.
6. Propose the minimum required fix.
7. Implement after approval.
8. Run relevant tests.

Do not apply unrelated changes.
```

## 14.7 Unit test generation

```text
Analyze the selected service/component.

Generate unit tests covering:

1. Successful scenarios.
2. Error scenarios.
3. Edge cases.
4. Invalid inputs.
5. Dependency interactions.

Follow the existing testing framework.

Run the tests and report the results.
```

## 14.8 API integration

```text
Act as a senior full-stack developer.

Integrate the provided REST API into the application.

Requirements:

- Follow existing service architecture.
- Use TypeScript interfaces.
- Handle loading states.
- Handle API errors.
- Handle empty responses.
- Avoid duplicate API calls.
- Follow existing coding conventions.

Explain all files modified.
```

## 14.9 Security review

```text
Act as an application security engineer.

Review the selected code for:

- Authentication issues.
- Authorization issues.
- Injection vulnerabilities.
- Sensitive data exposure.
- Insecure API handling.
- Input validation problems.
- Dependency risks.

Report evidence-based findings with severity and remediation.

Do not modify source files.
```

## 14.10 Documentation generation

```text
Analyze the selected module and generate technical documentation.

Include:

1. Module overview.
2. Architecture.
3. Folder structure.
4. Main components.
5. Services.
6. API integration.
7. Execution flow.
8. Dependencies.
9. Testing approach.

Use clean GitHub README Markdown.
```

## 14.11 Pull request preparation

```text
Analyze the current Git changes.

Prepare:

1. Change summary.
2. Features implemented.
3. Bug fixes.
4. Potential risks.
5. Tests executed.
6. Suggested pull request title.
7. Pull request description.

Do not commit or push changes.
```

## 14.12 Performance optimization

```text
Act as a senior performance engineer.

Analyze the selected module.

Identify:

- Unnecessary rendering.
- Expensive computations.
- Memory leaks.
- Duplicate API calls.
- Unnecessary subscriptions.
- Large bundle dependencies.
- Inefficient data transformations.

Prioritize improvements based on actual impact.

Do not optimize without evidence.
```

---

# 15. Claude Code Workflows

## 15.1 New feature development

```text
Requirement
    |
    v
Analyze Project
    |
    v
Understand Architecture
    |
    v
Prepare Implementation Plan
    |
    v
Developer Approval
    |
    v
Implement Feature
    |
    v
Generate Tests
    |
    v
Run Tests
    |
    v
Review Changes
    |
    v
Complete
```

## 15.2 Bug fixing workflow

```text
Bug Report
    |
    v
Analyze Logs
    |
    v
Inspect Relevant Files
    |
    v
Find Root Cause
    |
    v
Propose Fix
    |
    v
Implement Fix
    |
    v
Run Tests
    |
    v
Validate
```

## 15.3 Code review workflow

```text
Git Changes
    |
    v
Code Reviewer
    |
    v
Analyze Modified Files
    |
    v
Check Code Quality
    |
    v
Check Security
    |
    v
Check Performance
    |
    v
Generate Findings
    |
    v
Developer Reviews Findings
```

## 15.4 Parallel agent workflow

```text
                  Main Agent
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
       Reviewer    Security     Testing
        Agent       Agent       Agent
          |           |           |
          v           v           v
       Findings    Findings    Findings
          |           |           |
          +-----------+-----------+
                      |
                      v
               Consolidated Report
```

Use parallel agents when tasks are independent and can be analyzed separately.

---

# 16. Pro Tips and Best Practices

## 16.1 Start with project analysis

Before asking Claude to implement a feature:

```text
Analyze the project architecture and explain the existing conventions.

Do not modify files.
```

This prevents unnecessary changes based on incorrect assumptions.

## 16.2 Use Plan Mode for complex tasks

For architecture changes and large features, ask Claude to prepare a plan first.

Avoid immediately asking for large implementations.

## 16.3 Give specific prompts

Instead of:

```text
Fix my application.
```

Use:

```text
Investigate the login API failure.

Trace the request from the login component to the authentication service.

Identify the root cause and suggest a minimal fix.
```

## 16.4 Limit file modifications

```text
Modify only the following files:

- user.component.ts
- user.component.html
- user.component.scss

Do not modify other files without asking.
```

## 16.5 Ask Claude to explain before implementing

```text
Explain the proposed changes before modifying any files.
```

## 16.6 Review every code change

Use:

```text
/diff
```

Or ask:

```text
Review all your changes.

Check for:
- Unintended modifications.
- Missing error handling.
- TypeScript errors.
- Security issues.
- Missing tests.
```

## 16.7 Maintain CLAUDE.md

Keep project instructions updated when:

- Architecture changes.
- Coding standards change.
- New dependencies are introduced.
- Repeated corrections are needed.

## 16.8 Use Skills for repeated workflows

If you frequently ask Claude to perform the same process, convert the instructions into a reusable skill.

## 16.9 Use Subagents for specialized work

Delegate tasks such as:

- Independent security analysis.
- Large codebase exploration.
- Test coverage analysis.
- Documentation research.

Avoid creating agents for every small task.

## 16.10 Manage context

Use:

```text
/context
```

When context becomes large:

```text
/compact
```

Start a new session when changing to an unrelated task.

## 16.11 Ask for root cause, not just a fix

Instead of:

```text
Fix this error.
```

Use:

```text
Identify the root cause.

Explain why the error occurs.

Show the minimum required change.

Implement the fix and validate it.
```

## 16.12 Avoid blindly accepting generated code

Always verify:

- Business logic.
- API contracts.
- Security.
- Error handling.
- Test results.
- Performance.
- Architectural consistency.

## 16.13 Use Git checkpoints

Before large changes:

```bash
git status
git diff
git add .
git commit -m "checkpoint before refactoring"
```

Only commit when the changes are understood and appropriate.

## 16.14 Ask Claude to validate its own implementation

```text
After implementation:

1. Run relevant tests.
2. Run linting.
3. Run the production build.
4. Inspect the Git diff.
5. Report any remaining issues.

Do not claim validation passed unless the commands completed successfully.
```

## 16.15 Don't overload CLAUDE.md

Keep project-wide instructions concise.

Use:

- CLAUDE.md for general project context.
- Rules for specific coding standards.
- Skills for reusable procedures.
- Agents for specialized independent tasks.

---

# 17. Security and Permissions

Claude Code can read files, edit source code, and execute terminal commands. Therefore, permissions and security are important.

## Permission modes

Common permission modes include:

| Mode | Purpose |
|---|---|
| `default` | Ask for approval when required |
| `acceptEdits` | Automatically accept supported file edits |
| `plan` | Explore and plan without modifying source files |
| `auto` | Use the supported automatic permission workflow where available |
| `bypassPermissions` | Skip permission checks |

Availability depends on environment and organizational policy.

## Configure permissions

Project settings:

`.claude/settings.json`

Example:

```json
{
  "permissions": {
    "allow": [
      "Bash(npm run lint)",
      "Bash(npm run test)"
    ],
    "deny": [
      "Read(./.env)",
      "Read(./.env.*)"
    ]
  }
}
```

## Settings locations

| File | Purpose |
|---|---|
| `~/.claude/settings.json` | Personal settings |
| `.claude/settings.json` | Shared project settings |
| `.claude/settings.local.json` | Local project settings |
| Managed settings | Organization-managed configuration |

## Security best practices

1. Never expose API keys in prompts.
2. Avoid giving unnecessary file access.
3. Review commands before approval.
4. Protect `.env` files.
5. Do not use bypass permission mode casually.
6. Review generated shell commands.
7. Keep sensitive information out of Git.
8. Use read-only agents for code reviews.
9. Apply least-privilege permissions.
10. Follow company security policies.

## Important distinction

CLAUDE.md and Rules are instructions, not security boundaries.

Use permissions, hooks, and organizational controls when an action must be restricted.

---

# 18. Troubleshooting

## Issue 1: Claude command not found

Check installation:

```bash
claude --version
```

Check PATH:

```bash
which claude
```

Verify your installation and shell configuration.

## Issue 2: Installation problems

Run:

```bash
claude doctor
```

Check the official installation instructions.

Modern Note: Avoid using `sudo npm install -g` as a routine workaround for npm permission issues. Follow the official installation guidance instead.

## Issue 3: Authentication problems

- Verify account authentication.
- Check network connectivity.
- Check organizational proxy restrictions.
- Verify the configured API provider.
- Check account and usage access.

## Issue 4: Context is too large

Run:

```text
/context
```

Then:

```text
/compact
```

For unrelated work, consider starting a fresh session.

## Issue 5: Claude is not following project instructions

Check:

- Is CLAUDE.md in the correct location?
- Are instructions clear?
- Are there conflicting instructions?
- Are rules scoped to the correct files?
- Is the project instruction file too large?

Run:

```text
/doctor
```

## Issue 6: MCP server not working

Run:

```text
/mcp
```

Check:

- Server configuration.
- Authentication.
- Environment variables.
- Server process.
- Tool availability.

## Issue 7: Claude Code becomes unresponsive

Try:

1. Press `Esc` or `Ctrl + C`.
2. Check whether a long-running command is active.
3. Review terminal output.
4. Restart Claude Code if necessary.
5. Resume the previous session.

```bash
claude --continue
```

---

# 19. Interview Questions and Answers

## Q1. What is Claude Code?

Claude Code is an agentic coding tool from Anthropic that works with a developer's codebase through terminal and supported IDE integrations. It can analyze files, modify code, execute commands, run tests, and perform development workflows.

## Q2. What is the difference between Claude Chat and Claude Code?

Claude Chat is primarily a conversational AI interface. Claude Code is designed for development workflows and can interact with project files and execute permitted tools directly.

## Q3. What is CLAUDE.md?

CLAUDE.md is a Markdown instruction file that provides persistent project context and coding guidelines to Claude Code.

## Q4. What are Skills?

Skills are reusable instructions that define how Claude should perform specific tasks. They can be automatically invoked when relevant or explicitly called using slash commands.

## Q5. What are Subagents?

Subagents are specialized AI assistants that execute delegated tasks using their own context windows and configured tool access.

## Q6. What is the difference between Skills and Subagents?

Skills define reusable workflows and instructions. Subagents are specialized workers that execute delegated tasks independently.

## Q7. What are Rules?

Rules provide additional coding instructions, often scoped to particular file types or directories.

## Q8. What is Plan Mode?

Plan Mode allows Claude to explore a codebase and prepare an implementation plan without modifying source files.

## Q9. What is a Context Window?

A context window represents the information available to the model during a session, including prompts, files, tool outputs, and conversation history.

## Q10. What is the purpose of `/compact`?

It summarizes the conversation to reduce context usage while retaining relevant information.

## Q11. What is the purpose of MCP?

MCP stands for Model Context Protocol. It provides a standardized way for AI applications to connect to external tools, resources, and data sources.

## Q12. What are Hooks?

Hooks are configured automation actions that execute in response to specific Claude Code lifecycle events.

Examples include:

- Running formatters after file edits.
- Validating commands before execution.
- Running tests after implementation.
- Logging tool activity.

## Q13. Can Claude Code use multiple agents?

Yes. Claude Code can delegate independent tasks to multiple subagents. Each agent works within its own context and returns results to the coordinating conversation.

## Q14. How do you improve Claude Code output quality?

- Provide clear prompts.
- Include project context.
- Maintain CLAUDE.md.
- Use relevant Rules.
- Create reusable Skills.
- Delegate specialized tasks.
- Review changes.
- Run tests and validation.

## Q15. How do you safely use Claude Code in enterprise projects?

Use least-privilege permissions, protect secrets, review generated changes, follow organizational policies, use appropriate sandboxing, and validate all generated code.

---

# 20. Official References

Always refer to official documentation for the latest commands, supported features, and configuration options.

| Topic | Official Documentation |
|---|---|
| Claude Code Overview | https://code.claude.com/docs/en/overview |
| Getting Started | https://code.claude.com/docs/en/quickstart |
| Installation | https://code.claude.com/docs/en/setup |
| CLI Reference | https://code.claude.com/docs/en/cli-reference |
| Interactive Mode | https://code.claude.com/docs/en/interactive-mode |
| Slash Commands | https://code.claude.com/docs/en/commands |
| Memory and CLAUDE.md | https://code.claude.com/docs/en/memory |
| Skills | https://code.claude.com/docs/en/skills |
| Subagents | https://code.claude.com/docs/en/sub-agents |
| Settings | https://code.claude.com/docs/en/settings |
| Permissions | https://code.claude.com/docs/en/permissions |
| Hooks | https://code.claude.com/docs/en/hooks |
| MCP | https://code.claude.com/docs/en/mcp |
| Common Workflows | https://code.claude.com/docs/en/common-workflows |
| Best Practices | https://code.claude.com/docs/en/best-practices |
| Troubleshooting | https://code.claude.com/docs/en/troubleshooting |

---

# Final Takeaways

| Concept | Remember |
|---|---|
| Claude Code | AI-powered agentic coding tool |
| Terminal Commands | Launch and control Claude Code |
| Slash Commands | Perform actions within interactive sessions |
| Keyboard Shortcuts | Improve productivity |
| Context Window | Information available to the model |
| CLAUDE.md | Persistent project instructions |
| Rules | Coding standards and scoped instructions |
| Skills | Reusable workflows |
| Subagents | Specialized task execution |
| Prompt Engineering | Clear and structured instructions |
| MCP | Connect external tools and data |
| Hooks | Automate lifecycle actions |
| Permissions | Control access and execution |

## Recommended Learning Path

1. Understand Claude Code fundamentals.
2. Practice terminal and slash commands.
3. Learn context management.
4. Create and maintain CLAUDE.md.
5. Configure project Rules.
6. Create custom Skills.
7. Build specialized Subagents.
8. Understand MCP integration.
9. Explore Hooks and permissions.
10. Build practical AI-powered development workflows.

**Learn → Experiment → Build → Review → Improve**

---

*Notes are intended as a practical learning reference. Features, commands, keyboard shortcuts, and configuration options may change between Claude Code releases. Verify version-specific behavior against the official documentation.*
