# Loxia Autopilot CLI

> **Dependency:** This software requires [Node.js](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) (includes npm). Please install Node.js before proceeding.

> AI-powered development companion that builds, modifies, and manages your projects using multiple AI models.

[![Version](https://img.shields.io/badge/version-0.5.9-blue.svg)](https://github.com/loxia-ai/autopilot-cli)
[![License](https://img.shields.io/badge/license-SEE%20LICENSE%20IN%20LICENSE.txt-green.svg)](LICENSE.txt)
[![Node](https://img.shields.io/badge/node-%3E%3D16.0.0-brightgreen.svg)](https://nodejs.org)

## 🚀 Quick Start

### Installation

```bash
# Install globally
npm install -g loxia-autopilot-cli
```

### Setup

1. **Get your API key** from [https://autopilot.loxia.ai/account/api-keys](https://autopilot.loxia.ai/account/api-keys)

2. **Set your API key:**
```bash
loxia key --set lx_your_api_key_here
```

3. **Verify setup:**
```bash
loxia status
```

4. **Start building:**
```bash
loxia do "create a React app with TypeScript"
```

## 📋 Commands Overview

| Command | Description | Example |
|---------|-------------|---------|
| `loxia do` | Create new project | `loxia do "build a web app" --model anthropic-sonnet` |
| `loxia make` | Alias for `do` command | `loxia make "build API" --strategy intelligence` |
| `loxia resume` | Resume existing project | `loxia resume ./my-project --strategy intelligence` |
| `loxia modify` | Modify existing code | `loxia modify ./app "add authentication" --model azure-openai-gpt4` |
| `loxia models` | List available models | `loxia models --pricing` |
| `loxia budget` | Manage budget limits | `loxia budget --set 25.00` |
| `loxia key` | Manage API keys | `loxia key --view` |
| `loxia status` | Check service health | `loxia status --models` |
| `loxia mode` | Show interaction mode | `loxia mode` |

## 🤖 Model Selection

### Available Models

| Model | Provider | Best For | Speed | Quality | Cost |
|-------|----------|----------|-------|---------|------|
| `azure-ai-phi4` | Microsoft | Code, efficiency | ⚡⚡⚡ | ⭐⭐⭐ | 💰 |
| `azure-ai-grok3` | xAI | Creative, conversation | ⚡⚡ | ⭐⭐⭐⭐ | 💰💰 |
| `anthropic-haiku` | Anthropic | Speed, summaries | ⚡⚡⚡ | ⭐⭐ | 💰 |
| `anthropic-sonnet` | Anthropic | Balanced performance | ⚡⚡ | ⭐⭐⭐⭐ | 💰💰 |
| `anthropic-opus` | Anthropic | Highest quality | ⚡ | ⭐⭐⭐⭐⭐ | 💰💰💰💰 |
| `azure-openai-gpt4` | OpenAI | Analysis, reasoning | ⚡ | ⭐⭐⭐⭐⭐ | 💰💰💰 |
| `azure-openai-gpt35` | OpenAI | Fast, cost-effective | ⚡⚡ | ⭐⭐⭐ | 💰 |
| `google-gemini` | Google | Versatile | ⚡⚡ | ⭐⭐⭐ | 💰 |

### Model Selection Options

#### Explicit Model Selection
```bash
# Use specific models
loxia do "build React app" --model anthropic-sonnet
loxia do "create Python API" --model azure-openai-gpt4  
loxia do "quick prototype" --model azure-ai-phi4
loxia resume ./project --model anthropic-opus
loxia modify ./app "add auth" --model azure-ai-grok3
```

#### Strategy-Based Selection
Choose a strategy and let Loxia automatically select the best model:

```bash
# Speed strategy (fastest models first)
loxia do "quick prototype" --strategy speed

# Intelligence strategy (smartest models first)  
loxia do "complex algorithm" --strategy intelligence

# Balanced strategy (good mix of speed and quality)
loxia do "web application" --strategy balanced

# Context strategy (largest context windows)
loxia do "analyze large codebase" --strategy context
```

**Strategy Model Preferences:**
- **Speed**: `haiku` → `phi4` → `gpt35` → `gemini` → `sonnet` → `gpt4` → `opus`
- **Intelligence**: `opus` → `gpt4` → `grok3` → `sonnet` → `gemini` → `gpt35` → `haiku`
- **Balanced**: `sonnet` → `gpt4` → `grok3` → `gemini` → `opus` → `gpt35` → `haiku`
- **Context**: Prioritizes models with largest context windows

## 🎛️ Interaction Modes

### Auto Mode
Run completely autonomously without user interaction:
```bash
loxia do "build a todo app" --auto-mode
loxia resume ./project --auto-mode
```

### Semi-Auto Mode
Run autonomously but enter interactive mode when job is complete:
```bash
loxia do "create web app" --semi-auto-mode
loxia modify ./app "add feature" --semi-auto-mode
```

### Interactive Mode (Default)
Full interactive mode with user prompts and real-time interaction.

## 📁 File Input Support

### Read Task Description from File
```bash
# Read description from file
loxia do --from-file ./requirements.txt
loxia do --file ./project-spec.md --output ./my-project

# Also works with make command
loxia make --from-file ./task-description.txt --model anthropic-sonnet
```

### Modify from File
```bash
# Read modification instructions from file
loxia modify ./src --from-file ./changes.txt --strategy intelligence
```

## 💰 Budget Management

### Set Budget Limits
```bash
# Set budget limit
loxia budget --set 25.00

# View current usage
loxia budget --view

# Check cost for specific model
loxia budget --model anthropic-opus
```

### Cost Estimation
```bash
# Get cost estimate before running
loxia do "build app" --model anthropic-opus --estimate

# Check if operation fits budget
loxia do "complex task" --budget-check
```

## 🛠️ Detailed Usage

### Creating New Projects
```bash
# Basic project creation
loxia do "create a todo app with React and TypeScript"

# With specific model and output directory
loxia do "build a REST API with Node.js" \
  --model azure-openai-gpt4 \
  --output ./my-api

# With cost estimation and auto mode
loxia do "complex web application" \
  --strategy intelligence \
  --estimate \
  --auto-mode

# From file with budget check
loxia do --from-file ./requirements.txt \
  --budget-check \
  --semi-auto-mode
```

### Resuming Projects
```bash
# Resume with original settings
loxia resume ./my-project

# Override model for this session
loxia resume ./my-project --model anthropic-opus

# Change strategy and mode for the session
loxia resume ./my-project --strategy speed --auto-mode
```

### Modifying Existing Code
```bash
# Modify existing project
loxia modify ./my-app "add user authentication system"

# Use specific model for modifications
loxia modify ./docs "update API documentation" \
  --model anthropic-sonnet

# Modify with strategy preference and file input
loxia modify ./src --from-file ./changes.txt \
  --strategy balanced \
  --semi-auto-mode
```

### Model Information
```bash
# List all available models
loxia models

# Show details for specific model
loxia models --model anthropic-sonnet

# Show pricing comparison
loxia models --pricing

# Enhanced service status
loxia status --models --pricing
```

## ⚙️ Configuration

### Environment Variables
```bash
# Server configuration
export LOXIA_SERVER_URL="https://autopilot-api.azurewebsites.net"
export LOXIA_USE_SERVER_LLM=true

# Model selection
export LOXIA_LLM_STRATEGY=balanced

# Budget settings
export LOXIA_BUDGET_LIMIT=25.00
export LOXIA_BUDGET_HARD_LIMIT=true

# Logging
export LOXIA_LOG_LEVEL=info
export LOXIA_DETAILED_LOGGING=false

# Timeouts and retries
export LOXIA_TIMEOUT=60000
export LOXIA_MAX_RETRIES=3
```

### Configuration File
Create `.loxia-config.json` in your project or `~/.loxia/config.json` globally:

```json
{
  "llmStrategy": "balanced",
  "useServerLLM": true,
  "budget": {
    "limit": 50.00,
    "hardLimit": false,
    "warningThreshold": 0.8
  },
  "logging": {
    "logLevel": "info",
    "file": true
  },
  "tools": {
    "browser": {
      "enabled": true,
      "headless": true
    },
    "terminal": {
      "enabled": true
    }
  }
}
```

## 🔧 Advanced Features

### Interactive Commands
During execution, you can use these interactive commands:

```bash
Loxia › help          # Show available commands
Loxia › models        # List available models  
Loxia › budget        # Check current budget
Loxia › status        # Check service health
Loxia › pause         # Pause execution
Loxia › exit          # End session
```

### Global Keyboard Shortcuts
- **Ctrl+I**: Enter interactive mode from any execution state

### Cost Control
```bash
# Set hard budget limit (blocks operations that exceed budget)
loxia budget --set 10.00
export LOXIA_BUDGET_HARD_LIMIT=true

# Get cost estimates before running
loxia do "expensive task" --estimate --model anthropic-opus

# View detailed cost breakdown
loxia budget --view
```

### Health Monitoring
```bash
# Check service status
loxia status

# Detailed status with models and pricing
loxia status --models --pricing

# Check specific model availability
loxia models --model azure-openai-gpt4
```

## 🚨 Error Handling & Troubleshooting

### Common Issues

#### API Key Problems
```bash
# Check API key status
loxia key --view

# Set new API key
loxia key --set lx_your_new_key

# Remove invalid key
loxia key --remove
```

#### Server Connection Issues
```bash
# Check server status
loxia status

# Force local mode (requires API keys for individual services)
LOXIA_USE_SERVER_LLM=false loxia do "build app"
```

#### Budget Exceeded
```bash
# Check current usage
loxia budget --view

# Increase budget limit
loxia budget --set 50.00

# Use cheaper models
loxia do "task" --model anthropic-haiku
```

### Debug Mode
```bash
# Enable detailed logging
export LOXIA_LOG_LEVEL=debug
export LOXIA_DETAILED_LOGGING=true

# Run with debug info
LOXIA_DEBUG=true loxia do "test task"
```

## 📊 Usage Examples

### Web Development
```bash
# React application with TypeScript
loxia do "create a modern React app with TypeScript, Tailwind CSS, and routing" \
  --model anthropic-sonnet \
  --output ./my-react-app

# Add authentication to existing app
loxia modify ./my-react-app "add user authentication with login/signup forms" \
  --model azure-openai-gpt4 \
  --semi-auto-mode

# Full-stack application from file
loxia do --from-file ./fullstack-requirements.txt \
  --strategy intelligence \
  --budget-check
```

### Python Development
```bash
# Data analysis script
loxia do "create a Python script that analyzes CSV data and creates visualizations" \
  --model anthropic-sonnet \
  --auto-mode

# API development
loxia do "create a FastAPI REST API with database integration and authentication" \
  --model azure-openai-gpt4 \
  --output ./my-api
```

### Quick Prototyping
```bash
# Fast prototypes
loxia do "quick calculator app" --strategy speed --auto-mode
loxia make "simple landing page" --model azure-ai-phi4
loxia do "basic chat interface" --model anthropic-haiku --estimate
```

## 🔐 Security & Privacy

- **API Keys**: Stored encrypted locally in `~/.loxia/credentials`
- **No Data Persistence**: Conversations are stored locally in your project directories
- **Secure Transmission**: All API communications use HTTPS
- **Local Processing**: Tool operations run locally on your machine

## 🆘 Support

### Getting Help
```bash
# Show available commands
loxia --help

# Show command-specific help
loxia do --help
loxia models --help

# Check service status
loxia status

# Check current interaction mode
loxia mode
```

### Resources
- **Documentation**: [https://docs.loxia.ai](https://docs.loxia.ai)
- **API Keys**: [https://autopilot.loxia.ai/account/api-keys](https://autopilot.loxia.ai/account/api-keys)
- **Issues**: [https://github.com/loxia-ai/autopilot-cli/issues](https://github.com/loxia-ai/autopilot-cli/issues)

### Quick Reference
```bash
# Essential commands
loxia do "task" --model MODEL --strategy STRATEGY --auto-mode
loxia make --from-file FILE --output DIR --estimate
loxia resume PROJECT --model MODEL --semi-auto-mode
loxia modify DIR "instructions" --strategy STRATEGY --auto-mode
loxia models --pricing
loxia budget --set AMOUNT --view
loxia status --models
loxia key --set KEY --view
loxia mode
```

## 📄 License

SEE LICENSE IN LICENSE.txt

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

**Built with ❤️ by Loxia Labs**