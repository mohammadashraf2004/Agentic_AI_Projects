🚀 Project Overview
This project leverages LangChain and LangGraph to create a stateful, cyclic AI workflow. The system doesn't just write an essay; it plans it, performs web searches for factual data, drafts the content, critiques itself, and then performs targeted research to address those critiques over multiple revisions.

🛠️ Core Components
The architecture is built on a StateGraph, where each node represents a specific stage of the writing process:

Planner: Creates a high-level outline and section-specific instructions.

Research Plan: Generates search queries based on the task and fetches real-world data using the Tavily API.

Generation (Writer): Synthesizes the plan and research data into a cohesive 5-paragraph essay.

Reflection (Grader): Acts as a teacher to provide detailed critiques on style, depth, and accuracy.

Research Critique: Performs "gap-fill" research specifically focused on the weaknesses identified during reflection.

🔄 The Workflow
Start: The user provides a topic (e.g., "The difference between LangChain and LangSmith").

Planning & Initial Research: The agent outlines the essay and searches the web for initial facts.

The Loop: * The Generator writes/revises the draft.

The Reflector critiques the draft.

The Researcher gathers more info based on that critique.

Termination: The process repeats until the max_revisions limit is reached, at which point the final draft is returned.

💻 Technical Stack
Orchestration: LangGraph (StateGraph).

LLM: OpenAI gpt-3.5-turbo.

Search Engine: Tavily.

Memory: SQLite (SqliteSaver) for persistent thread-based conversations.

UI: Includes a Gradio-based GUI (via helper functions) for easy interaction.
