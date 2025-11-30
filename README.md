# Context Engineering

Practical techniques for optimizing context management in Large Language Models (LLMs). This repository demonstrates six key strategies to improve LLM performance by managing what context is provided and how.

## Overview

As LLM context windows grow larger, the assumption that "more context is better" has proven false. This project explores techniques to optimize context delivery, improving accuracy, reducing costs, and enhancing response quality.

Based on insights from [How to Fix Your Context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html).

## Techniques

### 1. Tool Loadout
**Problem**: Loading too many tools reduces answer quality.  
**Solution**: Dynamically select only relevant tools using semantic similarity.

- Implements "Less is More" approach from [arXiv:2411.15399](https://arxiv.org/abs/2411.15399)
- Ask LLM what tools it needs before showing any tools
- Use embeddings to match and provide only relevant tools

📓 **Notebook**: `01_tool_loadout.ipynb`

### 2. Context Quarantine
**Problem**: Unnecessary context reduces accuracy.  
**Solution**: Separate concerns by isolating contexts between agents.

- Lead Agent and Subtask Agents operate independently
- No context sharing between different agent workflows
- Prevents context pollution across tasks

📓 **Notebook**: `02_context_quarantine.ipynb`

### 3. Context Pruning
**Problem**: Long contexts negatively impact LLM performance.  
**Solution**: Remove unnecessary information before passing to LLM.

- Implements techniques from [Provence](https://arxiv.org/abs/2501.16214)
- Strips irrelevant data while preserving essential information
- Reduces token usage and improves focus

📓 **Notebook**: `03_context_pruning.ipynb`

### 4. Context Summarization
**Problem**: Context distraction from verbose information.  
**Solution**: Summarize content tailored to the specific task.

- Addresses small context window limitations
- Reduces [context distraction](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html#context-distraction)
- Requires careful optimization for agent-specific needs

📓 **Notebook**: `04_context_summarization.ipynb`

### 5. Context Offloading
**Problem**: Not all data needs to be in LLM context.  
**Solution**: Store data externally for tool access.

- Inspired by Anthropic's ["think" tool](https://www.anthropic.com/engineering/claude-think-tool)
- Provides a "scratchpad" or "notepad" for the model
- Useful for logs, progress tracking, and working memory

📓 **Notebook**: `05_context_offloading.ipynb`

## Getting Started

### Prerequisites
- Python 3.11+
- AWS Account with Bedrock access
- Jupyter Notebook or JupyterLab

## Key Takeaway

**Garbage In, Garbage Out**: More context isn't always better. Strategic context management improves LLM performance, reduces costs, and delivers more accurate results.

## References

- [How to Fix Your Context](https://www.dbreunig.com/2025/06/26/how-to-fix-your-context.html)
- [Less is More: Optimizing Function Calling](https://arxiv.org/abs/2411.15399)
- [Provence: Context Pruning](https://arxiv.org/abs/2501.16214)
- [How Contexts Fail](https://www.dbreunig.com/2025/06/22/how-contexts-fail-and-how-to-fix-them.html)
- [Anthropic's Think Tool](https://www.anthropic.com/engineering/claude-think-tool)
