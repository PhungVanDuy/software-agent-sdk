# Frequently Asked Questions (FAQ)

This FAQ provides answers to common questions about the OpenHands Software Agent SDK.

## Table of Contents

- [General Questions](#general-questions)
- [Getting Started](#getting-started)
- [Features & Capabilities](#features--capabilities)
- [Tools & Architecture](#tools--architecture)
- [Examples & Documentation](#examples--documentation)
- [Community & Support](#community--support)
- [Contributing](#contributing)
- [Licensing & Citation](#licensing--citation)

---

## General Questions

### What is the OpenHands Software Agent SDK?

The OpenHands Software Agent SDK is a set of Python and REST APIs for **building agents that work with code**. It provides a composable and extensible foundation for creating production-ready software agents.

### Who is this SDK for?

The SDK is designed for developers who want to:
- Build AI-powered coding assistants
- Automate software development tasks
- Create custom developer tools and experiences
- Integrate AI agents into existing workflows

### What powers the OpenHands ecosystem?

The SDK is the engine behind:
- [OpenHands CLI](https://github.com/OpenHands/OpenHands-CLI) - Command-line interface for OpenHands
- [OpenHands Cloud](https://github.com/OpenHands/OpenHands) - Cloud-based OpenHands platform

---

## Getting Started

### How do I install the SDK?

For detailed installation instructions, please refer to the [Getting Started Guide](https://docs.openhands.dev/sdk/getting-started).

### What are the basic requirements?

You'll need:
- Python environment
- An LLM API key (e.g., Anthropic API key for Claude)
- The OpenHands SDK package installed

### How do I create my first agent?

Here's a minimal example:

```python
import os

from openhands.sdk import LLM, Agent, Conversation, Tool
from openhands.tools.file_editor import FileEditorTool
from openhands.tools.task_tracker import TaskTrackerTool
from openhands.tools.terminal import TerminalTool


llm = LLM(
    model="anthropic/claude-sonnet-4-5-20250929",
    api_key=os.getenv("LLM_API_KEY"),
)

agent = Agent(
    llm=llm,
    tools=[
        Tool(name=TerminalTool.name),
        Tool(name=FileEditorTool.name),
        Tool(name=TaskTrackerTool.name),
    ],
)

cwd = os.getcwd()
conversation = Conversation(agent=agent, workspace=cwd)

conversation.send_message("Write 3 facts about the current project into FACTS.txt.")
conversation.run()
print("All done!")
```

---

## Features & Capabilities

### What can I use the SDK for?

You can use the OpenHands Software Agent SDK for:

- **One-off tasks** - Like building a README for your repo
- **Routine maintenance tasks** - Like updating dependencies
- **Major tasks** - Involving multiple agents, like refactors and rewrites
- **Building new developer experiences** - Custom tools and interfaces

### What types of workspaces are supported?

Agents can work in two types of workspaces:

1. **Local machine** - Use your local filesystem as the workspace
2. **Ephemeral workspaces** - Run inside isolated environments (e.g., Docker or Kubernetes) using the Agent Server

### Can I use multiple agents together?

Yes! The SDK supports multi-agent architectures for complex tasks like refactors and rewrites.

---

## Tools & Architecture

### What built-in tools are available?

The SDK includes several built-in tools:

- **TerminalTool** - Execute terminal commands
- **FileEditorTool** - Read and edit files
- **TaskTrackerTool** - Track and manage tasks

### Can I create custom tools?

Yes! The SDK is designed to be extensible. You can create custom tools to extend agent capabilities. Check the [Guides](https://docs.openhands.dev/sdk/guides/hello-world) for tutorials on building custom tools.

### What is the Agent Server?

The Agent Server provides a REST API for running agents in ephemeral workspaces. It enables:
- Client-server architecture
- WebSocket connections for real-time communication
- Isolated execution environments

---

## Examples & Documentation

### Where can I find examples?

The `examples/` directory contains comprehensive usage examples:

| Directory | Description |
|-----------|-------------|
| `examples/01_standalone_sdk/` | Basic agent usage, custom tools, and microagents |
| `examples/02_remote_agent_server/` | Client-server architecture and WebSocket connections |
| `examples/03_github_workflows/` | CI/CD integration and automated workflows |

### Where is the full documentation?

Visit **[https://docs.openhands.dev/sdk](https://docs.openhands.dev/sdk)** for:

- [Getting Started Guide](https://docs.openhands.dev/sdk/getting-started) - Installation and setup
- [Architecture & Core Concepts](https://docs.openhands.dev/sdk/arch/overview) - Agents, tools, workspaces, and more
- [Guides](https://docs.openhands.dev/sdk/guides/hello-world) - Hello World, custom tools, MCP, skills, and more
- [API Reference](https://docs.openhands.dev/sdk/guides/agent-server/api-reference/server-details/alive) - Agent Server REST API documentation

---

## Community & Support

### How can I get help?

- **Slack** - [Join our Slack community](https://openhands.dev/joinslack) to connect with other users and the OpenHands team
- **GitHub Issues** - Report bugs or request features on the [GitHub Repository](https://github.com/OpenHands/agent-sdk)
- **Documentation** - Check the [complete documentation](https://docs.openhands.dev/sdk)

### Is there a community I can join?

Yes! Join our [Slack workspace](https://all-hands.dev/joinslack) to:
- Ask questions
- Share your projects
- Get help from the community
- Stay updated on new releases

---

## Contributing

### How can I contribute to the project?

We welcome contributions! For development setup, testing, and contribution guidelines, see [DEVELOPMENT.md](DEVELOPMENT.md).

### Where can I find the source code?

The source code is available on GitHub: [https://github.com/OpenHands/agent-sdk](https://github.com/OpenHands/agent-sdk)

---

## Licensing & Citation

### What license is the SDK released under?

The OpenHands Software Agent SDK is released under the [MIT License](LICENSE).

### How should I cite this project?

If you use the OpenHands Software Agent SDK in your research, please cite:

```bibtex
@misc{wang2025openhandssoftwareagentsdk,
      title={The OpenHands Software Agent SDK: A Composable and Extensible Foundation for Production Agents}, 
      author={Xingyao Wang and Simon Rosenberg and Juan Michelini and Calvin Smith and Hoang Tran and Engel Nyst and Rohit Malhotra and Xuhui Zhou and Valerie Chen and Robert Brennan and Graham Neubig},
      year={2025},
      eprint={2511.03690},
      archivePrefix={arXiv},
      primaryClass={cs.SE},
      url={https://arxiv.org/abs/2511.03690}, 
}
```

### Where can I read the technical paper?

The technical paper is available on arXiv: [https://arxiv.org/abs/2511.03690](https://arxiv.org/abs/2511.03690)

---

## Still Have Questions?

If your question isn't answered here:

1. Check the [full documentation](https://docs.openhands.dev/sdk)
2. Search [existing GitHub issues](https://github.com/OpenHands/agent-sdk/issues)
3. Ask in our [Slack community](https://openhands.dev/joinslack)
4. Open a new issue on GitHub

<p align="right">(<a href="#top">back to top</a>)</p>