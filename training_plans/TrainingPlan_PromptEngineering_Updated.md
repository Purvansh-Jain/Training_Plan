# Prompt Engineering Training Plan

Large‑language models (LLMs) usefulness depends entirely on the **prompts** you provide. Prompt engineering is the practice of crafting clear, precise instructions that guide an AI model toward the desired output.  This training plan teaches developers how to design effective prompts based on sound computer‑science principles.  It revisits first‑year topics like algorithms, data structures and problem decomposition, and demonstrates how these concepts improve your prompts.  Whether you are new to AI or looking to refine your skills, this guide will help you harness the full potential of Copilot and RooCode.

---

## A]  Why Prompt Engineering Matters

When you ask a model to “write some code,” you leave it to guess what you need.  If you specify your goal, inputs, expected outputs, constraints and examples, you narrow the possibilities and increase accuracy.  Poorly written prompts lead to incorrect, incomplete or inefficient code; clear prompts result in reliable, maintainable solutions.  The principles of prompt engineering apply across languages and tools.  They are especially important when working with enterprise projects where security, performance and readability are critical.

### 1  Algorithmic Context

Programming tasks are built on algorithms and data structures.  In first‑year computer‑science courses you learn patterns like linear search, binary search, sorting algorithms and recursion.  You also learn to choose between lists, dictionaries, stacks, queues, trees and graphs.  When writing prompts, refer to these patterns explicitly: *“Implement a binary search algorithm”* or *“Use a hash map keyed by user ID”*.  This helps the model understand the performance requirements and data relationships.

### 2  Clarity and Detail

Ambiguity is the enemy of prompt engineering.  Avoid vague terms like “improve,” “better” or “clean up.”  Instead specify what you want to change and why.  For example: *“Refactor this function to reduce its time complexity from O(n²) to O(n log n)”* or *“Rewrite this code to follow PEP 8 style guidelines.”*  Provide the relevant code or function signature so the model has context.  If you need documentation, specify the format (docstring, JSDoc, Markdown) and include examples.

### 3  Iterative Refinement

Prompt engineering is not a one‑shot process.  After receiving a response from the model, review the output.  If it contains mistakes or omissions, adjust your prompt by adding constraints or examples.  Repeat until the output meets your requirements.  Keep a record of effective prompts to reuse and share with teammates.

---

## B]  Anatomy of a Well‑Structured Prompt

A well‑structured prompt typically includes these elements:

1. **Role or Perspective** – Define the persona or expertise you want the model to adopt.  Example: *“Act as a senior Python developer specialising in data processing.”*
2. **Task Description** – Clearly state what you want the model to do.  Use verbs like *implement*, *refactor*, *explain*, *document*, *test*, *summarise*.
3. **Inputs** – Describe the input types, formats and any relevant constraints.  Example: *“The function receives a list of strings where each string is a comma‑separated list of values.”*
4. **Outputs** – Describe the expected output type and structure.  Example: *“Return a dictionary with keys `mean`, `median` and `mode` mapped to floats.”*
5. **Algorithmic Constraints** – Mention performance, memory or algorithm requirements.  Example: *“Use merge sort for O(n log n) time complexity”* or *“Do not use recursion to avoid stack overflow.”*
6. **Examples** – Provide sample inputs and outputs, or templates for formatting.  Example: show a function signature with a docstring so the model mimics your style.
7. **Style Instructions** – Specify coding style, naming conventions and documentation guidelines.  Example: *“Use snake_case for variables and include type hints.”*

Here is an example of a well‑structured prompt:

> *You are a Python developer.  Implement a function `validate_password(password: str) -> bool` that checks whether a password is at least 8 characters long, contains an uppercase letter, a lowercase letter, a digit and a special character.  Return `True` if the password is valid, `False` otherwise.  Include a PEP 257 docstring and two example calls in a comment.*

This prompt defines the role, task, input, output, constraints and format, leaving little room for misinterpretation.

---

## C]  Principles for Effective Prompting

Use these principles to design prompts that yield accurate and useful results:

### 1  Be Specific

Specify what you want the model to do and how it should do it.  For example, *“Generate a list of prime numbers up to 100 using the Sieve of Eratosthenes”* is better than *“Write a prime generator.”*  Include relevant constraints like time complexity or memory usage.

### 2  Decompose Complex Tasks

Breaking large problems into smaller tasks improves the quality of the output and makes it easier to debug.  For instance, when building a web service, separate prompts for data models, API endpoints, input validation and tests.  This mirrors algorithmic decomposition: solve subproblems and compose the results.

### 3  Provide Examples

Demonstrate the expected input and output format.  If you want the model to produce a JSON response, include a sample JSON.  For diagrams, provide a small Mermaid snippet.  Examples act as a template the model can emulate.

### 4  Ask for Explanations

When you need to understand code or make improvements, ask the model to explain what the code does and why.  For example: *“Explain how this function calculates the Fibonacci sequence and suggest two optimisations.”*  Explanations reveal the model’s reasoning and help you identify errors or inefficiencies.

### 5  Use Chat Interfaces for Exploration

Tools like Copilot Chat and ChatGPT are ideal for brainstorming and iterative prompting.  You can ask for clarifications, request alternative implementations or explore different design choices.  This interactive approach is particularly useful when working on unfamiliar tasks.

---

## D]  Training Exercises

Use the exercises in the `training_repo` to practise prompt engineering.  Focus on Python tasks and apply the principles above.  After each task, review the generated code, adjust your prompts and rerun the model.

1. **Password Validation** – Prompt the AI to implement a function `is_strong_password(password: str) -> bool` based on specific criteria.  Ask for type hints, a docstring and example calls.
2. **Sorting Algorithms** – Ask the model to implement bubble sort, selection sort and merge sort on a list of integers.  Request a complexity analysis and test cases.  Compare the generated algorithms and discuss which is more efficient.
3. **File Parsing** – Prompt the AI to write a function that reads a log file, extracts timestamps and error messages and returns a summary dictionary.  Provide a sample log entry and specify error levels to filter.
4. **Data Transformation** – Ask the model to transform a list of student dictionaries (name, scores) into a dictionary keyed by name with value `Student` objects.  Include methods for computing GPA and printing a transcript.
5. **Unit Test Generation** – Provide a sample Python function and ask the AI to generate a set of `pytest` tests covering normal and edge cases.  Encourage the model to include descriptive assertion messages.
6. **Refactoring** – Give the model a legacy function with deep nesting or repeated code.  Ask it to refactor using smaller helper functions or list comprehensions.  Specify improvements such as readability or time complexity.

These exercises will sharpen your ability to design prompts that produce reliable code.  For each exercise, write down the prompt you used, note what worked and what did not, and iterate to improve the output.

---

## E]  Additional Resources

* **OpenAI Prompt Engineering Guide** – [https://platform.openai.com/docs/guides/prompt-engineering](https://platform.openai.com/docs/guides/prompt-engineering) – Official guide with examples and best practices.
* **GitHub Copilot Prompt Guide** – [https://github.blog/2023-09-12-how-to-write-better-prompts-for-github-copilot/](https://github.blog/2023-09-12-how-to-write-better-prompts-for-github-copilot/) – Tips for crafting prompts specifically for Copilot.


Videos:

| Topic                       | Video Title                                           | Link                                                              | Description                                       |
|-----------------------------|-------------------------------------------------------|-------------------------------------------------------------------|---------------------------------------------------|
| Prompt Engineering Basics   | *Prompt Engineering for Beginners*                   | [Watch](https://youtu.be/riO3e-FBieA?si=86gIO74zk2tYrjSW)               | Introduction to prompt design and common pitfalls. |
| Advanced Prompt Techniques  | *Advanced Prompt Engineering with GPT-4*             | [Watch](https://youtu.be/-XivIt_5oSw?si=agLozvFqrGiLT4Oz)               | Covers complex tasks, multi‑step prompts and more. |
| Demo    | *Master the core principles of prompt engineering with GitHub Copilot*             | [Watch](https://youtu.be/hh1nOX14TyY?si=flrngVtmrDbwFYEv)               | Shows iterative prompting to build a real project. |

---

## F]  Summary

Prompt engineering is a critical skill for working with AI coding assistants.  By grounding your prompts in algorithmic thinking, providing clear objectives and constraints, and iteratively refining your instructions, you can guide models like Copilot and RooCode to produce high‑quality code, tests, documentation and diagrams.  Use the exercises and resources in this plan to practise and improve.  As you gain experience, share effective prompts with your colleagues to build a collective knowledge base.