---
description: Understanding the structure of automation projects
---

# Project Structure

This guide explains the standard project structure in Automate-My-Job.com and best practices for organizing your automation projects.

## Overview

A typical project structure:

```
my-automation-project/
├── .amj/                    # Project configuration
│   ├── config.yaml         # Main configuration
│   ├── secrets.yaml        # Encrypted secrets
│   └── environment.yaml    # Environment variables
├── workflows/              # Workflow definitions
│   ├── main.yaml          # Main workflow
│   └── subtasks/          # Reusable subtasks
├── scripts/               # Custom scripts
│   ├── python/           # Python scripts
│   ├── javascript/       # JavaScript scripts
│   └── shell/           # Shell scripts
├── data/                 # Data directory
│   ├── input/           # Input data
│   ├── output/          # Output data
│   └── temp/            # Temporary files
├── tests/               # Test files
│   ├── unit/           # Unit tests
│   ├── integration/    # Integration tests
│   └── data/           # Test data
├── docs/                # Documentation
│   ├── workflows/      # Workflow documentation
│   └── api/            # API documentation
└── logs/               # Log files
```

## Configuration Files

### 1. Main Configuration (config.yaml)

```yaml
project:
  name: "My Automation Project"
  version: "1.0.0"
  description: "Project description"
  
settings:
  timeout: 3600
  retry_attempts: 3
  log_level: "info"
  
dependencies:
  python: "requirements.txt"
  node: "package.json"
```

### 2. Secrets Management (secrets.yaml)

```yaml
secrets:
  api_keys:
    service_a: "${ENCRYPTED}"
    service_b: "${ENCRYPTED}"
  
  credentials:
    database:
      username: "${ENCRYPTED}"
      password: "${ENCRYPTED}"
```

### 3. Environment Variables (environment.yaml)

```yaml
development:
  DATABASE_URL: "dev-db:5432"
  API_ENDPOINT: "https://dev-api.example.com"

production:
  DATABASE_URL: "prod-db:5432"
  API_ENDPOINT: "https://api.example.com"
```

## Workflow Organization

### 1. Main Workflow

```yaml
# workflows/main.yaml
name: "Main Process"
description: "Primary workflow"

imports:
  - subtasks/data_processing.yaml
  - subtasks/notification.yaml

workflow:
  tasks:
    - !include subtasks/data_processing.yaml
    - !include subtasks/notification.yaml
```

### 2. Subtasks

```yaml
# workflows/subtasks/data_processing.yaml
name: "Data Processing"
type: "subtask"

tasks:
  - name: "process"
    type: "python"
    script: "python/process_data.py"
```

## Script Management

### 1. Python Scripts

```python
# scripts/python/process_data.py
def process_data(input_data):
    """
    Process input data
    """
    # Implementation
    return processed_data
```

### 2. JavaScript Scripts

```javascript
// scripts/javascript/transform.js
function transformData(data) {
  // Implementation
  return transformedData;
}
```

## Data Management

### 1. Directory Structure

- **input/**: Raw data files
- **output/**: Processed results
- **temp/**: Temporary processing files

### 2. Data Handling

```yaml
data_management:
  retention:
    temp: "24h"
    output: "30d"
  backup:
    enabled: true
    frequency: "daily"
```

## Testing Framework

### 1. Test Organization

```
tests/
├── unit/
│   ├── test_processing.py
│   └── test_validation.py
├── integration/
│   ├── test_workflow.py
│   └── test_api.py
└── data/
    ├── sample_input.json
    └── expected_output.json
```

### 2. Test Configuration

```yaml
# tests/config.yaml
test_settings:
  environment: "test"
  database: "test_db"
  mocks:
    enabled: true
```

## Documentation

### 1. Structure

```
docs/
├── workflows/
│   ├── main.md
│   └── subtasks/
├── api/
│   ├── endpoints.md
│   └── schemas.md
└── README.md
```

### 2. Documentation Standards

- Use markdown format
- Include code examples
- Provide diagrams
- Keep updated

## Best Practices

1. **Organization**
   - Follow consistent naming
   - Group related files
   - Maintain clear hierarchy
   - Document structure

2. **Version Control**
   - Use .gitignore
   - Track configurations
   - Exclude secrets
   - Manage dependencies

3. **Security**
   - Encrypt secrets
   - Separate configurations
   - Control access
   - Audit changes

## Next Steps

- Learn about [Security & Permissions](security.md)
- Explore [Project Configuration](project-configuration.md)
- Review [Best Practices](best-practices.md)

## Resources

- [Project Templates](https://github.com/automate-my-job/templates)
- [Configuration Guide](project-configuration.md)
- [Security Guidelines](security.md) 