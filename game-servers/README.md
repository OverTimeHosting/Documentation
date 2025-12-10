# Game Server Hosting on OTH

> Comprehensive guide to hosting and managing game servers on the OTH (Open Hosting) platform

## Overview

OTH provides enterprise-grade game server hosting solutions for popular games with automatic scaling, performance monitoring, and easy configuration management. Our platform supports both Java and Bedrock editions of Minecraft, Rust, Valheim, ARK: Survival Evolved, Palworld, and many other popular titles.

## Key Features

- **Automatic Scaling**: Dynamically adjust server resources based on player count
- **Global CDN**: Low-latency connections from multiple geographic regions
- **One-Click Installation**: Deploy servers in minutes, not hours
- **DDoS Protection**: Enterprise-grade security for all game servers
- **Backup & Recovery**: Automatic daily backups with point-in-time restoration
- **Performance Monitoring**: Real-time metrics and analytics
- **Plugin Management**: Easy installation and configuration of mods and plugins
- **Custom Domains**: Use your own domain name for player connections
- **Team Management**: Manage multiple servers and team members

## Supported Games

### Primary Support Tier

- **Minecraft Java Edition** - Full EULA compliance
- **Minecraft Bedrock Edition** - Cross-platform support
- **Rust** - Procedural map generation, oxide mods
- **Valheim** - Dedicated server support
- **ARK: Survival Evolved** - Single and cluster setups
- **Palworld** - Early access dedicated servers

### Additional Supported Titles

- Terraria
- Satisfactory
- Project Zomboid
- Core Keeper
- Stardew Valley
- 7 Days to Die
- And 50+ more titles

## Getting Started

### Quick Start (5 Minutes)

1. **Create an Account**: Sign up at OTH.cloud
2. **Choose a Game**: Select from our supported titles
3. **Configure Server**: Set name, game mode, world settings
4. **Deploy**: Click deploy and get your server IP
5. **Play**: Connect and start playing

### System Requirements

Before hosting a server, ensure you have:

- Valid OTH account
- Payment method on file
- Stable internet connection (for remote play)
- Game license (for most titles)
- 15 minutes setup time per server

## Pricing

All our game server packages include:

- Server hosting on enterprise hardware
- Automatic backups (daily)
- DDoS protection
- 99.9% uptime SLA
- 24/7 support

Pricing varies by game and player count. See individual game guides for details.

## Documentation Guide

Each game has its own comprehensive guide:

### Minecraft
- **Java Edition Guide**: [minecraft.md](./minecraft.md)
  - Server setup and configuration
  - Bukkit, Spigot, Paper server types
  - Plugin installation and management
  - Performance optimization

- **Bedrock Edition Guide**: [minecraft.md](./minecraft.md)
  - Windows Dedicated Server setup
  - Cross-platform support
  - Realm alternatives

### Other Games
- **Rust**: [rust.md](./rust.md) - Dedicated server setup, wipe scheduling, oxide mods
- **Valheim**: [valheim.md](./valheim.md) - World management, dedicated server configuration
- **ARK: Survival Evolved**: [ark.md](./ark.md) - Single player, cluster setup, mod management
- **Palworld**: [palworld.md](./palworld.md) - Dedicated server setup, configuration

## Common Tasks

### How to: Connect to Your Server

1. Launch your game
2. Navigate to "Multiplayer" or "Join Server"
3. Enter the server IP address provided in your OTH dashboard
4. Enter the port number (varies by game)
5. Click "Join Server" or "Connect"

### How to: Install Plugins/Mods

1. Log in to OTH dashboard
2. Navigate to your server
3. Go to "Mods & Plugins" section
4. Search for desired mod/plugin
5. Click "Install"
6. Server restarts automatically

### How to: Backup Your Server

1. In OTH dashboard, select your server
2. Click "Backups" tab
3. Click "Create Manual Backup"
4. Wait for backup to complete
5. Download or restore as needed

### How to: Manage Server Settings

1. Open OTH dashboard
2. Select your server
3. Click "Settings" tab
4. Modify desired settings
5. Click "Save Changes"
6. Server applies changes (may require restart)

### How to: Add Server Administrators

1. In OTH dashboard, go to "Team" section
2. Click "Invite Team Member"
3. Enter email address and select permission level
4. Send invitation
5. Member accepts and gains access

## Server Management

### Understanding Server Logs

All game servers produce logs available in the OTH dashboard:

- **Error Logs**: Display critical errors and issues
- **Console Output**: Full server console output
- **Performance Logs**: CPU, RAM, and network metrics
- **Player Activity**: Login/logout events and player actions

### Monitoring Server Health

Use the OTH dashboard to monitor:

- **CPU Usage**: Keep below 80% for stability
- **RAM Usage**: Allocate enough for player count
- **Network**: Monitor bandwidth for lag issues
- **Player Count**: Track concurrent players
- **TPS/FPS**: Server performance metrics

### Scheduled Maintenance

OTH provides automatic maintenance windows:

- **Daily**: Incremental backups at 2 AM UTC
- **Weekly**: Full backups every Sunday
- **Monthly**: Optimization and security updates

You can customize maintenance schedules in server settings.

## Security Best Practices

1. **Use Strong Passwords**: Change default admin passwords immediately
2. **Enable Whitelist**: Use whitelist feature for private servers
3. **Regular Backups**: Enable automatic daily backups
4. **Monitor Activity**: Review logs regularly for suspicious activity
5. **Keep Updated**: Install security patches when available
6. **Limit Admin Access**: Only grant admin to trusted team members

## Performance Optimization

### General Tips

1. **Adjust View Distance**: Lower for better performance
2. **Disable Unnecessary Features**: Turn off unused plugins/mods
3. **Monitor Player Count**: Adjust server specs if approaching limits
4. **Clean Old Data**: Remove unnecessary world data
5. **Optimize Plugins**: Keep plugins updated and remove duplicates

### Game-Specific Optimization

- See individual game guides for optimization tips
- Minecraft: Disable entity AI, chunk loading optimization
- Rust: Map size, entity decay settings
- Valheim: Location sync frequency, network optimization
- ARK: Dino spawn rates, rendering distance
- Palworld: Player spawn rates, server performance settings

## Troubleshooting

### Server Won't Start

1. Check server logs in OTH dashboard
2. Verify server has sufficient resources
3. Check for mod/plugin conflicts
4. Restart server via dashboard
5. Contact support if issue persists

### High Ping/Lag

1. Check network status in dashboard
2. Verify server location is geographically close
3. Reduce server render distance
4. Disable unnecessary mods/plugins
5. Upgrade server specs if needed

### Players Can't Connect

1. Verify server is running (check dashboard)
2. Confirm correct IP and port
3. Check firewall isn't blocking connection
4. Verify player count hasn't exceeded limit
5. Restart server

### Crashes or Freezes

1. Check error logs in dashboard
2. Look for mod/plugin conflicts
3. Verify sufficient RAM allocated
4. Update game and server software
5. Contact support with log file

## Support & Resources

### Getting Help

- **Documentation**: Browse our comprehensive guides
- **FAQ**: Common questions and answers
- **Support Tickets**: Submit issues through OTH dashboard
- **Community**: Join our Discord server
- **Status Page**: Check server status and uptime

### Important Links

- **OTH Dashboard**: https://oth.cloud/dashboard
- **Support Portal**: https://support.oth.cloud
- **Community Discord**: https://discord.gg/oth
- **Status Page**: https://status.oth.cloud
- **API Documentation**: https://docs.oth.cloud/api

## Billing & Subscription

### Payment Options

- Credit/Debit Card
- PayPal
- Cryptocurrency
- Enterprise invoicing

### Billing Cycle

- Monthly subscriptions renew automatically
- Downgrade or upgrade anytime
- Unused time is prorated
- Cancel anytime with no penalty

### Cost Optimization

1. Right-size your server based on actual player count
2. Use spot instances for testing/development
3. Bundle multiple game servers for discounts
4. Reserve instances for stable hosting rates
5. Monitor usage to identify optimization opportunities

## Version Information

Last Updated: December 2024
OTH Platform Version: 3.2.0
Documentation Version: 2.0.0

## Related Documentation

- [Getting Started Guide](../getting-started/README.md)
- [API Reference](../api/README.md)
- [Troubleshooting FAQ](../faq/README.md)
- [Network Configuration](./network-configuration.md)
- [Advanced Administration](./advanced-administration.md)

## License & Compliance

All documentation is provided under the OTH Terms of Service. Game servers must comply with game publisher requirements and EULAs.

For Minecraft servers, full EULA compliance is enforced. See individual game guides for specific compliance requirements.

---

**Need help?** Contact support@oth.cloud or visit our support portal.
