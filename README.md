# ✍️ AI Blog Writing Agent (LangGraph + LLM + Streamlit)

An end-to-end AI-powered content generation system built using **LangGraph**, **Large Language Models (LLMs)**, and **Streamlit**. This project automates the entire lifecycle of technical content creation—from initial research to final formatted output with AI-generated visuals.

The system utilizes a **multi-agent orchestration workflow** to ensure high-quality, structured, and fact-checked blog posts.

---

## 📌 Project Overview

This pipeline transforms a simple user topic into a comprehensive technical article by coordinating specialized AI agents. It addresses the common "hallucination" and "lack of structure" issues in standard LLM outputs by:

- **Routing:** Determining if the topic requires live web data.
- **Planning:** Breaking the topic into a logical outline (H1, H2, H3).
- **Parallel Writing:** Generating different sections of the blog simultaneously for speed and focus.
- **Visual Integration:** Automatically generating relevant diagrams or images to support the text.

---

## 🚀 Key Features

- **Intelligent Routing:** Automatically detects if a topic is "general knowledge" or requires "live research" via Tavily.
- **Multi-Agent Planning:** An Orchestrator agent creates a structured blueprint before any writing begins.
- **Parallel Execution:** Individual "Worker" agents write specific sections in parallel, significantly reducing latency.
- **Automated Diagrams:** Integration with Gemini Image API to create and embed technical visuals.
- **State Management:** Built on LangGraph to maintain context and allow for "cycles" (e.g., rewriting a section if it fails quality checks).
- **Interactive UI:** A polished Streamlit interface to track progress, view logs, and download the final Markdown.

---

## 🛠️ Tech Stack

| Component         | Technology/Tool         |
|-------------------|------------------------|
| Orchestration     | LangGraph              |
| LLM               | Mistral/Ollama         |
| Web Search        | Tavily API             |
| Image Generation  | Gemini Image API       |
| UI                | Streamlit              |
| State Management  | LangGraph              |

---

## 🗼 System Architecture & Pipeline Flow

The following diagram illustrates how data moves through the system, from the initial user query to the final Markdown output.

```mermaid
graph TD
    A[User Input] --> B{Router}
    B -->|General Knowledge| C[Orchestrator]
    B -->|Live Research| D[Tavily Search]
    D --> C
    C --> E[Worker Agents]
    E --> F[Image Pipeline]
    F --> G[Final Markdown]
