---
title: Local AI Orchestration
status: active
---

# Project Lugia: Localized Intelligence

Project Lugia is the dedicated framework within `theFenix` for hosting, orchestrating, and interacting with Large Language Models (LLMs) completely locally. This ensures absolute data privacy and zero reliance on external, proprietary API endpoints.

## Core Components
* **Model Hosting:** Ollama is utilized to pull, run, and serve open-source language models directly on local cluster hardware.
* **User Interface:** Open WebUI provides a seamless interface for interaction, local document uploading, and contextual querying.
* **Automation Workflows:** `n8n` is integrated into the stack to build automated pipelines, allowing the local LLMs to parse incoming server data, trigger scripts, or summarize logs from across the environment.
* **Resource Management:** Persistent volumes are mapped to independent storage drives to prevent heavy generation I/O operations from bottlenecking the primary operating systems.
