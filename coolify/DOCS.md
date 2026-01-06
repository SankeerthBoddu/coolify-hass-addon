# Home Assistant Add-on: Coolify

## Installation

Follow these steps to get the add-on installed on your system:

1. Navigate in your Home Assistant frontend to **Settings** → **Add-ons** → **Add-on store**.
2. Click the menu icon (⋮) in the top right corner and select **Repositories**.
3. Add this repository URL: `https://github.com/SankeerthBoddu/coolify-hass-addon`
4. Find the "Coolify" add-on in the store and click it.
5. Click on the "INSTALL" button.

## How to use

1. After installation, configure the add-on options as needed.
2. Start the add-on.
3. Check the add-on logs to ensure it started correctly.
4. Open the Web UI by clicking "OPEN WEB UI" or navigate to `http://your-home-assistant-ip:8000`.
5. Complete the initial Coolify setup wizard.

## Configuration

Add-on configuration:

```yaml
APP_URL: "http://homeassistant.local:8000"
APP_KEY: ""
PUSHER_APP_ID: "coolify"
PUSHER_APP_KEY: ""
PUSHER_APP_SECRET: ""
```

### Option: `APP_URL`

This is the URL where Coolify will be accessible. You should set this to your Home Assistant's IP address or hostname followed by port 8000.

Examples:
- `http://192.168.1.100:8000`
- `http://homeassistant.local:8000`

### Option: `APP_KEY`

The Laravel application encryption key. If left empty, a key will be automatically generated on first start and logged to the add-on logs.

### Option: `PUSHER_APP_ID`

The Pusher application ID used for real-time WebSocket communications. The default value "coolify" works fine for most installations.

### Option: `PUSHER_APP_KEY` / `PUSHER_APP_SECRET`

Credentials for the internal Pusher/Soketi WebSocket server. Leave empty to auto-generate.

## Network Configuration

The add-on runs in host network mode to allow full Docker access. The following ports are used:

- **8000**: Main Coolify web interface
- **6001**: WebSocket server for real-time updates
- **6002**: Terminal server for web-based terminal access

## Docker Access

This add-on requires full Docker API access to manage containers, images, and networks. It has been granted:

- `docker_api: true` - Access to Docker socket
- `privileged: true` - Required for Docker-in-Docker operations
- `full_access: true` - Full hardware access

## Backup

All Coolify data including the SQLite database is stored in the add-on's data directory, which is included in Home Assistant backups.

## Known Issues and Limitations

1. **Resource Usage**: Coolify can be resource-intensive. Ensure your Home Assistant host has adequate RAM and CPU.

2. **ARM Compatibility**: While the add-on supports aarch64, some Docker images you deploy through Coolify may not have ARM versions.

3. **SSL/TLS**: For secure access, configure a reverse proxy (like NGINX Proxy Manager) in front of Coolify.

## Troubleshooting

### Add-on won't start

Check the logs for error messages. Common issues:
- Port 8000 already in use
- Insufficient memory
- Docker socket not accessible

### Cannot connect to Web UI

1. Verify the add-on is running
2. Check if the port is open: `netstat -tuln | grep 8000`
3. Ensure your firewall allows connections to port 8000

### Database errors

If you encounter database issues, you can reset the database by:
1. Stopping the add-on
2. Accessing the add-on's data folder and removing `coolify.db`
3. Restarting the add-on

## Support

Got questions or found a bug?

- [Open an issue on GitHub](https://github.com/SankeerthBoddu/coolify-hass-addon/issues)
- [Coolify Discord](https://discord.gg/coolify)
- [Home Assistant Community Forum](https://community.home-assistant.io/)
