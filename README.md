# Draft

An experimental, GitHub-style markdown editor with AI assistance, drag-and-drop image uploads, and live preview. Meant to make barrier of entry for creating blog posts *very* low. 


## 🚀 Quick Start

### "Installation"

```bash
uvx --with git+https://github.com/koaning/draft draft --help
```

### Setup API Keys

```bash
# For Gemini (default)
export LLM_GEMINI_KEY="your-key-here"
# Or configure via: llm keys set gemini

# For OpenAI
export OPENAI_API_KEY="your-key-here"
```

### Launch the Editor

```bash
# Basic usage
draft --write-folder ./my-documents

# With custom system prompt
draft --write-folder ./blog-posts --system-prompt ./prompts/blog-writer.md

# Advanced options
draft \
  --write-folder ./content \
  --system-prompt ./prompts/technical-writer.md \
  --model gemini-2.0-flash \
  --host 0.0.0.0 \
  --port 8080 \
  --debug
```

## 📖 Usage Guide

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Cmd+Enter` | Open AI command palette |
| `Cmd+S` | Save document |
| `Cmd+Z` | Undo last action |
| `Enter` | Accept AI suggestion |
| `X` | Retry AI suggestion |
| `Esc` | Cancel/close modals |

### AI Commands

After selecting text and pressing `Cmd+Enter`, try prompts like:
- "Make this more formal"
- "Fix grammar and spelling"
- "Simplify for a general audience"
- "Translate to Spanish"
- "Add more detail and examples"
- "Convert to bullet points"

### Image Workflow

1. **Drag image** into the editor
2. **Enter caption** in the auto-selected placeholder
3. **Images auto-saved** to document folder with UUID names
4. **Relative paths** ensure portability across systems

## 📁 File Structure

Draft creates a clean, Quarto blog-ready structure:

```
my-documents/
├── my-first-post/
│   ├── index.qmd          # Main content with frontmatter
│   ├── hero-image.png     # Uploaded images (UUID-named)
│   └── diagram.jpg
├── another-article/
│   ├── index.qmd
│   └── screenshot.png
└── documentation/
    ├── index.qmd
    ├── architecture.png
    └── flowchart.svg
```

### Frontmatter Format

```markdown
---
title: "My Blog Post"
description: "A brief description"
date: 2024-01-15
---

# Your content here

![](hero-image.png)
```

## 🤝 LLM Providers

Draft uses [Simon Willison's LLM library](https://llm.datasette.io/), supporting many providers:

### Google Gemini (Default)
```bash
export LLM_GEMINI_KEY="your-key"
# Or configure via: llm keys set gemini
```

### OpenAI
```bash
export OPENAI_API_KEY="your-key"
draft --write-folder ./docs --model gpt-4o
```

### Anthropic Claude
```bash
llm install llm-claude-3
export ANTHROPIC_API_KEY="your-key"
draft --write-folder ./docs --model claude-3-opus
```

### Local Models (Ollama)
```bash
llm install llm-ollama
draft --write-folder ./docs --model ollama/llama3
```

### List Available Models
```bash
llm models
```

