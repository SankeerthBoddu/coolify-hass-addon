# Coolify Add-on for Home Assistant

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg

## About

[Coolify](https://coolify.io/) is an open-source & self-hostable alternative to Heroku / Netlify / Vercel / etc. It helps you manage your servers, applications, and databases on your own hardware; you only need an SSH connection.

This add-on allows you to run Coolify directly on your Home Assistant instance, enabling you to:

- Deploy and manage Docker containers
- Host your own applications and services
- Manage databases
- Set up automatic deployments from Git repositories
- Monitor your services

## Installation

1. Click the Home Assistant My button below to add this repository to your Home Assistant instance:

   [![Add Repository](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FSankeerthBoddu%2Fcoolify-hass-addon)

   Or manually add this repository URL to your Home Assistant add-on store:
   ```
   https://github.com/SankeerthBoddu/coolify-hass-addon
   ```

2. Find "Coolify" in the add-on store and click "Install"
3. Configure the add-on (see Configuration section below)
4. Start the add-on
5. Access Coolify at `http://your-home-assistant-ip:8000`

## Configuration

```yaml
APP_URL: "http://homeassistant.local:8000"
APP_KEY: ""
PUSHER_APP_ID: "coolify"
PUSHER_APP_KEY: ""
PUSHER_APP_SECRET: ""
```

### Option: `APP_URL`

The URL where Coolify will be accessible. Update this to match your Home Assistant's IP address or hostname.

### Option: `APP_KEY`

Laravel application key. Leave empty to auto-generate on first start.

### Option: `PUSHER_APP_ID`

Pusher application ID for real-time updates. Default is "coolify".

### Option: `PUSHER_APP_KEY` / `PUSHER_APP_SECRET`

Pusher credentials. Leave empty to auto-generate on first start.

## Ports

The add-on uses the following ports:

| Port | Description |
|------|-------------|
| 8000 | Coolify Web UI |
| 6001 | Websocket for real-time updates |
| 6002 | Terminal access |

## Data Persistence

All Coolify data is stored in `/data` which is persisted across add-on restarts and updates.

## Requirements

- Home Assistant OS or Supervised installation
- At least 2GB of RAM available
- At least 10GB of free disk space (more recommended for Docker images)
- amd64 or aarch64 architecture

## Support

- [Coolify Documentation](https://coolify.io/docs)
- [Coolify GitHub](https://github.com/coollabsio/coolify)
- [Report issues](https://github.com/SankeerthBoddu/coolify-hass-addon/issues)

## License

MIT License - see [LICENSE](LICENSE) for details.
