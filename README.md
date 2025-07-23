# Sidekick: An Autonomous AI Co-Worker

![Python](https://img.shields.io/badge/python-3.11-blue.svg) ![LangChain](https://img.shields.io/badge/LangChain-b546f1) ![Gradio](https://img.shields.io/badge/Gradio-ff7600)

Sidekick is an advanced AI agent designed to autonomously handle complex tasks by leveraging a powerful suite of tools and a unique self-correcting architecture. It goes beyond simple question-answering by planning, executing, and evaluating its own work to ensure it meets user-defined success criteria.

This project uses a novel **Worker-Evaluator** architecture built with **LangGraph**, where one agent performs the work and a second agent critically evaluates the output, providing feedback for iterative refinement.

---

## Core Features

* **🤖 Self-Correcting Architecture**: At its core is a **Worker-Evaluator** loop. The Worker agent uses tools to complete a task, and the Evaluator agent assesses the outcome against the user's success criteria, prompting retries or refinements until the goal is met.
* **🛠️ Comprehensive Toolset**: Sidekick comes equipped with a versatile set of tools to interact with the real world, including:
    * **Web Browse**: A **Playwright**-based toolkit for autonomous web navigation, interaction, and data extraction.
    * **Code Execution**: An integrated **Python REPL** for dynamic code generation and execution to solve computational problems.
    * **Web Search**: A Google Serper integration for fast and accurate web searches.
    * **File Management**: The ability to read, write, and list files in a local directory.
* **💬 Interactive UI**: A clean and user-friendly web interface built with **Gradio** that allows you to provide a task, define success criteria, and watch the agent's multi-step reasoning process in real-time.

---

## How It Works

The system is architected as a state machine using **LangGraph**. The flow follows a clear, cyclical path:

1.  **Request**: The user provides a prompt and optional **success criteria**.
2.  **Work**: The **Worker Agent** receives the request. It can use any of its available tools (like searching the web, writing code, or reading a file) to work towards the goal.
3.  **Evaluate**: Once the Worker produces a final answer, it's passed to the **Evaluator Agent**. The Evaluator assesses the response *strictly* against the initial success criteria.
4.  **Refine or Finish**:
    * If the criteria are not met, the Evaluator provides constructive feedback, and the state loops back to the **Worker** to try again with the new input.
    * If the criteria are met, the process concludes and the final, validated answer is presented to the user.



---

## Getting Started

Follow these steps to get Sidekick running on your local machine.

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <repository-name>
