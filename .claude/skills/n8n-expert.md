# n8n Expert Skill

## Description
Expert knowledge base for n8n workflow automation platform. Provides comprehensive guidance on node configuration, JSON structures, AI agents, integrations, and best practices. Use this skill when users ask questions about n8n workflows, nodes, automation, or need help with n8n JSON configurations.

## Invocation Examples
- "How do I configure an AI Agent in n8n?"
- "What's the JSON structure for a webhook trigger?"
- "Help me with Google Calendar integration in n8n"
- "Show me examples of n8n HTTP Request nodes"
- "How do I use memory with AI agents in n8n?"
- "What are the best practices for n8n workflows?"

## When to Use
Invoke this skill whenever the user:
- Asks about n8n automation, workflows, or nodes
- Needs help with n8n JSON configurations
- Wants examples of specific n8n integrations (Airtable, PostgreSQL, Google services, Telegram, etc.)
- Needs guidance on AI Agent setup and manipulation
- Asks about expressions, data structures, or node connections in n8n
- Troubleshoots n8n workflow issues

## Knowledge Base

### 1. FUNDAMENTAL n8n CONCEPTS

#### Data Structure
n8n passes data between nodes as an array of objects:
```json
[
  {
    "json": {
      "property1": "value1",
      "property2": "value2"
    },
    "binary": {}
  }
]
```

#### Expressions
Access data using n8n expressions:
- Basic: `{{ $json.property }}`
- Nested: `{{ $json.parent.child.property }}`
- From specific node: `{{ $node["NodeName"].json.property }}`

#### Common Node Structure
```json
{
  "id": "unique-id",
  "name": "Node Name",
  "type": "node-type",
  "typeVersion": 2.2,
  "position": [x, y],
  "parameters": {
    // Node-specific configuration
  }
}
```

### 2. AI AGENT MODULE

#### Basic Configuration
```json
{
  "id": "agent-1",
  "name": "AI Agent",
  "type": "@n8n/n8n-nodes-langchain.agent",
  "position": [100, 100],
  "parameters": {
    "text": "={{ $json.chatInput }}",
    "options": {
      "systemMessage": "You are a helpful assistant."
    },
    "promptType": "define"
  },
  "typeVersion": 2.2
}
```

#### AI Agent Best Practices
1. Craft comprehensive system messages
2. Use dynamic expressions for input
3. Connect memory nodes for context
4. Validate JSON outputs
5. Test different models (gpt-4o vs gpt-4o-mini)

#### Memory Integration
```json
{
  "id": "memory-1",
  "name": "Memory Buffer",
  "type": "@n8n/n8n-nodes-langchain.memoryBufferWindow",
  "parameters": {
    "sessionKey": "={{ $json.sessionId }}",
    "contextWindowLength": 5
  }
}
```

### 3. TRIGGER NODES

#### Chat Trigger
```json
{
  "name": "Chat Trigger",
  "type": "@n8n/n8n-nodes-langchain.chatTrigger",
  "typeVersion": 1.1,
  "parameters": {
    "webhookId": "unique-webhook-id",
    "mode": "webhook",
    "public": true,
    "initialMessages": "Hello! How can I help you?",
    "options": {
      "responseMode": "responseNode",
      "allowedOrigins": "https://yourdomain.com",
      "loadPreviousSession": "memory"
    }
  }
}
```

#### Webhook Trigger
```json
{
  "name": "Webhook",
  "type": "n8n-nodes-base.webhook",
  "parameters": {
    "path": "incoming-data",
    "methods": ["POST"],
    "responseMode": "onReceived",
    "responseData": {
      "statusCode": 200,
      "body": "Webhook received"
    }
  }
}
```

#### Cron Trigger (Schedule)
```json
{
  "name": "Schedule",
  "type": "n8n-nodes-base.cron",
  "parameters": {
    "triggerTimes": {
      "item": [
        { "hour": 9, "minute": 0 },
        { "hour": 17, "minute": 0 }
      ]
    }
  }
}
```

### 4. DATA PROCESSING NODES

#### Code Node (Function)
```javascript
// Run once for all items
const newItems = [];
const inputData = $input.all().json;
for (const item of inputData) {
  newItems.push({
    json: {
      modifiedData: item.originalData,
      timestamp: new Date().toISOString()
    }
  });
}
return newItems;
```

#### Set Node (Edit Fields)
```json
{
  "name": "Set Fields",
  "type": "n8n-nodes-base.set",
  "typeVersion": 3,
  "parameters": {
    "keepOnlySet": false,
    "values": {
      "number": [{ "name": "year", "value": 2025 }],
      "string": [{ "name": "status", "value": "Processed" }]
    }
  }
}
```

#### IF Node (Conditional)
```json
{
  "name": "Check Status",
  "type": "n8n-nodes-base.if",
  "typeVersion": 2,
  "parameters": {
    "conditions": {
      "conditions": [{
        "leftValue": "={{ $json[\"status\"] }}",
        "rightValue": "success",
        "operator": {
          "type": "string",
          "operation": "equals"
        }
      }],
      "combinator": "and"
    }
  }
}
```

#### Switch Node
```json
{
  "name": "Route by Category",
  "type": "n8n-nodes-base.switch",
  "parameters": {
    "dataType": "string",
    "value1": "={{ $json[\"category\"] }}",
    "rules": {
      "rules": [
        { "operation": "equal", "value2": "support" },
        { "operation": "equal", "value2": "sales" }
      ]
    },
    "fallbackOutput": 2
  }
}
```

#### Merge Node
```json
{
  "name": "Merge on ID",
  "type": "n8n-nodes-base.merge",
  "parameters": {
    "mode": "mergeByKey",
    "propertyName": "id",
    "outputDataFrom": "both"
  }
}
```

### 5. API & HTTP INTEGRATIONS

#### HTTP Request (GET)
```json
{
  "name": "HTTP GET",
  "type": "n8n-nodes-base.httpRequest",
  "parameters": {
    "url": "https://api.example.com/data",
    "method": "GET",
    "responseFormat": "json",
    "queryParametersUi": {
      "parameter": [
        { "name": "q", "value": "search term" },
        { "name": "limit", "value": "10" }
      ]
    }
  }
}
```

#### HTTP Request (POST)
```json
{
  "name": "HTTP POST",
  "type": "n8n-nodes-base.httpRequest",
  "parameters": {
    "url": "https://api.example.com/posts",
    "method": "POST",
    "responseFormat": "json",
    "jsonParameters": true,
    "bodyParametersJson": {
      "title": "Hello World",
      "content": "Example post"
    }
  }
}
```

### 6. MAJOR INTEGRATIONS

#### Google Sheets
```json
{
  "name": "Append to Sheet",
  "type": "n8n-nodes-base.googleSheets",
  "typeVersion": 4,
  "parameters": {
    "operation": "append",
    "spreadsheetId": "1A2b3C4D5E6FgHiJkLMnoPQrstu",
    "sheetName": "Sheet1",
    "dataMode": "autoMap",
    "options": {
      "valueInputMode": "USER_ENTERED"
    }
  }
}
```

#### Google Calendar - Get Events
```json
{
  "operation": "getAll",
  "calendar": "primary",
  "start": "={{ $json.startDate }}",
  "end": "={{ $json.endDate }}"
}
```

#### Google Calendar - Create Event
```json
{
  "operation": "create",
  "calendar": "primary",
  "summary": "Meeting Title",
  "start": "2025-01-15 10:00:00",
  "end": "2025-01-15 11:00:00",
  "description": "Meeting description"
}
```

#### Airtable
```json
{
  "name": "Airtable",
  "type": "n8n-nodes-base.airtable",
  "parameters": {
    "operation": "append",
    "base": "YOUR_BASE_ID",
    "table": "YOUR_TABLE_NAME",
    "addAllFields": true
  }
}
```

#### PostgreSQL
```json
{
  "name": "PostgreSQL",
  "type": "n8n-nodes-base.postgres",
  "parameters": {
    "operation": "executeQuery",
    "query": "SELECT * FROM users WHERE id = {{ $json[\"user_id\"] }}"
  }
}
```

#### Slack - Send Message
```json
{
  "name": "Slack",
  "type": "n8n-nodes-base.slack",
  "parameters": {
    "resource": "message",
    "operation": "send",
    "channel": "C01234567",
    "text": "Hello from n8n!"
  }
}
```

#### Telegram - Send Message
```json
{
  "chatId": "={{ $json.message.chat.id }}",
  "text": "Your reply message here"
}
```

#### Telegram - Send File
```json
{
  "chatId": "={{ $json.chatId }}",
  "binaryData": true,
  "file": "data",
  "additionalFields": {
    "caption": "Here's your file"
  }
}
```

#### Notion - Query Database
```json
{
  "name": "Notion",
  "type": "n8n-nodes-base.notion",
  "parameters": {
    "resource": "databasePage",
    "operation": "getAll",
    "databaseId": "YOUR_DATABASE_ID",
    "options": {
      "filter": {
        "singleCondition": {
          "key": "Email|email",
          "condition": "equals",
          "emailValue": "={{ $json[\"email\"] }}"
        }
      }
    }
  }
}
```

#### GitHub - Create Issue
```json
{
  "name": "GitHub",
  "type": "n8n-nodes-base.github",
  "parameters": {
    "resource": "issue",
    "operation": "create",
    "owner": "username",
    "repository": "repo-name",
    "title": "Issue Title",
    "body": "Issue description"
  }
}
```

### 7. AI & LLM INTEGRATIONS

#### OpenAI Chat (GPT)
```json
{
  "name": "ChatGPT",
  "type": "n8n-nodes-langchain.lmChatOpenAi",
  "typeVersion": 2.2,
  "parameters": {
    "model": "gpt-4o",
    "temperature": 0.7,
    "maxTokens": 500,
    "systemPrompt": "You are a helpful assistant.",
    "userPrompt": "{{ $json.question }}"
  }
}
```

#### Embeddings (OpenAI)
```json
{
  "name": "Text to Vector",
  "type": "n8n-nodes-langchain.embeddingsOpenAi",
  "parameters": {
    "model": "text-embedding-ada-002",
    "text": "={{ $json[\"content\"] }}"
  }
}
```

#### Pinecone - Upsert Vectors
```json
{
  "operation": "upsert",
  "index": "your-index-name",
  "vectors": "={{ $json.vectors }}"
}
```

### 8. COMMON PATTERNS & BEST PRACTICES

#### Looping with Split in Batches
```json
{
  "name": "Batch Loop",
  "type": "n8n-nodes-base.splitInBatches",
  "parameters": {
    "batchSize": 10
  }
}
```

#### Error Handling
Add to any node parameters:
```json
{
  "continueOnFail": true
}
```

#### Stop and Error
```json
{
  "name": "Stop on Error",
  "type": "n8n-nodes-base.stopAndError",
  "parameters": {
    "message": "Workflow stopped due to validation failure"
  }
}
```

#### Item Lists - Split Array
```json
{
  "name": "Split Array",
  "type": "n8n-nodes-base.itemLists",
  "parameters": {
    "operation": "splitIntoItems",
    "property": "results"
  }
}
```

### 9. COMMON ISSUES & SOLUTIONS

#### LLM-Generated JSON Issues
1. **Quotation Marks**: Use double quotes for property names and strings
2. **Trailing Commas**: Avoid trailing commas after last elements
3. **Data Types**: Don't wrap numbers/booleans in quotes
4. **Case Sensitivity**: Match expected property name casing
5. **Validation**: Use JSON validators before deployment

#### AI Agent Output Parsing
```javascript
// Parse AI Agent string output to JSON
const outputStr = $json.output;
let parsedData;
try {
  parsedData = JSON.parse(outputStr);
  return { json: parsedData };
} catch (error) {
  return {
    json: {
      error: "Could not parse output",
      original: outputStr
    }
  };
}
```

#### Avoiding Template Errors with JSON Examples
Use a Code node to generate JSON examples:
```javascript
const example = {
  "data": [{ "field": "value" }]
};
return { json: { example: JSON.stringify(example) } };
```

#### Preserving Input Fields in AI Output
```javascript
// Merge original input with AI output
const originalId = $node["PreviousNode"].first().json.id;
const aiOutput = $json.output;
return {
  json: {
    id: originalId,
    aiResult: aiOutput
  }
};
```

### 10. STICKY NOTES FOR DOCUMENTATION

```json
{
  "name": "Sticky Note",
  "type": "n8n-nodes-base.stickyNote",
  "parameters": {
    "content": "## Section Title\n\nDescription here",
    "width": 300,
    "height": 200,
    "color": 4
  }
}
```

## Instructions

When this skill is invoked:

1. **Understand the Question**: Identify what specific n8n topic the user is asking about
2. **Provide Relevant Information**: Extract and present the most relevant knowledge from this knowledge base
3. **Give Examples**: Always include JSON code examples when applicable
4. **Be Practical**: Focus on actionable guidance and best practices
5. **Explain Nuances**: Highlight important details, gotchas, and common issues
6. **Offer Alternatives**: When multiple approaches exist, present options with pros/cons
7. **Reference Connections**: Explain how nodes connect and data flows between them

## Response Format

Structure your responses as:
1. **Direct Answer**: Start with the core answer to the question
2. **JSON Example**: Provide relevant code snippet(s)
3. **Explanation**: Explain key parameters and their purposes
4. **Best Practices**: Share tips and common pitfalls to avoid
5. **Related Topics**: Suggest related concepts if helpful

## Examples of Usage

**User**: "How do I set up an AI Agent with memory in n8n?"

**Response**: Provide AI Agent configuration, memory buffer setup, connection details, and best practices for system messages.

**User**: "Show me how to integrate Google Calendar"

**Response**: Provide Google Calendar node examples for both getting and creating events, explain date formats, and credential setup.

**User**: "What's the best way to loop through data in n8n?"

**Response**: Explain n8n's item-based processing, show Split in Batches, Item Lists, and Code node approaches with examples.
