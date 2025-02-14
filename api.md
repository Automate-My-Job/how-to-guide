---
layout: default
title: API Reference
---

# API Reference

TaskMaster AI provides a comprehensive REST API for integrating automation capabilities into your applications.

## Authentication

All API requests require authentication using your API key in the header:

```bash
Authorization: Bearer your_api_key_here
```

## Base URL

```
https://api.taskmaster.ai/v1
```

## Endpoints

### Workflows

#### List Workflows

```http
GET /workflows
```

Returns a list of all workflows in your account.

**Response**
```json
{
  "workflows": [
    {
      "id": "wf_123",
      "name": "Email Processing",
      "status": "active",
      "created_at": "2024-02-14T12:00:00Z"
    }
  ]
}
```

#### Create Workflow

```http
POST /workflows
```

**Request Body**
```json
{
  "name": "New Workflow",
  "trigger": {
    "type": "schedule",
    "cron": "0 9 * * *"
  },
  "actions": [
    {
      "type": "email_categorize",
      "config": {
        "categories": ["urgent", "follow-up"]
      }
    }
  ]
}
```

### Tasks

#### Get Task Status

```http
GET /tasks/{task_id}
```

Returns the current status of a task.

**Response**
```json
{
  "id": "task_123",
  "status": "completed",
  "result": {
    "category": "urgent",
    "confidence": 0.95
  }
}
```

## Rate Limits

- 1000 requests per minute for paid plans
- 100 requests per minute for free tier
- Burst limit: 50 requests per second

## Error Codes

| Code | Description |
|------|-------------|
| 401  | Invalid API key |
| 403  | Permission denied |
| 429  | Rate limit exceeded |
| 500  | Internal server error |

## SDKs

- [Node.js SDK](https://github.com/taskmaster/node-sdk)
- [Python SDK](https://github.com/taskmaster/python-sdk)
- [Ruby SDK](https://github.com/taskmaster/ruby-sdk) 