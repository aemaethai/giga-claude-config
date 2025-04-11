# Giga Claude Config

A configuration setup for running MCP (Multi-Cloud Platform) servers using Docker containers. This project provides a standardized way to run various service integrations including GitHub, Slack, and Okta.

## Prerequisites

- Docker installed and running on your system
- Valid API keys and tokens for the services you want to use

## Configuration

The project uses `claude_desktop_config.json` to manage MCP server configurations. Each service requires specific environment variables and credentials:

### GitHub MCP Server
- Requires a GitHub Personal Access Token
- Environment variable: `GITHUB_PERSONAL_ACCESS_TOKEN`

### Slack MCP Server
- Requires a Slack Bot Token and Team ID
- Environment variables:
  - `SLACK_BOT_TOKEN`
  - `SLACK_TEAM_ID`

### Okta MCP Server
- Requires Okta Organization URL and API Token
- Environment variables:
  - `OKTA_ORG_URL`
  - `OKTA_API_TOKEN`

## Usage

1. Replace the placeholder values in `claude_desktop_config.json` with your actual credentials:
   - `{{github-apikey}}` with your GitHub Personal Access Token
   - `{{xoxb-apikey}}` with your Slack Bot Token
   - `{{T01234567}}` with your Slack Team ID
   - `{{https://hostname.okta.com}}` with your Okta organization URL
   - `{{okta-apikey}}` with your Okta API Token

2. The MCP servers will automatically start when needed, running in Docker containers with the specified configurations.

## Security Notes

- Never commit your actual API keys or tokens to version control
- Keep your `claude_desktop_config.json` file secure and private
- Use environment variables or a secure secrets management system for production deployments

## Support

For issues or questions, please refer to the respective service documentation:
- [GitHub API Documentation](https://docs.github.com/en/rest)
- [Slack API Documentation](https://api.slack.com/)
- [Okta API Documentation](https://developer.okta.com/docs/api/)
