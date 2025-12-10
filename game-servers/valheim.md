# Valheim Server Hosting on OTH

> Complete guide to hosting Valheim dedicated servers on OTH with full mod support and world management

## Table of Contents

- [Overview](#overview)
- [System Requirements](#system-requirements)
- [Setup Instructions](#setup-instructions)
- [Configuration](#configuration)
- [Common Commands](#common-commands)
- [Mods & Plugins](#mods--plugins)
- [World Management](#world-management)
- [Optimization](#optimization)
- [Troubleshooting](#troubleshooting)
- [Advanced Configuration](#advanced-configuration)

## Overview

OTH Valheim server hosting provides fully managed dedicated servers with BepInEx modding support, automatic world backups, and comprehensive player management tools.

### Features

- **Full BepInEx Support**: Install and manage community mods
- **World Backup System**: Automatic daily backups with manual backup creation
- **Player Management**: Whitelist, ban list, and admin controls
- **Cross-Platform Support**: Windows and Linux dedicated servers
- **Performance Monitoring**: Real-time metrics and TPS tracking
- **Auto-Restart Scheduling**: Custom server restart schedules
- **Discord Integration**: Server status and event notifications
- **Port Management**: Automatic port assignment and forwarding
- **Multiple Worlds**: Run multiple worlds on single server
- **Mod Manager**: Easy mod installation and updates

## System Requirements

| Player Count | RAM    | CPU Cores | Storage | Bandwidth |
|--------------|--------|-----------|---------|-----------|
| 1-10         | 3GB    | 1-2       | 20GB    | 2Mbps     |
| 10-20        | 4GB    | 2         | 30GB    | 3Mbps     |
| 20-32        | 6GB    | 2-3       | 40GB    | 5Mbps     |
| 32-50        | 8GB    | 4         | 50GB    | 8Mbps     |
| 50+          | 12GB+  | 4+        | 70GB+   | 10Mbps+   |

### Recommended Configuration

**Small Group (10 players)**: 4GB RAM, 2 CPU cores, 30GB storage
**Medium Server (20-30 players)**: 6GB RAM, 3 CPU cores, 40GB storage
**Large Server (50+ players)**: 8-12GB RAM, 4 CPU cores, 50-70GB storage

## Setup Instructions

### Creating a Valheim Server

1. **Access OTH Dashboard**
   - Log in to your account
   - Navigate to "Game Servers"
   - Click "Create New Server"

2. **Select Valheim**
   - Choose Valheim from game list
   - Select preferred region
   - Confirm latest version

3. **Configure Server Details**
   ```
   Server Name: My Valheim Server
   Server Password: SecurePassword123
   World Name: Mistlands
   Player Limit: 10 (1-64 players)
   Modding Framework: BepInEx
   Region: Select closest to players
   ```

4. **Select Resources**
   ```
   RAM: 4GB (10 players), 6GB (20-30), 8GB (50+)
   CPU: 2 cores (10 players), 3-4 cores (30+)
   Storage: 30GB minimum, 50GB+ for mods
   ```

5. **Server Settings**
   - Enable password protection: YES
   - Enable auto-backups: YES
   - Discord webhook: [optional]
   - Auto-restart: Enable

6. **Launch Server**
   - Complete payment
   - Server launches in 3-5 minutes
   - Share server details with players

### Connecting to Your Server

1. **Get Server Details**
   - Check OTH dashboard
   - Record: IP Address, Port, Password

2. **Launch Valheim**
   - Open Steam, launch Valheim
   - Click "Start Game"

3. **Join Server**
   - Click "Join World"
   - Select "Community Server"
   - Enter server IP and password
   - Click "Join"

4. **Character Creation**
   - Create or select character
   - Spawn into world
   - Begin playing

## Configuration

### Server Configuration Files

Valheim server configuration is stored in multiple files:

#### startserver.sh (Linux)

```bash
#!/bin/bash
# Valheim Dedicated Server Start Script

# Server settings
export templdpath=/home/valheim/temp
export steamldpath=/home/valheim/steamcmd
export steamappid=896660

# Server parameters
/home/valheim/valheim_server/valheim_server.x86_64 \
  -nographics \
  -batchmode \
  -name "My Valheim Server" \
  -port 2456 \
  -world Mistlands \
  -password MyServerPassword123 \
  -public 1 \
  -saveinterval 1800 \
  -backups 4 \
  -backupshort 3600 \
  -logFile - \
  -updatemask 258
```

#### Server Parameters Explained

```bash
-name "Server Name"              # Server display name
-port 2456                       # Server port (2456-2458 auto)
-world "WorldName"               # World name (no spaces)
-password "Password"             # Server password
-public 1                        # Public server (1) or private (0)
-saveinterval 1800               # Auto-save interval (seconds)
-backups 4                       # Number of backups to keep
-backupshort 3600                # Short backup interval (seconds)
-logFile -                        # Log to stdout
-updatemask 258                  # Auto-update settings
```

#### World Configuration Files

Located in save game directory: `~/.config/unity3d/IronGate/Valheim/worlds/`

**worldname.db** - World data file
**worldname.fwl** - World file list
**playersexDB** - Player data

These are binary files, do not edit directly.

### Server Settings via Dashboard

1. **Open Server Settings**
   - OTH Dashboard > Your Server
   - Click "Settings"

2. **Configure Options**

```
Server Name: My Valheim Server
Server Password: SecurePassword123
Server Visibility: Public
World Name: Mistlands
Player Limit: 20
Auto-save Interval: 30 minutes
Backup Frequency: 4 per day
Auto-restart: Every 24 hours
Performance Mode: Balanced
```

### Advanced Configuration

Edit server startup parameters:

```bash
# Performance tuning
-logFile /var/log/valheim.log    # Custom log file
-updateRate 30                    # Update rate (ticks per second)

# Game rules (requires mods)
-diffficulty 0                    # Normal difficulty
-seasonalEventsEnabled 1          # Enable seasonal events
-ghostsEnabled 1                  # Enable ghosts
```

## Common Commands

### Admin Commands

Admin commands are executed through the server console or via RCON (requires BepInEx Admin mod).

```bash
# Player Management
listplayers                       # Show online players
ban playername                    # Ban player from server
unban playername                  # Unban player
kick playername [reason]          # Kick player from server
permit "Steam ID"                 # Add to permit list
revoke "Steam ID"                 # Remove from permit list

# Server Control
save                              # Force save world
restart                           # Restart server
shutdown                          # Shutdown server
```

### Chat Commands (with mods)

With Admin mod installed, players can use:

```bash
/help                             # Show available commands
/admin                            # Admin help
/status                           # Server status
/players                          # List players
```

### Mod-Specific Commands

**Better Chat** mod:
```bash
/whisper playername message       # Private message
/global message                   # Global announcement
/faction create name              # Create player faction
```

**Teleport** mod:
```bash
/portal list                      # List portals
/tp playername                    # Teleport to player
/home set                         # Set home location
/home                             # Teleport to home
```

## Mods & Plugins

### What is BepInEx?

BepInEx is a modding framework for Unity games that allows installation of community mods. Valheim uses BepInEx for its mod ecosystem.

### Installing Mods

1. **Download Mod**
   - Visit [Valheim Mods](https://www.nexusmods.com/valheim)
   - or [ThunderStore](https://valheim.thunderstore.io)
   - Download mod .zip file

2. **Upload to Server**
   - Use OTH dashboard file manager or FTP
   - Extract to `/BepInEx/plugins/` folder
   - Or upload with mod manager GUI

3. **Configure Mod** (if needed)
   - Edit config files if mod provides them
   - Located in `/BepInEx/config/`

4. **Restart Server**
   - Restart from OTH dashboard
   - Server loads mods on startup

### Essential Mods

#### Server Management

**Epic Management Console** - In-game server management
- Teleport players
- Spawn items
- Ban/kick players
- View player stats

Installation:
```
1. Download from Nexus Mods
2. Extract to /BepInEx/plugins/
3. Install dependencies
4. Restart server
```

**Valheim Plus** - Quality of life improvements
- Better building system
- Improved crafting
- Enhanced UI
- Performance optimizations

#### Gameplay Enhancement

**Common Sense** - Quality of life features
- Better building mechanics
- Improved item rotation
- Crafting queue system
- Tool durability improvements

**Crafty Carls** - Smithing enhancements
- Smithy improvements
- Tool upgrades
- New crafting recipes

**Teleporter** - Fast travel system
- Create portals
- Teleport between them
- Requires materials

#### Cosmetics & UI

**Seasons Mod** - Seasonal changes
- Winter, spring, summer, autumn
- Visual changes
- Modified difficulty
- Event scheduling

**Jötunn** - Mod creation framework
- Custom GUI
- Asset bundles
- Animation support

### Popular Modpack

**Valheim+ Modpack** combines essential mods:
- Valheim Plus (QoL)
- Epic Management Console
- Custom Raid System
- Trader
- Marketplace

Download from: https://valheim.thunderstore.io

### Creating Custom Mods

Advanced users can create custom mods:

```csharp
using BepInEx;
using Valheim.Net;

[BepInPlugin("com.example.myplugin", "My Plugin", "1.0.0")]
public class MyPlugin : BaseUnityPlugin
{
    void Awake()
    {
        Logger.LogInfo("My plugin loaded!");
    }

    void Update()
    {
        // Plugin logic here
    }
}
```

## World Management

### World Backup & Restore

**Automatic Backups**
- Daily at 3:00 AM UTC
- Stored for 30 days
- Automatic restoration on crash

**Manual Backup**

1. Open OTH Dashboard
2. Select your server
3. Click "Backups"
4. Click "Create Backup"
5. Name the backup
6. Use "Restore" to restore anytime

### World Reset

1. **Backup Current World**
   - Create manual backup first

2. **Reset World**
   - OTH Dashboard > Server Settings
   - Click "Reset World"
   - Select world from list or create new
   - Confirm

3. **Wait for Reset**
   - Server restarts
   - World files cleared
   - New world generated

### Transferring Worlds

1. **Download World Files**
   - Use FTP to connect
   - Navigate to `.config/unity3d/IronGate/Valheim/worlds/`
   - Download world.db and world.fwl files

2. **Upload to New Server**
   - Use FTP on new server
   - Upload files to worlds directory
   - Rename to match world name in config
   - Restart server

## Optimization

### Performance Tuning

#### Reduce CPU Usage

1. **Lower Player Limit**
   - Reduce from 32 to 20 if CPU-bound
   - Saves significant CPU
   - Improve performance for remaining players

2. **Adjust Save Interval**
   ```bash
   -saveinterval 3600              # Save every 1 hour (default 30 min)
   ```
   - Less frequent saves = lower CPU
   - Risk of data loss if crash occurs

3. **Reduce Backup Frequency**
   ```bash
   -backups 2                      # Keep 2 backups instead of 4
   -backupshort 7200               # Backup every 2 hours
   ```

#### Memory Optimization

1. **Disable Unnecessary Mods**
   - Remove cosmetic mods if not needed
   - Each mod uses memory
   - Monitor memory in dashboard

2. **Limit World Size**
   - Smaller worlds use less RAM
   - Generate smaller world during setup
   - Move to larger world later if needed

3. **Clear Old Data**
   - Remove unused character data
   - Clean old backup files
   - Delete unused mod files

### Network Optimization

1. **Adjust Update Rate**
   - Default is reasonable
   - Don't change unless experiencing lag
   - Higher = more network traffic

2. **Port Configuration**
   - Use default ports 2456-2458
   - Don't change unless necessary
   - Test connectivity after changes

### Mod Performance Impact

Monitor mod impact in logs:

```bash
# Check mod loading times
grep "Load" /var/log/valheim.log

# Monitor memory usage
free -h

# Monitor CPU
top -b -n 1 | grep valheim
```

## Troubleshooting

### Server Won't Start

**Issue**: Server fails to launch

**Solutions**:
1. Check system resources available
2. Review startup logs
3. Verify world name is valid
4. Ensure sufficient disk space (need 50GB+)
5. Contact OTH support

### Players Can't Connect

**Issue**: Connection timeout or "Cannot connect"

**Solutions**:
1. Verify server is running (dashboard status)
2. Check correct IP and port
3. Verify server password entered correctly
4. Ensure ports 2456-2458 are open
5. Check Steam servers online
6. Try direct connection vs. server list

**Connection String**:
```
IP:Port
Example: 192.168.1.100:2456
```

### Mods Not Loading

**Issue**: Mods don't appear or server crashes

**Solutions**:
1. Verify BepInEx installed correctly
2. Check mod compatibility with server version
3. Verify mod dependencies installed
4. Check mod config files for syntax errors
5. Review console logs for error messages
6. Try removing recently added mods

**Debug Process**:
1. Remove all custom mods
2. Restart server
3. Re-add mods one at a time
4. Test after each addition

### World Data Corruption

**Issue**: "Cannot load world" or missing data

**Solutions**:
1. Restore from automatic backup
   - OTH Dashboard > Backups
   - Select backup before corruption
   - Click "Restore"
2. Verify disk space not full
3. Check file system health
4. Contact OTH support for recovery

### Performance Issues

**Issue**: Lag, low FPS, or server stuttering

**Solutions**:
1. Reduce player count
2. Reduce mod count
3. Lower save interval (less frequent saves)
4. Check CPU/RAM in dashboard
5. Disable cosmetic mods
6. Reduce world size if possible
7. Upgrade server resources

### Network Lag

**Issue**: High ping or packet loss

**Solutions**:
1. Change server region closer to players
2. Check internet bandwidth
3. Monitor bandwidth usage dashboard
4. Reduce player count
5. Disable unnecessary mods
6. Contact OTH support

## Advanced Configuration

### Custom World Generation

1. **World Name**
   - Use descriptive name: "Mistlands", "Blackforest", etc.
   - No spaces in world name
   - World generates on first launch

2. **World Seed**
   - Valheim generates from world name hash
   - Same name = same world
   - Rename world = different generation

### Scheduled Restarts

1. **Configure in OTH Dashboard**
   - Server Settings > Auto-Restart
   - Select time (e.g., 6:00 AM UTC)
   - Frequency (Daily, Weekly)

2. **Startup Script**
   ```bash
   # Add to crontab for automatic restarts
   0 6 * * * /home/valheim/restart.sh
   ```

### Discord Integration

1. **Get Webhook URL**
   - Create Discord channel
   - Create webhook in channel settings
   - Copy webhook URL

2. **Configure in Dashboard**
   - Server Settings > Discord Webhook
   - Paste webhook URL
   - Select events to notify

3. **Events Notified**
   - Server started/stopped
   - Players joined/left
   - Server crashes
   - Backup created

### Multi-World Hosting

Run multiple worlds on same server:

1. **Create Multiple Worlds**
   - Each world needs own configuration
   - Separate ports: 2456, 2460, 2464, etc.
   - Separate passwords

2. **Server Hardware**
   - Scale resources appropriately
   - 4GB per 10 players per world
   - CPU cores for each world
   - Monitor total resource usage

## Related Documentation

- [OTH Game Servers Overview](./README.md)
- [Server Management API](../api/)
- [Troubleshooting Guide](../faq/)

## Support Resources

- OTH Dashboard Help Center
- Valheim Community: https://www.reddit.com/r/valheim
- Mod Resources: https://www.nexusmods.com/valheim
- Thunderstore: https://valheim.thunderstore.io
- Email Support: support@oth.io

## Last Updated

2024-12-10 | Documentation v2.1.0
