# Giga Claude MCP Configuration

A Docker-based configuration for running Multi-Cloud Platform (MCP) servers that integrate with GitHub, Slack, Okta, and Google services. This project provides a standardized and containerized approach to managing service integrations.

## Quick Start

1. Clone this repository
2. Install Docker and Docker Compose
3. Configure your credentials in `claude_desktop_config.json`
4. Start the services as needed

## Prerequisites

- Docker 20.10.0 or higher
- Docker Compose 2.0.0 or higher (optional, for advanced configurations)
- Valid API keys and tokens for the services you want to use
- Git (for version control)

## Project Structure

```
.
├── README.md
└── claude_desktop_config.json
```

## Service Configurations

The project uses `claude_desktop_config.json` to manage MCP server configurations. Each service runs in its own Docker container with specific environment variables:

### GitHub MCP Server
- **Docker Image**: `ghcr.io/github/github-mcp-server`
- **Required Environment Variables**:
  - `GITHUB_PERSONAL_ACCESS_TOKEN`: Your GitHub Personal Access Token

### Slack MCP Server
- **Docker Image**: `mcp/slack`
- **Required Environment Variables**:
  - `SLACK_BOT_TOKEN`: Your Slack Bot Token
  - `SLACK_TEAM_ID`: Your Slack Team ID

### Okta MCP Server
- **Docker Image**: `okta-mcp-server`
- **Required Environment Variables**:
  - `OKTA_ORG_URL`: Your Okta organization URL
  - `OKTA_API_TOKEN`: Your Okta API Token

### Google MCP Server
- **Docker Image**: `google-mcp-server`
- **Required Environment Variables**:
  - `GOOGLE_CLIENT_ID`: Your Google OAuth Client ID
  - `GOOGLE_CLIENT_SECRET`: Your Google OAuth Client Secret
  - `GOOGLE_REDIRECT_URI`: Your OAuth redirect URI

## Configuration Setup

1. Edit `claude_desktop_config.json` and replace the placeholder values with your actual credentials:
   ```json
   {
     "mcpServers": {
       "github": {
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "your-github-token"
         }
       },
       "slack": {
         "env": {
           "SLACK_BOT_TOKEN": "your-slack-token",
           "SLACK_TEAM_ID": "your-team-id"
         }
       },
       "okta": {
         "env": {
           "OKTA_ORG_URL": "your-okta-url",
           "OKTA_API_TOKEN": "your-okta-token"
         }
       },
       "google": {
         "env": {
           "GOOGLE_CLIENT_ID": "your-client-id",
           "GOOGLE_CLIENT_SECRET": "your-client-secret",
           "GOOGLE_REDIRECT_URI": "your-redirect-uri"
         }
       }
     }
   }
   ```

2. The MCP servers will automatically start when needed, running in isolated Docker containers.

## Docker Container Management

Each service runs in a Docker container with the following characteristics:
- Interactive mode (`-i`)
- Automatic cleanup on exit (`--rm`)
- Environment variables passed through the `-e` flag
- Container removal after execution

### Container Health Checks

To verify your containers are running properly:
```bash
# Check running containers
docker ps

# View container logs
docker logs <container-id>

# Check container health
docker inspect <container-id>
```

## Security Best Practices

- **Never commit sensitive data**: Keep your `claude_desktop_config.json` file out of version control
- **Use environment variables**: For production deployments, consider using a secrets management system
- **Regular token rotation**: Implement a schedule for rotating your API tokens
- **Least privilege principle**: Use tokens with minimal required permissions
- **Network security**: Use Docker networks to isolate services
- **Volume management**: Use named volumes for persistent data

## Troubleshooting

If you encounter issues:
1. Verify Docker is running: `docker info`
2. Check container logs: `docker logs <container-id>`
3. Ensure all environment variables are properly set
4. Verify network connectivity for the services
5. Check Docker resource limits: `docker stats`
6. Verify service-specific requirements are met

### Common Issues

- **Container won't start**: Check Docker daemon status and resource limits
- **Connection issues**: Verify network settings and firewall rules
- **Authentication errors**: Validate API tokens and permissions
- **Resource constraints**: Monitor Docker resource usage

## Support and Documentation

For detailed API documentation and support:
- [GitHub API Documentation](https://docs.github.com/en/rest)
- [Slack API Documentation](https://api.slack.com/)
- [Okta API Documentation](https://developer.okta.com/docs/api/)
- [Google Cloud API Documentation](https://cloud.google.com/apis/docs)

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### Contribution Guidelines

- Follow the existing code style
- Add tests for new features
- Update documentation as needed
- Keep commits atomic and well-described

## Version Compatibility

| Service      | Minimum Version | Recommended Version |
|--------------|-----------------|---------------------|
| Docker       | 20.10.0         | 24.0.0              |
| GitHub MCP   | 1.0.0           | 2.0.0               |
| Slack MCP    | 1.0.0           | 1.5.0               |
| Okta MCP     | 1.0.0           | 1.3.0               |
| Google MCP   | 1.0.0           | 1.2.0               |

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Docker Community
- GitHub API Team
- Slack Developer Relations
- Okta Developer Experience Team
- Google Cloud Platform Team
