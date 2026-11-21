# Building AI Agents Using Claude Code – Generic Development Guide

A reusable guide for planning, designing, developing, testing, and deploying AI agents using Claude Code and modern AI technologies.

---

# Table of Contents

1. [Introduction to AI Agents](#1-introduction-to-ai-agents)
2. [Understanding AI Agent Architecture](#2-understanding-ai-agent-architecture)
3. [Technology Stack](#3-technology-stack)
4. [Step 1: Define the Agent Idea and Requirements](#4-step-1-define-the-agent-idea-and-requirements)
5. [Step 2: Create the PRD.md File](#5-step-2-create-the-prdmd-file)
6. [Step 3: Prepare Project Context and CLAUDE.md](#6-step-3-prepare-project-context-and-claudemd)
7. [Step 4: Design the Agent Architecture](#7-step-4-design-the-agent-architecture)
8. [Step 5: Select the LLM Provider](#8-step-5-select-the-llm-provider)
9. [Step 6: Identify Tools and Integrations](#9-step-6-identify-tools-and-integrations)
10. [Step 7: Implement Agent Instructions Using Skills](#10-step-7-implement-agent-instructions-using-skills)
11. [Step 8: Configure Hooks and Guardrails](#11-step-8-configure-hooks-and-guardrails)
12. [Step 9: Implement Agent Logic](#12-step-9-implement-agent-logic)
13. [Step 10: Add Memory and Context Management](#13-step-10-add-memory-and-context-management)
14. [Step 11: Implement Error Handling and Validation](#14-step-11-implement-error-handling-and-validation)
15. [Step 12: Test and Evaluate the Agent](#15-step-12-test-and-evaluate-the-agent)
16. [Step 13: Build the User Interface](#16-step-13-build-the-user-interface)
17. [Step 14: Deploy the Agent](#17-step-14-deploy-the-agent)
18. [Step 15: Monitoring and Maintenance](#18-step-15-monitoring-and-maintenance)
19. [Claude Code Important Concepts](#19-claude-code-important-concepts)
20. [Generic Project Structure](#20-generic-project-structure)
21. [Best Practices](#21-best-practices)
22. [Reusable Claude Code Prompts](#22-reusable-claude-code-prompts)
23. [Final Development Checklist](#23-final-development-checklist)
24. [Interview Questions](#24-interview-questions)

---

# 1. Introduction to AI Agents

## What is an AI Agent?

An AI Agent is a software system that uses an AI model, instructions, tools, and context to perform tasks toward a specific objective.

Unlike traditional applications that follow only predefined rules, an AI agent can interpret information, decide which actions are appropriate, use available tools, and produce results.

### Simple Example

Consider an AI Research Agent.

A user asks:

"Research the latest trends in Angular and prepare a technical report."

The agent can:

1. Understand the user's request.
2. Identify the required research topics.
3. Search relevant information.
4. Read and analyze the results.
5. Summarize important findings.
6. Generate a technical report.
7. Return the final output.

### AI Agent vs Traditional Automation

| Traditional Automation | AI Agent |
|---|---|
| Follows predefined instructions | Interprets context and instructions |
| Mostly rule-based | Uses an AI model for reasoning |
| Usually follows a fixed workflow | Can select among permitted actions |
| Works well with predictable inputs | Can handle unstructured inputs |
| Limited contextual understanding | Can use context to make decisions |

**Important:** Not every AI-powered application is an agent. A simple LLM API call that generates text is an AI-powered feature. An agent typically has a defined objective, access to tools, and some ability to decide and execute actions.

---

# 2. Understanding AI Agent Architecture

## Basic AI Agent Architecture

An AI agent generally consists of these components:

1. User Input
2. Agent Instructions
3. LLM
4. Tools
5. Context and Memory
6. Agent Orchestration
7. Output

### Architecture Diagram

```text
              USER
                |
                v
          User Interface
                |
                v
           Agent Backend
                |
                v
        Agent Orchestrator
                |
       +--------+--------+
       |        |        |
       v        v        v
   Instructions Context  Tools
       |        |        |
       +--------+--------+
                |
                v
           LLM Provider
                |
                v
         Model Response
                |
                v
       Tool Execution (if needed)
                |
                v
        Result Validation
                |
                v
          Final Response
                |
                v
               USER
```

### Component Explanation

| Component | Responsibility |
|---|---|
| User Interface | Accepts user requests and displays results |
| Backend | Handles application logic and API requests |
| Agent Orchestrator | Controls the execution workflow |
| Instructions | Define the agent's role and behavior |
| LLM | Understands requests and generates responses |
| Tools | Allow the agent to interact with external systems |
| Context | Provides relevant information to the agent |
| Memory | Stores useful information across interactions when required |
| Validation | Checks outputs and tool results |
| Output | Returns the final result to the user |

---

# 3. Technology Stack

The technology stack depends on the type of agent being developed.

| Category | Example Technologies | Purpose |
|---|---|---|
| AI Development | Claude Code | AI-assisted application development |
| LLM | Claude, OpenAI, Gemini | Language model |
| LLM Gateway | OpenRouter | Access supported models through a unified API |
| Frontend | React, Angular | User interface |
| Backend | Node.js, Express, Python | Application logic |
| Database | MongoDB, PostgreSQL | Store application data |
| Vector Database | Pinecone, Chroma, pgvector | Store and retrieve vector embeddings |
| API Integration | REST APIs, GraphQL | Connect external services |
| Browser Automation | Playwright | Automate browser interactions |
| Agent Tools | MCP | Connect models and applications to external tools |
| Scheduling | Cron, Modal | Execute scheduled tasks |
| Deployment | Azure, AWS, Modal, Docker | Host applications |
| Monitoring | Langfuse, LangSmith | Observe and evaluate AI workflows |

**Note:** You do not need every technology for every agent. Select technologies based on actual requirements.

---

# 4. Step 1: Define the Agent Idea and Requirements

Before starting development, clearly define what the agent should accomplish.

### Questions to Answer

1. What problem are we solving?
2. Who will use the agent?
3. What is the main objective?
4. What inputs will the agent receive?
5. What outputs should it generate?
6. What tools or external systems are required?
7. Does it need memory?
8. Does it need autonomous execution?
9. What actions require user approval?
10. How will we measure success?

### Example

| Requirement | Example |
|---|---|
| Agent Name | AI Research Agent |
| Problem | Manual research takes time |
| Objective | Automate technical research |
| Input | Research topic |
| Processing | Search, analyze, summarize |
| Tools | Search API, document reader |
| Output | Technical report |
| Memory | Optional research history |
| User Approval | Required before publishing |
| Execution | Manual initially |

### Define the Scope

Separate requirements into three categories.

**Must Have**
- Core functionality.
- Required integrations.
- Basic validation.
- Error handling.

**Should Have**
- Memory.
- Advanced reporting.
- Background processing.

**Could Have**
- Multi-agent architecture.
- Advanced analytics.
- Additional integrations.

Start with a small, working version rather than implementing every advanced feature immediately.

---

# 5. Step 2: Create the PRD.md File

## What is PRD.md?

PRD stands for Product Requirements Document.

It defines the product requirements, functionality, architecture expectations, and acceptance criteria.

### Recommended PRD Structure

```text
PRD.md
│
├── Project Overview
├── Problem Statement
├── Project Objectives
├── Target Users
├── Functional Requirements
├── Non-Functional Requirements
├── Input and Output Specifications
├── Agent Capabilities
├── LLM Requirements
├── Tools and Integrations
├── Memory Requirements
├── Security Requirements
├── Error Handling
├── Testing Strategy
├── Deployment Requirements
├── Out of Scope
└── Acceptance Criteria
```

### Why is PRD Important?

- Defines the application scope.
- Avoids unclear requirements.
- Helps Claude Code understand the project.
- Provides implementation guidance.
- Reduces unnecessary code generation.
- Establishes measurable completion criteria.

### Claude Code Prompt

```text
I want to build a new AI Agent.

Before writing any code, help me define the product requirements.

First, understand the problem statement and ask me questions about:

1. Agent objective.
2. Target users.
3. Input and output requirements.
4. Core features.
5. Required tools and integrations.
6. LLM provider.
7. Memory requirements.
8. Security and approval requirements.
9. Execution workflow.
10. Deployment requirements.

After gathering the requirements:

- Propose the application scope.
- Identify missing requirements.
- Suggest a suitable technology stack.
- Prepare the PRD.md structure.
- Define functional and non-functional requirements.
- Add acceptance criteria.

Do not start implementation until we review and agree on the PRD.
```

---

# 6. Step 3: Prepare Project Context and CLAUDE.md

## What is Claude Code?

Claude Code is an agentic coding tool that helps developers understand, create, modify, and troubleshoot software projects using natural-language instructions.

It can work with project files, execute permitted commands, and use configured tools.

## What is CLAUDE.md?

`CLAUDE.md` is a project-level instruction file that provides Claude Code with persistent project context.

It helps Claude Code understand:

- Project purpose.
- Architecture.
- Technology stack.
- Coding standards.
- Development guidelines.
- Important project-specific rules.

### Initialize Claude Code

Open the project directory:

```bash
mkdir my-ai-agent
cd my-ai-agent

claude
```

Run:

```text
/init
```

Claude Code can analyze the project and create an initial `CLAUDE.md` file.

### Recommended CLAUDE.md Structure

```markdown
# Project Instructions

## Project Overview

Describe the purpose of the AI Agent.

## Technology Stack

Mention the frontend, backend, LLM provider, database, and integrations.

## Architecture

Explain the main application components.

## Coding Standards

- Follow modular architecture.
- Use meaningful naming conventions.
- Write reusable functions.
- Handle errors properly.
- Avoid unnecessary dependencies.

## Security Guidelines

- Never hardcode API keys.
- Use environment variables.
- Validate external inputs.
- Protect user data.

## AI Development Guidelines

- Keep prompts and instructions organized.
- Validate model responses.
- Avoid trusting unverified model output.
- Apply approval controls for sensitive actions.

## Testing

Mention unit, integration, and end-to-end testing requirements.
```

### Important

`CLAUDE.md` is not the application runtime configuration. It provides context to Claude Code while developing the project.

---

# 7. Step 4: Design the Agent Architecture

Before implementation, decide how the agent will work internally.

### Important Architecture Decisions

- Single-agent or multi-agent architecture?
- Which LLM will be used?
- Which tools will the agent access?
- Does it need memory?
- Does it need a database?
- Does it need a frontend?
- Will execution be manual or automated?
- Which actions require approval?

### Single-Agent Architecture

A single agent handles the complete workflow.

Example:

```text
User
  |
  v
AI Agent
  |
  +---- LLM
  |
  +---- Search Tool
  |
  +---- Database Tool
  |
  +---- External API
  |
  v
Final Result
```

Suitable for:

- Research agents.
- Document-processing agents.
- Simple customer-support agents.
- Personal productivity agents.

### Multi-Agent Architecture

Multiple specialized agents work together.

Example:

```text
                User
                  |
                  v
             Main Agent
                  |
        +---------+---------+
        |         |         |
        v         v         v
    Research   Analysis   Reporting
      Agent      Agent      Agent
        |         |         |
        +---------+---------+
                  |
                  v
             Final Output
```

Suitable for:

- Complex research workflows.
- Multi-stage business processes.
- Specialized analysis systems.

**Best practice:** Start with a single-agent architecture. Introduce multiple agents only when independent responsibilities or coordination requirements justify the additional complexity.

---

# 8. Step 5: Select the LLM Provider

## What is an LLM?

LLM stands for Large Language Model.

It is an AI model trained to understand and generate human language and other supported content.

The LLM acts as the reasoning and language-generation component of an AI agent.

### Common LLM Providers

| Provider | Example |
|---|---|
| Anthropic | Claude models |
| OpenAI | GPT models |
| Google | Gemini models |
| OpenRouter | Unified API for supported models |

### Selection Criteria

Consider:

- Model quality.
- Reasoning capabilities.
- Context window.
- Tool-calling support.
- Response latency.
- API pricing.
- Rate limits.
- Data privacy.
- Provider availability.

### Example Environment Variables

```env
LLM_PROVIDER=your_provider
LLM_API_KEY=your_api_key
LLM_MODEL=your_model
LLM_BASE_URL=your_api_endpoint
```

The exact configuration depends on the selected provider.

### Claude Code Prompt

```text
Now we need to integrate an LLM into our AI Agent.

Please evaluate the requirements in PRD.md and recommend a suitable LLM provider.

Consider:

- Model quality.
- Tool-calling capabilities.
- API pricing.
- Context window.
- Response time.
- Integration complexity.

Explain the integration architecture before implementation.

Use environment variables for API configuration.

Never hardcode or expose API credentials.
```

### Important Architecture Distinction

Claude Code and the LLM used by the application are not necessarily the same thing.

| Claude Code | Runtime LLM |
|---|---|
| Helps develop the application | Powers the application |
| Reads and modifies project files | Processes application requests |
| Helps implement agent logic | Generates responses and tool decisions |
| Used during development | Used whenever the application invokes it |

You can use Claude Code to develop an agent that uses another provider's LLM at runtime.

---

# 9. Step 6: Identify Tools and Integrations

## What are Agent Tools?

Tools are functions or external services that allow an AI agent to perform actions beyond generating text.

Examples:

- Search the web.
- Read files.
- Query a database.
- Call external APIs.
- Send emails.
- Create documents.
- Execute approved commands.
- Interact with browser applications.

### Example

A Research Agent might use:

| Tool | Purpose |
|---|---|
| Web Search | Find relevant information |
| URL Reader | Read web pages |
| Document Reader | Extract information from documents |
| Database | Store research history |
| Report Generator | Generate final reports |

### Tool Execution Flow

```text
User Request
     |
     v
Agent + LLM
     |
     v
Determine Required Tool
     |
     v
Tool Call
     |
     v
External Tool Execution
     |
     v
Tool Result
     |
     v
LLM Processes Result
     |
     v
Final Response
```

### Tool Design Best Practices

- Give each tool one clear responsibility.
- Use meaningful function names.
- Validate input parameters.
- Return predictable structured outputs.
- Handle tool failures.
- Apply authorization checks.
- Avoid unnecessary tool access.

---

# 10. Step 7: Implement Agent Instructions Using Skills

## What are Claude Code Skills?

Skills are reusable instruction sets that help Claude Code perform specialized tasks.

They can contain detailed instructions, workflows, and supporting resources.

### Example Use Cases

- Code review.
- Resume generation.
- Document analysis.
- Test case generation.
- API documentation.
- Research and reporting.

### Recommended Directory

```text
.claude/
└── skills/
    ├── research/
    │   └── SKILL.md
    │
    ├── code-review/
    │   └── SKILL.md
    │
    └── report-generation/
        └── SKILL.md
```

### Example SKILL.md

```markdown
# Research Skill

## Objective

Perform structured research on a given topic.

## Input

- Research topic.
- Optional context.
- Desired output format.

## Instructions

1. Understand the research objective.
2. Identify relevant information sources.
3. Collect information.
4. Compare findings.
5. Identify important insights.
6. Verify important claims.
7. Prepare a structured report.

## Output

- Introduction.
- Key Findings.
- Analysis.
- Recommendations.
- References.

## Rules

- Do not invent information.
- Distinguish facts from assumptions.
- Mention uncertainty.
- Use reliable sources.
```

### Important

Claude Code Skills are instructions for Claude Code. They do not automatically become runtime skills for a separately deployed application.

If your application needs reusable runtime instructions, implement them in the application's own prompt or agent configuration.

---

# 11. Step 8: Configure Hooks and Guardrails

## What are Claude Code Hooks?

Hooks are automation mechanisms that execute configured commands in response to specific Claude Code lifecycle events.

### Example Use Cases

- Run formatting after file changes.
- Execute tests after modifications.
- Validate files before committing.
- Check code quality.
- Prevent certain unsafe operations.

### Example Hook Workflow

```text
Claude Code Action
        |
        v
Configured Hook Event
        |
        v
Execute Validation Script
        |
        v
Check Result
        |
   +----+----+
   |         |
   v         v
Success    Failure
   |         |
   v         v
Continue   Report Error
```

### Guardrails

Guardrails are restrictions and validation rules that help keep the agent's behavior safe and reliable.

Examples:

- Validate user input.
- Restrict access to sensitive operations.
- Require approval before sending emails.
- Prevent unauthorized file deletion.
- Validate generated SQL.
- Avoid exposing confidential information.

### Important

Do not confuse Claude Code Hooks with runtime application guardrails.

For a deployed agent, implement security and validation directly in the application backend. Claude Code Hooks only operate within their configured Claude Code environment.

---

# 12. Step 9: Implement Agent Logic

This is where the actual application functionality is developed.

### Recommended Development Order

1. Project setup.
2. Configuration management.
3. LLM integration.
4. Prompt and instruction design.
5. Tool implementation.
6. Agent orchestration.
7. Input validation.
8. Output validation.
9. Error handling.
10. API endpoints.
11. Frontend integration, if required.

### Example Agent Logic

A simplified conceptual example:

```text
function executeAgent(userRequest):

    validate(userRequest)

    context = loadContext(userRequest)

    response = callLLM(
        userRequest,
        context,
        availableTools
    )

    if response.requiresTool:

        toolResult = executeTool(
            response.toolName,
            response.toolArguments
        )

        validateToolResult(toolResult)

        finalResponse = callLLM(
            userRequest,
            toolResult
        )

        return finalResponse

    return response
```

This is conceptual pseudocode, not a complete production implementation.

### Agent Execution Responsibilities

The application should manage:

- User requests.
- LLM requests.
- Tool selection.
- Tool execution.
- Tool results.
- Context updates.
- Final response generation.
- Execution limits.
- Error handling.

### Claude Code Prompt

```text
We have finalized the PRD and architecture.

Now implement the AI Agent incrementally.

Follow these guidelines:

1. Implement one feature at a time.
2. Explain the purpose of each component.
3. Follow modular architecture.
4. Keep LLM integration separate from business logic.
5. Keep tools independently testable.
6. Validate inputs and outputs.
7. Add proper error handling.
8. Write tests for important functionality.
9. Update README.md when necessary.

Before creating or modifying files, explain the implementation plan.

Do not implement unrelated features.
```

---

# 13. Step 10: Add Memory and Context Management

## What is Agent Memory?

Memory allows an agent to retain or retrieve useful information across interactions.

It helps the agent maintain continuity and avoid repeatedly asking for the same information.

### Different Types of Memory

| Type | Description | Example |
|---|---|---|
| Conversation Context | Information available in the current interaction | Previous messages |
| Short-Term Memory | Temporary information during a task | Current workflow state |
| Long-Term Memory | Information retained across sessions | User preferences |
| External Memory | Information stored in databases or files | User profile |
| Vector Memory | Information retrieved through embeddings | Relevant document chunks |

### Context vs Memory

Context is information supplied to the model for a particular request.

Memory is information retained or retrieved for use in future requests.

### Example

```text
User Request
     |
     v
Load Relevant Memory
     |
     v
Combine with Current Context
     |
     v
Send to LLM
     |
     v
Generate Response
     |
     v
Update Memory (if required)
```

### When Do We Need Memory?

Memory is useful when the agent needs to:

- Remember user preferences.
- Continue long-running workflows.
- Retrieve previous task results.
- Maintain conversation continuity.
- Store application-specific information.

Not every agent requires memory. Avoid adding a vector database simply because the application uses AI.

---

# 14. Step 11: Implement Error Handling and Validation

AI agents interact with external services and produce probabilistic outputs. Therefore, error handling and validation are essential.

### Common Failure Scenarios

| Failure | Handling |
|---|---|
| LLM API unavailable | Retry with backoff |
| Invalid API key | Return authentication error |
| Rate limit exceeded | Apply retry policy |
| Invalid model response | Validate and retry where appropriate |
| Tool execution failed | Return structured tool error |
| Database unavailable | Log and handle safely |
| Invalid user input | Reject with clear message |
| Timeout | Apply execution timeout |
| Unexpected output | Validate against schema |

### Input Validation

Validate user input before sending it to the LLM or executing tools.

### Output Validation

Do not assume that every LLM response is correct.

Validate:

- Required fields.
- Data types.
- JSON structure.
- Business rules.
- Allowed values.
- External references.

### Structured Output Example

```json
{
  "status": "success",
  "agent": "research-agent",
  "result": {
    "summary": "Research completed",
    "findings": [
      "Finding one",
      "Finding two"
    ]
  }
}
```

This is an illustrative response format.

---

# 15. Step 12: Test and Evaluate the Agent

## Why is Agent Testing Important?

Traditional software testing checks whether the application behaves as expected.

AI agent testing must also evaluate response quality, reasoning outcomes, tool selection, and reliability.

### Types of Testing

| Testing Type | Purpose |
|---|---|
| Unit Testing | Test individual functions |
| Integration Testing | Test API and tool integrations |
| End-to-End Testing | Test complete workflows |
| Prompt Testing | Check prompt behavior |
| Output Evaluation | Evaluate generated responses |
| Tool Testing | Check tool selection and execution |
| Security Testing | Identify unsafe behavior |
| Performance Testing | Measure latency and resource usage |

### Example Test Scenarios

For a Research Agent:

1. Provide a valid research topic.
2. Provide an empty request.
3. Provide an ambiguous request.
4. Simulate an unavailable search API.
5. Simulate an invalid LLM response.
6. Test a large research request.
7. Verify source references.
8. Verify the generated report.

### Evaluation Criteria

- Accuracy.
- Relevance.
- Completeness.
- Reliability.
- Tool-selection correctness.
- Response time.
- Cost per execution.
- Safety and policy compliance.

### Regression Testing

Maintain a collection of representative test cases.

Whenever prompts, models, tools, or agent logic change, run the same test cases again to identify regressions.

---

# 16. Step 13: Build the User Interface

A user interface is optional. Some agents can operate through a CLI, API, scheduled job, or messaging interface.

If a UI is required, choose a suitable frontend framework.

### Common Options

- React.
- Angular.
- Next.js.
- Simple web interface.

### Example Architecture

```text
              User
                |
                v
          React / Angular
                |
                v
           Backend API
                |
                v
          Agent Service
                |
                v
             LLM API
                |
                v
          Tool Execution
                |
                v
           Agent Result
                |
                v
          Frontend Display
```

### UI Features

Depending on the agent's purpose:

- User input.
- Conversation history.
- Loading status.
- Tool execution status.
- Result display.
- Error messages.
- Approval controls.
- Download or export functionality.

### Best Practices

- Keep UI logic separate from agent logic.
- Do not expose LLM API keys in the browser.
- Call the backend for protected operations.
- Display execution status clearly.
- Handle long-running tasks appropriately.

---

# 17. Step 14: Deploy the Agent

After local development and testing, prepare the application for deployment.

### Deployment Options

| Platform | Typical Use |
|---|---|
| Azure | Enterprise applications |
| AWS | Cloud applications and services |
| Modal | Python workloads and scheduled jobs |
| Docker | Containerized applications |
| Vercel | Frontend and supported backend workloads |

### Deployment Steps

1. Review application architecture.
2. Prepare production configuration.
3. Configure environment variables.
4. Secure API credentials.
5. Configure database connectivity.
6. Configure file or object storage.
7. Build and test deployment artifacts.
8. Deploy the application.
9. Verify health checks.
10. Test integrations.
11. Configure monitoring.
12. Verify recovery and rollback procedures.

### Environment Configuration

Example `.env`:

```env
APP_ENV=development

LLM_API_KEY=your_api_key
LLM_MODEL=your_model

DATABASE_URL=your_database_url

EXTERNAL_API_KEY=your_external_api_key
```

Use `.env.example` to document required variables without exposing real secrets.

### Scheduled Execution

If the agent needs to run automatically:

- Configure a scheduler.
- Define execution intervals.
- Set the timezone.
- Prevent overlapping executions where necessary.
- Handle retries.
- Store execution results.
- Send notifications for failures.

---

# 18. Step 15: Monitoring and Maintenance

Deploying an agent is not the end of development.

AI agents require continuous monitoring because model behavior, external APIs, data, and costs can change.

### What Should We Monitor?

| Metric | Purpose |
|---|---|
| Total Executions | Number of agent runs |
| Successful Executions | Completed workflows |
| Failed Executions | Failed workflows |
| LLM Latency | Model response time |
| Tool Latency | External tool execution time |
| Token Usage | LLM consumption |
| API Cost | Operating cost |
| Output Quality | Response accuracy and relevance |
| Error Rate | System reliability |

### Monitoring Tools

- Langfuse.
- LangSmith.
- Application logs.
- Cloud platform monitoring.
- Error tracking systems.

### Continuous Improvement

1. Review failed executions.
2. Analyze incorrect outputs.
3. Improve instructions and prompts.
4. Improve tool descriptions.
5. Optimize context usage.
6. Evaluate model alternatives.
7. Reduce unnecessary LLM calls.
8. Add regression tests.
9. Review security and permissions.

---

# 19. Claude Code Important Concepts

The following concepts are useful when developing AI applications using Claude Code.

| Concept | Definition | Purpose |
|---|---|---|
| Claude Code | Agentic coding tool | Develop and maintain applications |
| CLAUDE.md | Project instruction file | Provide persistent project context |
| Skills | Reusable instruction sets | Perform specialized tasks |
| Hooks | Event-triggered automation | Execute configured commands |
| Subagents | Specialized agents used by Claude Code | Delegate focused development tasks |
| MCP | Model Context Protocol | Connect AI applications to external tools and data |
| Rules | Project-specific coding guidance | Maintain consistent development practices |
| Slash Commands | Claude Code commands | Trigger supported workflows |
| Context Window | Model's available context capacity | Process instructions and information |
| Tool Use | Model-directed tool invocation | Interact with external capabilities |

## 19.1 CLAUDE.md

Provides project context and development instructions.

## 19.2 Skills

Reusable instructions for specialized tasks.

## 19.3 Hooks

Execute configured commands in response to lifecycle events.

## 19.4 Subagents

Specialized Claude Code agents that can handle focused tasks.

Example:

- Frontend implementation agent.
- Backend implementation agent.
- Code review agent.
- Testing agent.

## 19.5 MCP – Model Context Protocol

MCP is an open protocol that allows AI applications to connect to external tools and data sources through standardized interactions.

Example integrations:

- GitHub.
- Databases.
- File systems.
- Browser tools.
- Internal enterprise systems.

### MCP Architecture

```text
          AI Application
                |
                v
           MCP Client
                |
                v
           MCP Server
                |
                v
       External Tool / Data
                |
                v
           Tool Result
                |
                v
          AI Application
```

**Important:** MCP is an integration protocol, not an LLM or an agent by itself.

## 19.6 Subagents vs Multi-Agent Application Architecture

These are related but different concepts.

| Claude Code Subagents | Multi-Agent Application |
|---|---|
| Help Claude Code during development | Form part of the deployed application |
| Delegate coding and analysis tasks | Delegate runtime business tasks |
| Use Claude Code's environment | Use the application's own orchestration |
| Support development workflows | Support application workflows |

---

# 20. Generic Project Structure

An example project structure for an AI Agent:

```text
my-ai-agent/
│
├── CLAUDE.md
├── PRD.md
├── README.md
├── package.json
├── .env.example
├── .gitignore
│
├── frontend/
│   ├── src/
│   ├── components/
│   └── services/
│
├── backend/
│   ├── src/
│   │   ├── agents/
│   │   │   ├── agent.service.ts
│   │   │   └── agent.config.ts
│   │   │
│   │   ├── llm/
│   │   │   └── llm.service.ts
│   │   │
│   │   ├── tools/
│   │   │   └── example.tool.ts
│   │   │
│   │   ├── memory/
│   │   │   └── memory.service.ts
│   │   │
│   │   ├── validation/
│   │   │   └── output.validator.ts
│   │   │
│   │   ├── controllers/
│   │   ├── routes/
│   │   └── config/
│   │
│   └── tests/
│
├── .claude/
│   ├── skills/
│   │   └── example-skill/
│   │       └── SKILL.md
│   │
│   ├── agents/
│   └── rules/
│
├── scripts/
│
├── docs/
│
└── output/
```

This is an illustrative structure, not a mandatory architecture. Adjust it based on the selected language, framework, and application complexity.

---

# 21. Best Practices

## 21.1 Start with a Clear Problem Statement

Do not start by choosing an LLM or framework.

First understand the problem and define the desired outcome.

## 21.2 Start Small

Build a minimum viable agent first.

Avoid introducing:

- Multiple agents unnecessarily.
- Complex memory systems.
- Vector databases without a retrieval requirement.
- Too many external integrations.
- Unnecessary orchestration frameworks.

## 21.3 Keep Business Logic Separate

Separate:

- LLM integration.
- Agent instructions.
- Tool execution.
- Business logic.
- Data access.
- Validation.
- User interface.

## 21.4 Use Structured Outputs

Prefer JSON schemas or other structured formats when the application needs predictable responses.

## 21.5 Never Trust LLM Output Blindly

Validate generated content before using it in critical operations.

## 21.6 Apply Human Approval

Require approval before actions such as:

- Sending emails.
- Publishing content.
- Making payments.
- Deleting data.
- Updating important records.
- Submitting external forms.

## 21.7 Apply Least-Privilege Tool Access

Give the agent only the tools and permissions required for its task.

## 21.8 Protect Sensitive Information

- Keep credentials secure.
- Avoid logging secrets.
- Limit access to personal data.
- Validate external inputs.
- Apply appropriate retention policies.

## 21.9 Control Cost and Latency

- Select an appropriate model.
- Avoid unnecessary LLM calls.
- Limit context size.
- Use caching where appropriate.
- Monitor token consumption.
- Set timeouts and execution limits.

## 21.10 Build for Observability

Record:

- Agent execution ID.
- Input metadata.
- Selected tools.
- Tool execution status.
- Model usage.
- Errors.
- Final execution status.

Avoid storing sensitive content unnecessarily.

---

# 22. Reusable Claude Code Prompts

These prompts can be reused for different AI agent projects.

## Prompt 1: Understand the Project Idea

```text
I want to build a new AI Agent.

Here is my initial idea:

[Explain the project idea]

First, analyze the idea.

Explain:

1. What problem are we solving?
2. What should the agent do?
3. What are the main features?
4. What technologies are suitable?
5. What external integrations are required?
6. What are the potential challenges?

Ask me questions wherever requirements are unclear.

Do not generate code yet.
```

## Prompt 2: Create PRD.md

```text
Based on our discussion, prepare a complete PRD.md file.

Include:

- Project overview.
- Problem statement.
- Objectives.
- Target users.
- Functional requirements.
- Non-functional requirements.
- Agent workflow.
- LLM requirements.
- Tools and integrations.
- Security requirements.
- Error handling.
- Testing strategy.
- Deployment requirements.
- Acceptance criteria.

Identify missing requirements before finalizing the PRD.
```

## Prompt 3: Analyze Architecture

```text
Review PRD.md and propose a suitable architecture.

Explain:

- Frontend architecture.
- Backend architecture.
- Agent orchestration.
- LLM integration.
- Tool integrations.
- Database requirements.
- Memory requirements.
- Security and approval controls.
- Deployment architecture.

Provide a simple architecture diagram.

Compare alternative approaches and explain your recommendation.

Do not start implementation.
```

## Prompt 4: Initialize the Project

```text
Review PRD.md and the agreed architecture.

Initialize the project structure.

Create or update CLAUDE.md with:

- Project overview.
- Technology stack.
- Architecture.
- Coding standards.
- Development guidelines.
- Security rules.
- Testing instructions.

Do not implement all application features yet.
```

## Prompt 5: Implement One Feature at a Time

```text
We are ready to start implementation.

Implement the following feature:

[Feature Name]

Before coding:

1. Explain the implementation approach.
2. Identify the files to create or modify.
3. Explain dependencies.
4. Identify possible edge cases.
5. Define how the feature will be tested.

Implement only this feature.

After implementation:

- Run relevant tests.
- Explain the changes.
- Report any remaining issues.
```

## Prompt 6: Review the Implementation

```text
Review the existing implementation against PRD.md.

Check:

- Functional correctness.
- Architecture consistency.
- Code quality.
- Security.
- Error handling.
- Input validation.
- Output validation.
- Performance.
- Test coverage.

Identify issues and prioritize them by severity.

Do not modify files until I approve the proposed changes.
```

## Prompt 7: Test the Agent

```text
Prepare a test plan for our AI Agent.

Include:

- Unit tests.
- Integration tests.
- End-to-end tests.
- Prompt evaluation.
- Tool execution tests.
- Failure scenarios.
- Security tests.
- Performance tests.

Provide positive, negative, and edge-case scenarios.

Implement the tests incrementally.
```

## Prompt 8: Prepare for Deployment

```text
Review the complete application and prepare a deployment plan.

Consider:

- Production configuration.
- Environment variables.
- Secrets management.
- Database connectivity.
- Persistent storage.
- API security.
- Logging.
- Monitoring.
- Deployment strategy.
- Rollback strategy.

Explain each step before implementation.

Do not expose credentials.
```

## Prompt 9: Final Project Review

```text
Perform a complete review of our AI Agent.

Compare the implementation against PRD.md.

Verify:

1. All required features are implemented.
2. LLM integration works.
3. Tools work correctly.
4. Validation is implemented.
5. Error handling is present.
6. Security controls are applied.
7. Tests are passing.
8. Documentation is updated.
9. Deployment requirements are satisfied.

Prepare a final report with:

- Completed features.
- Pending features.
- Known limitations.
- Risks.
- Recommended improvements.

Do not claim completion for features that have not been tested.
```

---

# 23. Final Development Checklist

## Planning

- [ ] Problem statement defined.
- [ ] Agent objective defined.
- [ ] Target users identified.
- [ ] Inputs and outputs defined.
- [ ] PRD.md created.
- [ ] Acceptance criteria defined.

## Architecture

- [ ] Single-agent or multi-agent approach selected.
- [ ] Frontend requirements identified.
- [ ] Backend architecture designed.
- [ ] LLM provider selected.
- [ ] Tools identified.
- [ ] Memory requirements evaluated.
- [ ] Security and approval model defined.

## Claude Code Setup

- [ ] Claude Code installed.
- [ ] Project initialized.
- [ ] CLAUDE.md created.
- [ ] Skills configured where required.
- [ ] Hooks configured where required.
- [ ] Subagents configured where useful.
- [ ] MCP integrations configured where required.

## Development

- [ ] LLM integration implemented.
- [ ] Agent instructions implemented.
- [ ] Tool integrations implemented.
- [ ] Orchestration implemented.
- [ ] Input validation implemented.
- [ ] Output validation implemented.
- [ ] Error handling implemented.
- [ ] Memory implemented if required.

## Testing

- [ ] Unit tests completed.
- [ ] Integration tests completed.
- [ ] End-to-end tests completed.
- [ ] AI output evaluation completed.
- [ ] Tool execution tested.
- [ ] Security checks completed.
- [ ] Failure scenarios tested.

## Deployment

- [ ] Production configuration prepared.
- [ ] Secrets configured securely.
- [ ] Database and storage configured.
- [ ] Application deployed.
- [ ] Health checks verified.
- [ ] Monitoring configured.
- [ ] Logging configured.
- [ ] Backup and recovery considered.

## Maintenance

- [ ] Execution metrics monitored.
- [ ] API usage monitored.
- [ ] Costs monitored.
- [ ] Errors reviewed.
- [ ] AI output quality evaluated.
- [ ] Regression tests maintained.

---

# Conclusion

Building an AI Agent is not just about connecting an LLM API.

A reliable agent requires clear requirements, suitable architecture, well-defined instructions, controlled tool access, validation, testing, and monitoring.

### Recommended Development Sequence

```text
1. Define the Problem
        |
        v
2. Gather Requirements
        |
        v
3. Create PRD.md
        |
        v
4. Initialize Claude Code
        |
        v
5. Create CLAUDE.md
        |
        v
6. Design Architecture
        |
        v
7. Select LLM Provider
        |
        v
8. Identify Tools and Integrations
        |
        v
9. Implement Agent Logic
        |
        v
10. Add Skills, Hooks and MCP
        |
        v
11. Implement Validation and Guardrails
        |
        v
12. Add Memory if Required
        |
        v
13. Test and Evaluate
        |
        v
14. Build UI if Required
        |
        v
15. Deploy
        |
        v
16. Monitor and Improve
```

**Key principle:** Start with a simple, working agent. Add tools, memory, Skills, MCP, multi-agent orchestration, and automation only when the requirements justify them.
