---
description: Learn how to create and configure your first automation project
---

# Create Your First Project

This guide will walk you through creating your first automation project on Automate-My-Job.com. We'll cover project setup, configuration, and basic workflow creation.

## Prerequisites

Before starting, ensure you have:
- Completed the [installation](../getting-started/installation.md)
- Basic understanding of [core concepts](core-concepts.md)
- Required access permissions

## Creating a New Project

### 1. Project Setup

1. Open Automate-My-Job.com
2. Click "New Project" in the dashboard
3. Fill in the project details:
   ```json
   {
     "name": "My First Automation",
     "description": "A simple automation workflow",
     "team": "Personal",
     "visibility": "Private"
   }
   ```
4. Click "Create Project"

### 2. Project Configuration

#### Configure Environment

1. Navigate to "Project Settings"
2. Set up environment variables:
   ```yaml
   ENVIRONMENT: development
   LOG_LEVEL: debug
   MAX_RETRIES: 3
   ```
3. Configure execution settings:
   - Timeout duration
   - Retry policy
   - Notification preferences

#### Set Up Connections

1. Go to "Connections" tab
2. Add necessary integrations:
   - API endpoints
   - Database connections
   - File system paths

## Creating Your First Workflow

### 1. Design the Workflow

1. Open "Workflow Editor"
2. Add a trigger:
   ```yaml
   trigger:
     type: schedule
     schedule: "0 9 * * *"  # Run daily at 9 AM
   ```

### 2. Add Tasks

1. Drag and drop tasks from the sidebar
2. Configure each task:

```yaml
tasks:
  - name: fetch_data
    type: http_request
    config:
      url: "https://api.example.com/data"
      method: GET
      
  - name: process_data
    type: transform
    config:
      input: "${fetch_data.response}"
      operations:
        - filter: "status == 'active'"
        - sort: "date DESC"
        
  - name: save_results
    type: file_operation
    config:
      operation: write
      path: "/data/output/results.json"
      content: "${process_data.output}"
```

### 3. Configure Error Handling

Add error handling to your workflow:

```yaml
error_handling:
  retry:
    max_attempts: 3
    delay: 60
  fallback:
    task: notify_admin
    config:
      channel: email
      recipient: "${PROJECT_ADMIN}"
```

## Testing Your Project

### 1. Run Test Mode

1. Click "Test Mode" in the toolbar
2. Select test data sources
3. Run the workflow

### 2. Monitor Execution

1. Open "Monitoring" dashboard
2. Check:
   - Task status
   - Execution time
   - Resource usage
   - Error logs

### 3. Debug Issues

If you encounter problems:
1. Check the logs
2. Use step-by-step execution
3. Validate input/output data
4. Review error messages

## Best Practices

1. **Version Control**
   - Use meaningful commit messages
   - Document changes
   - Create branches for features

2. **Documentation**
   - Write clear task descriptions
   - Document dependencies
   - Maintain README files

3. **Testing**
   - Create test cases
   - Validate edge cases
   - Test error scenarios

## Next Steps

- Learn about [Project Configuration](project-configuration.md)
- Explore [Testing & Debugging](testing.md)
- Review [Best Practices](best-practices.md)

## Common Issues

### Project Creation Fails
- Check permissions
- Verify project name is unique
- Ensure all required fields are filled

### Workflow Errors
- Validate task configurations
- Check connection settings
- Review error logs

## Need Help?

- Visit [Community Forums](https://community.automate-my-job.com)
- Contact [Support](mailto:support@automate-my-job.com)
- Check [FAQs](faqs.md) 