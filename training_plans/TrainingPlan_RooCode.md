# RooCode Training Plan

This document provides a thorough training plan for using **RooCode**, an open‑source AI coding assistant that runs locally in your editor.  RooCode allows you to generate code, refactor existing projects, write documentation, create diagrams and automate tasks—all without sending your code to a remote server.  Because RooCode is privacy‑first and open source, it is ideal for organisations that prefer to retain control over their source code.  This plan guides developers through installation, configuration, and advanced usage of RooCode.  It also revisits fundamental computer‑science concepts to help you craft clear, algorithmic prompts.  Whether you are a seasoned engineer or a first‑year student reacquainting yourself with algorithms, this guide will equip you to get the most out of RooCode.

---

## 1  Purpose and Audience

The purpose of this training plan is to enable **developers** to adopt RooCode as a privacy‑preserving alternative to cloud‑hosted AI assistants.  No matter where you work, you can follow this guide to install RooCode, connect it to an AI model (OpenAI, Azure OpenAI or a local model) and use it for day‑to‑day coding tasks.  The plan emphasises algorithmic thinking—breaking problems into steps, selecting appropriate data structures and understanding complexity—because RooCode works best when given precise, logical instructions.  This document does not mention any specific team or location; it is designed for anyone interested in using RooCode.

---

## 2  Setting Up RooCode

RooCode integrates into Visual Studio Code, but it does not bundle its own language model.  You must install the extension and configure an AI provider before generating code.  Follow these steps:

### 2.1  Installation

1. **Install from Marketplace** – Visit the [Visual Studio Marketplace page for RooCode](https://marketplace.visualstudio.com/items?itemName=Roo-Code.Roo-Code) and click **Install**.  Alternatively, install from [Open VSX Registry](https://open-vsx.org/extension/roo-code/roo-code) if your environment uses Open VSX.
2. **Manual Install via VSIX** – Download the latest `.vsix` package from the [RooCode GitHub releases](https://github.com/RooCodeInc/Roo-Code/releases).  Open the Extensions view in VS Code (`Ctrl+Shift+X`), click the **…** menu and select **Install from VSIX**.  Choose the downloaded file and confirm installation.
3. **Verify Installation** – After installation, the RooCode icon appears in the Activity Bar.  Click it to open the RooCode panel.  A welcome message describes the available modes (Code, Architect, Doc, Ask, Debug, Orchestrator).

### 2.2  Configure an AI Provider

RooCode separates the interface from the language model backend.  You need to specify which model to use:

* **OpenAI API** – If your organisation has an OpenAI API key, you can connect RooCode to GPT‑3.5 or GPT‑4.  In VS Code, open **Settings** (`Ctrl+,`) and search for **“RooCode: Api Provider”**.  Choose **OpenAI**, then enter the API key in **“RooCode: Api Key”**.  Optionally set the model (e.g. `gpt-4o`) and temperature.
* **Azure OpenAI** – Many enterprises, including Programmers.io, prefer Azure OpenAI.  Choose **AzureOpenAI** as the provider and supply your endpoint URL, API key, API version (e.g. `2024-12-01-preview`) and deployment name.  This ensures your prompts and code stay within your Azure environment.
* **Custom Models (Local/Ollama)** – RooCode supports self‑hosted models like [Ollama](https://ollama.com) or other HTTP APIs.  Select **Custom** provider and set the base URL (e.g. `http://localhost:11434/api`), model name (e.g. `llama3` or `mistral-large`) and any authentication parameters.  This mode lets you run AI offline or on your own hardware for maximum privacy.

After configuring, restart VS Code.  RooCode will use the specified model for all prompts.  Remember that local models may require additional memory and CPU resources.

### 2.3  Permissions and Security

Because RooCode operates locally, it will ask for permission to read and write files, execute shell commands and open browser windows.  Grant only the permissions you need.  If you connect to an external API (OpenAI or Azure), ensure that the network settings and API keys comply with your organisation’s security policies.  When using a local model, your code never leaves your machine.

---

## 3  Exploring RooCode Modes

RooCode offers multiple modes tailored to different tasks.  Each mode benefits from clear, algorithmic prompts.  Here is a summary:

### 3.1  Code Mode

**Purpose:** Generate or edit code directly in the current file.

**Usage:** Highlight the code you want to refactor or place the cursor where you need new code.  Open the Command Palette (`Ctrl+Shift+P`) and run **“Roo Code: Run”**.  Describe the desired changes, such as *“Implement a Python function to parse a CSV file into a list of dictionaries”* or *“Refactor this C# loop using LINQ.”*  RooCode will insert code at your cursor or replace the selected text.  You can accept, modify or reject the output.

**Algorithmic Tips:** Provide algorithm details in your prompt.  For example, if parsing CSV, mention how to handle quoted fields and missing values.  If sorting, specify which algorithm to use (merge sort, quicksort, etc.).  Clear instructions lead to better results.

### 3.2  Architect Mode

**Purpose:** Generate high‑level scaffolding for new projects, services or modules.

**Usage:** From any file or an empty workspace, run **“Roo Code: Architect”** and describe your desired structure: *“Create a Flask app with endpoints for users and orders, including SQLAlchemy models and tests.”*  Architect Mode can create multiple files, directories and a README.  Use it to jump‑start new projects.

**Algorithmic Tips:** Outline the architecture you want.  Describe database relations, API endpoints, authentication flows or messaging patterns.  The more structure you provide, the closer the generated scaffolding will be to your needs.

### 3.3  Doc Mode

**Purpose:** Generate documentation, comments and pull‑request summaries.

**Usage:** Select code or open a file and run **“Roo Code: Doc”**.  Ask RooCode to produce function docstrings, class summaries or Markdown documentation.  Example: *“Write a docstring for this function that explains its parameters, return value and complexity.”*  RooCode can also generate PR descriptions summarising your changes.

**Algorithmic Tips:** Provide context like parameter types, expected behaviour and complexity requirements.  Ask for specific formats (e.g. PEP 257 docstrings) or diagrams (e.g. Mermaid).  This ensures accurate documentation.

### 3.4  Ask Mode and Debug Mode

**Ask Mode:** Use `Ask` to ask questions about your codebase.  For example, *“Where is the user authentication logic implemented?”* or *“How does the checkout process update inventory?”*  RooCode analyses your project and returns relevant information.

**Debug Mode:** Use `Debug` to diagnose errors and propose fixes.  Describe the error, provide the stack trace and ask for suggestions.  RooCode will analyse the code and suggest changes to resolve the issue.

### 3.5  Orchestrator Mode (Advanced)

**Purpose:** Execute multi‑step tasks across files and tools.  Orchestrator Mode can navigate your file system, run commands, open browsers and manage workflows.

**Usage:** Example tasks include generating a project plan, running tests, updating dependencies and creating release notes.  Because Orchestrator Mode can perform automated actions, use it carefully and review each step before confirming.

---

## 4  Algorithmic Thinking for RooCode

AI models rely on your instructions.  To provide clear, effective prompts, revisit these key computer‑science concepts:

1. **Problem Decomposition** – Break large tasks into steps.  For example, to build a CRUD API, list the models, endpoints, validation rules and authentication.  Ask RooCode to implement each part individually.
2. **Data Structures** – Specify whether to use lists, dictionaries, sets, stacks, queues or trees.  For instance, *“Use a priority queue to implement Dijkstra’s algorithm”* or *“Use a dictionary keyed by customer ID.”*
3. **Algorithms and Complexity** – Mention the algorithm you want (bubble sort vs. merge sort) and desired complexity (O(n log n) vs. O(n²)).  This guides the model toward efficient code.
4. **Examples** – Provide sample inputs and outputs.  If you want a function to validate passwords, include a couple of valid and invalid examples so RooCode knows the expected behaviour.
5. **Iterative Refinement** – Don’t accept the first suggestion blindly.  Review the output, identify issues and adjust your prompt.  For example, if a generated parser fails on quoted commas, update your prompt to address that case.

---

## 5  Training Exercises

The companion repository `training_repo_final` contains exercises to practise using RooCode and algorithmic prompting.  Focus on the **Python** examples for hands‑on learning and try the Java migration exercise for cross‑language practice.

1. **CSV Parsing (Python)** – In `python_examples/file_io.py`, implement `parse_csv_content` using RooCode.  Provide explicit instructions about splitting lines, handling quoted fields and returning a list of dictionaries with proper types.
2. **Student Statistics (Python)** – In `python_examples/data_processing.py`, implement `calculate_student_statistics`, `normalise_scores` and `group_by_grade`.  Use RooCode to generate code that calculates mean, median and mode, normalises scores between 0 and 100 and categorises students by grade.
3. **HTTP Client (Python)** – In `python_examples/api_client.py`, implement the `get` and `post` methods.  Ask RooCode to create asynchronous methods using `httpx`, handle timeouts and raise exceptions when the response status indicates an error.
4. **Library Model (Python)** – In `python_examples/model_script.py`, implement methods in the `Author`, `Book` and `Library` classes.  Use RooCode to generate functions like `add_book`, `remove_book`, `search_by_title` and `list_books`.  Request docstrings, type hints and list comprehensions.
5. **Java Migration** – In `java_migration/legacy_java/Example.java`, use RooCode’s `Ask` or `Orchestrator` mode to migrate the legacy code to a modern version using generics and streams.  Compare your result to `modern_java/Example.java`.

After completing each task, run the associated tests in the `tests` directory to verify correctness.  Reflect on how your prompts affected the generated code and adjust accordingly.

---

## 6  Additional Resources

* **RooCode Documentation** – The official docs are available at [docs.roocode.com](https://docs.roocode.com) and include tutorials, API reference and troubleshooting tips.
* **RooCode GitHub Repository** – Source code and releases at [https://github.com/RooCodeInc/Roo-Code](https://github.com/RooCodeInc/Roo-Code).
* **Basic Guide to Roo Code** – A detailed setup and usage guide on Medium: [https://medium.com/@nayib/basic-guide-to-roo-code-579facefedbe](https://medium.com/@nayib/basic-guide-to-roo-code-579facefedbe).
* **Videos** – Watch the following tutorials for visual explanations:
  * [RooCode v3.3 UPDATE: Fully Free Autonomous AI Agent](https://www.youtube.com/watch?v=PE-0P6SAZYc) – Walkthrough of installation and configuration.
  * [Roo Code is AMAZING – AI VSCode Extension](https://www.youtube.com/watch?v=r5T3h0BOiWw) – Demonstration of different modes and features.

---

## 7  Summary

By following this plan, developers can install and configure RooCode with OpenAI, Azure OpenAI or a custom model, understand its various modes and apply algorithmic thinking to prompt it effectively.  Practise using the exercises in the companion repository to generate code, refactor legacy projects, write documentation and create diagrams.  As with any AI tool, always review generated output for correctness, style and security before committing changes.