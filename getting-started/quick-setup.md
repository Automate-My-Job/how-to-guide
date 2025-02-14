---
description: Quick setup guide for getting started with Automate-My-Job.com
---

# Quick Setup

After completing the [installation](installation.md), this guide will help you quickly set up your first automation environment.

## Initial Configuration

### 1. Account Setup

1. Launch Automate-My-Job.com
2. Click "Sign Up" or "Login"
3. Complete your profile:
   - Personal information
   - Organization details
   - Preferred settings

### 2. Workspace Configuration

1. Create a workspace:
   ```json
   {
     "name": "My Workspace",
     "type": "personal",
     "description": "My automation projects"
   }
   ```

2. Configure workspace settings:
   - Team members (if applicable)
   - Default project settings
   - Security preferences

## Environment Setup

### 1. Development Environment

1. Install recommended tools:
   - Code editor
   - Version control
   - Testing tools

2. Configure local environment:
   ```bash
   # Set up environment variables
   export AMJ_WORKSPACE="my-workspace"
   export AMJ_ENV="development"
   ```

### 2. API Access

1. Generate API keys:
   - Go to Settings > API
   - Create new API key
   - Save credentials securely

2. Test API access:
   ```bash
   curl -H "Authorization: Bearer YOUR_API_KEY" \
        https://api.automate-my-job.com/v1/test
   ```

## Verification Steps

1. Create a test project
2. Run the sample workflow
3. Check system logs
4. Verify notifications

## Next Steps

- [First Steps Guide](first-steps.md)
- [Create Your First Project](../basics/create-project.md)
- [Platform Overview](../basics/core-concepts.md)

## Troubleshooting

### Common Setup Issues

1. **API Connection Failed**
   - Check API key
   - Verify network connection
   - Confirm API endpoints

2. **Workspace Creation Failed**
   - Verify permissions
   - Check name uniqueness
   - Validate configuration

Need help? Contact [support](mailto:support@automate-my-job.com) 