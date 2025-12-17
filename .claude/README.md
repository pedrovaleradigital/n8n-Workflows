# Claude Code Configuration for n8n Workflows

This directory contains local skills and agents to help you work with n8n workflows.

## Created Resources

### 1. n8n-expert Skill
**Location**: `.claude/skills/n8n-expert.md`

**Purpose**: Comprehensive knowledge base containing all n8n configurations, node types, integrations, and best practices.

**How to Use**:
```
@n8n-expert how do I configure an AI agent?
```

**Contains**:
- Node JSON structures
- AI Agent configurations
- Integration guides (Google Calendar, Airtable, PostgreSQL, Telegram, etc.)
- Data processing patterns
- Best practices and common issues

### 2. prompt-n8n-assistant Agent
**Location**: `.claude/agents/prompt-n8n-assistant.md`

**Purpose**: Specialized agent that uses the n8n-expert skill to provide interactive help with n8n workflows.

**How to Use**:
```
@prompt-n8n-assistant I need to create a workflow that sends Telegram messages when events are created in Google Calendar
```

**Capabilities**:
- Provides ready-to-use JSON configurations
- Explains n8n concepts and patterns
- Troubleshoots workflow issues
- Designs complete workflows
- Suggests best practices

## Quick Start Examples

### Ask about specific nodes:
```
@n8n-expert show me how to configure a webhook trigger
```

### Get integration help:
```
@prompt-n8n-assistant how do I integrate Google Sheets with n8n?
```

### Design a complete workflow:
```
@prompt-n8n-assistant create a workflow that:
1. Receives chat messages
2. Uses an AI agent to process them
3. Stores conversation history
4. Sends responses back
```

### Troubleshoot issues:
```
@prompt-n8n-assistant my AI agent is outputting strings instead of JSON objects, how do I parse them?
```

### Learn best practices:
```
@n8n-expert what are the best practices for error handling in n8n?
```

## Features Covered

### Triggers
- Chat Trigger
- Webhook Trigger
- Cron/Schedule Trigger
- Email Trigger
- Telegram Trigger

### Data Processing
- Code/Function nodes
- Set nodes
- IF/Switch nodes
- Merge nodes
- Item Lists

### AI & LLM
- AI Agent configuration
- Memory management
- OpenAI integration
- Embeddings
- Vector stores (Pinecone)

### Integrations
- Google Services (Sheets, Calendar, Docs, Gmail)
- Airtable
- PostgreSQL
- Telegram
- Slack
- Notion
- GitHub
- HTTP/REST APIs

### Advanced Topics
- Expression syntax
- Data structures
- Error handling
- Looping and batching
- Workflow connections
- JSON validation

## Replacing Old Files

You can now safely delete these files as their content is fully integrated:
- `0. n8n cheat sheet guide.txt`
- `0. n8n tips and tricks.txt`

The skill and agent provide:
- Better organization
- Interactive help
- Searchable knowledge
- Up-to-date examples
- Context-aware assistance

## Tips for Best Results

1. **Be specific**: The more details you provide, the better the help
2. **Ask follow-ups**: Request clarification or deeper explanations
3. **Request examples**: Always ask for JSON code when needed
4. **Describe your goal**: Explain what you're trying to achieve
5. **Share errors**: Include error messages for troubleshooting

## Maintenance

To update the knowledge base:
1. Edit `.claude/skills/n8n-expert.md` with new information
2. The agent will automatically use the updated knowledge
3. No need to modify the agent file unless changing behavior

---

**Created**: 2025-12-17
**Purpose**: Replace static .txt files with interactive, intelligent n8n assistance
