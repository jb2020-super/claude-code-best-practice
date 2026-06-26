# Claude Code Best Practice

A guide to using Claude Code effectively, including common commands and usage patterns.

## Table of Contents

- [Installation](#installation)
- [CLI Commands](#cli-commands)
- [Slash Commands](#slash-commands)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Common Workflows](#common-workflows)

---

## Installation

```bash
npm install -g @anthropic-ai/claude-code
```

---

## CLI Commands

Start Claude Code from the terminal:

```bash
# Launch interactive session
claude

# Start with an initial prompt
claude "explain this codebase"

# Run a one-shot command (non-interactive)
claude -p "fix the bug in src/app.js"

# Specify a model
claude --model claude-opus-4-8

# Limit conversation turns
claude --max-turns 10

# Specify allowed tools
claude --allowedTools "Bash,Read,Write,Edit"

# Pipe input from stdin
cat file.txt | claude -p "summarize this"

# Output in JSON format
claude -p "list all API endpoints" --output-format json

# Continue the most recent conversation
claude --continue

# Resume a specific conversation
claude --resume <conversation-id>

# Print version
claude --version

# Show help
claude --help
```

---

## Slash Commands

These commands are used inside an active Claude Code session:

| Command | Description |
|---------|-------------|
| `/help` | Show all available slash commands |
| `/clear` | Clear the current conversation history |
| `/compact` | Compact conversation to save context space |
| `/config` | Open configuration settings |
| `/cost` | Show token usage and cost for current session |
| `/doctor` | Check environment and diagnose issues |
| `/exit` | Exit Claude Code |
| `/init` | Initialize a `CLAUDE.md` file in the project |
| `/login` | Log in to your Anthropic account |
| `/logout` | Log out of your Anthropic account |
| `/memory` | View and manage persistent memory |
| `/model` | Switch the AI model |
| `/pr_comments` | View comments on the current pull request |
| `/review` | Request a code review of current changes |
| `/status` | Show current session status |
| `/vim` | Toggle vim keybindings |

### Skill / Custom Slash Commands

```bash
# Run the built-in deep-research skill
/deep-research "how does React reconciliation work?"

# Run a code review
/code-review

# Initialize CLAUDE.md
/init
```

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Enter` | Send message / confirm |
| `Shift+Enter` | Insert newline |
| `Ctrl+C` | Cancel current operation |
| `Ctrl+D` | Exit Claude Code |
| `↑` / `↓` | Navigate message history |
| `Tab` | Accept auto-complete suggestion |
| `Shift+Tab` | Cycle through suggestions |

---

## Common Workflows

### Ask a question about the codebase

```bash
claude "how does authentication work in this project?"
```

### Fix a bug

```bash
claude "fix the null pointer exception in src/utils.js"
```

### Write tests

```bash
claude "write unit tests for the UserService class"
```

### Code review before committing

```bash
# Stage changes first, then run
/review
```

### Initialize project context

```bash
# Creates a CLAUDE.md with project conventions
/init
```

### One-shot script (CI-friendly)

```bash
claude -p "check for any TODO comments and list them" --output-format json
```

### Add custom instructions via CLAUDE.md

Create a `CLAUDE.md` file at the root of your project:

```markdown
# Project Guidelines

- Use TypeScript strict mode
- Run `npm test` before committing
- Follow the existing code style
```

Claude Code reads this file automatically to understand project-specific conventions.

---

## Tips

- Prefix a message with `#` to save it to persistent memory: `# always use tabs for indentation`
- Use `/compact` when the conversation gets long to free up context space
- Use `--allowedTools` to restrict what tools Claude can use for safer automation
- Place a `CLAUDE.md` in subdirectories to provide context for specific modules
