# Rust Server Hosting on OTH

> Complete guide to hosting Rust dedicated servers on OTH with full plugin and configuration support

## Table of Contents

- [Overview](#overview)
- [System Requirements](#system-requirements)
- [Setup Instructions](#setup-instructions)
- [Configuration](#configuration)
- [Common Commands](#common-commands)
- [Plugins & Oxide](#plugins--oxide)
- [Server Management](#server-management)
- [Optimization](#optimization)
- [Troubleshooting](#troubleshooting)
- [Advanced Topics](#advanced-topics)

## Overview

OTH Rust server hosting provides fully managed dedicated servers with Oxide modding framework, automatic wipe scheduling, and advanced player management tools.

### Features

- **Full Oxide Support**: Install and manage thousands of community mods
- **Plugin Ecosystem**: Pre-installed plugin manager with web interface
- **Automatic Wipes**: Schedule monthly, weekly, or custom wipe schedules
- **Team Management**: Built-in team system for admins and moderators
- **Backup System**: Regular snapshots with full recovery options
- **Performance Monitoring**: Real-time metrics and server health tracking
- **Web Console**: Remote RCON and player management
- **Discord Integration**: Automatic death/raid/wipe notifications
- **Anti-Cheat**: Built-in anti-cheat system with admin tools
- **Custom Maps**: Support for custom map sizes and seeds

## System Requirements

| Player Count | RAM    | CPU Cores | Storage | Bandwidth |
|--------------|--------|-----------|---------|-----------|
| 1-50         | 8GB    | 2         | 50GB    | 8Mbps     |
| 50-100       | 12GB   | 4         | 80GB    | 12Mbps    |
| 100-150      | 16GB   | 6         | 120GB   | 15Mbps    |
| 150-200      | 20GB   | 8         | 150GB   | 20Mbps    |
| 200+         | 24GB+  | 8+        | 200GB+  | 25Mbps+   |

### Minimum Requirements (10 players)

- RAM: 4GB minimum (8GB recommended)
- CPU: 2 cores minimum (4 recommended)
- Storage: 50GB minimum
- Bandwidth: 5Mbps minimum

## Setup Instructions

### Creating a Rust Server

1. **Access OTH Dashboard**
   - Log in to your OTH account
   - Navigate to "Game Servers"
   - Click "Create New Server"

2. **Select Rust**
   - Choose Rust from game list
   - Select preferred region
   - Confirm latest version

3. **Configure Server Details**
   ```
   Server Name: My Rust Server
   Player Slots: 100 (pick 50, 100, 150, 200, 250)
   Wipe Schedule: Monthly (first Thursday)
   Game Mode: Standard (PvP)
   Level Size: 3000x3000 (default)
   Seed: Random (or specify custom seed)
   Region: Select closest to players
   ```

4. **Select Resources**
   - RAM: 12GB (for 100 players)
   - CPU: 4 cores
   - Storage: 80GB
   - Auto-scale enabled

5. **Enable Features**
   - Oxide modding: YES
   - Auto-wipe scheduling: YES
   - Discord notifications: YES
   - Anti-cheat: YES

6. **Complete Setup**
   - Enter payment information
   - Launch server
   - Server online in 5-10 minutes

### Connecting to Your Server

1. **Find Server Address**
   - Check OTH dashboard
   - Server address: `game.server.address:28015`

2. **Launch Rust**
   - Open Steam and launch Rust
   - Click "Play"

3. **Find Your Server**
   - Click "Browse Community Servers"
   - Search server name or IP
   - Check "Official/Community Servers" and "Modded"

4. **Connect**
   - Click your server
   - Click "Join"
   - Wait for server to load

### Initial Configuration

After server launch:

1. **Login as Admin**
   - Connect to server
   - Use admin commands (see below)

2. **Set Permissions**
   - Add moderators
   - Set admin group
   - Configure permissions with plugins

3. **Configure Server**
   - Edit server.cfg file
   - Install essential plugins
   - Schedule backups

## Configuration

### Server Configuration (server.cfg)

The main server configuration file. Edit via OTH dashboard or FTP:

```cfg
# Server Identity
server.hostname "My Rust Server"
server.description "PvP Survival Server"
server.url "https://myserver.com"
server.headerimage "https://myserver.com/logo.png"
server.identity "rust_server_1"
server.seed 1234567890
server.worldsize 3000                        # World size 500-6000
server.maxplayers 100

# Server Port (do not change)
server.port 28015
server.queryport 28016
rcon.port 28017
rcon.web 1                                   # Enable web RCON

# Game Rules
server.pvp true                              # Enable PvP
server.pve false                             # PvE mode
server.radiation 1                           # Radiation on
decay.enabled 1                              # Building decay

# Performance
server.tickrate 30                           # Higher = better, more CPU
server.gc_interval 300
server.netcache_enabled 1

# Console
console.enabled 1
rcon.password "YourSecurePassword"           # Change this!

# Update checking
server.official false
steam.update_branch public                   # public, beta, next
```

### RCON Configuration

Enable remote console access:

```cfg
rcon.ip 0.0.0.0
rcon.port 28017
rcon.password "VerySecurePassword123"
rcon.web 1                                   # Enable web interface
```

Access web RCON:
```
http://your-server-ip:28017
```

### Server.cfg Rules

```cfg
# PvP & Gameplay
server.pvp true                              # Enable player vs player
server.radiation 1                           # Radiation damage
server.decay 1                               # Building decay
server.purge_enabled 0                       # Disable auto-purge
decay.scale 1.0                              # Decay speed multiplier

# Night/Weather
weather.enabled 1                            # Weather system
night.enabled 1                              # Day/night cycle
environment.itemdespawn 300                  # Item despawn time (seconds)
environment.spawndeltatime 0.5               # Spawn system timing

# Airdrops & Events
airdrop.enabled 1                            # Airdrops
airdrop.respawn_base_time 300                # Minimum time between drops
cargoship.enabled 1                          # Cargo ship events
heli.enabled 1                               # Helicopters

# Map Events
cargoship.npcspawner.fraction 0.1            # Probability of NPC
spawngroups.use_cached_spawngroups 1         # Cache spawns
monuments.enabled 1                          # Enable monuments
```

## Common Commands

### Admin Commands (requires admin status)

```bash
# Server Control
save                                         # Save server state
quit                                         # Shutdown server
restart 60                                   # Restart in 60 seconds

# Player Management
players                                      # List online players
ban playername                               # Ban player
unban playername                             # Unban player
banid steamid                                # Ban by Steam ID
unbanid steamid                              # Unban by Steam ID
banlist                                      # Show ban list
kick playername                              # Kick from server

# Permissions
ownerid steamid                              # Make server owner
moderatorid steamid                          # Make moderator
removemoderator steamid                      # Remove moderator
removeoowner steamid                         # Remove owner
ownerid                                      # List owners
moderatorid                                  # List moderators
```

### User Commands

```bash
# Information
help                                         # Show commands
time                                         # Show server time
fps                                          # Show FPS
ping                                         # Show ping

# Social
say "message"                                # Server-wide message
chat.say "message"                           # Chat message
notice.popup "message" "subtitle"            # Popup message
```

### Oxide Commands

```bash
# Plugin Management
plugins.load pluginname                      # Load plugin
plugins.unload pluginname                    # Unload plugin
plugins.reload pluginname                    # Reload plugin
plugin.list                                  # List installed plugins

# User Management (with plugins)
giveid steamid playername                    # Give steam ID
removeid steamid                             # Remove steam ID

# Permissions (with permission plugin)
permission.grant group playername permname   # Grant permission
permission.revoke group playername permname  # Revoke permission
```

## Plugins & Oxide

### What is Oxide?

Oxide is a modding framework for Rust that allows server administrators to install and manage community-created plugins. Plugins extend server functionality without modifying the core game.

### Installing Plugins

1. **Search for Plugin**
   - Visit [Oxide.io](https://oxide.io)
   - Find desired plugin
   - Check compatibility with your server version

2. **Download Plugin**
   - Download .cs file from Oxide.io
   - Or use plugin installer in OTH dashboard

3. **Upload to Server**
   - Use OTH dashboard file manager
   - Place in `oxide/plugins/` folder
   - Or use FTP: `/path/to/oxide/plugins/`

4. **Load Plugin**
   - Via console: `plugins.load pluginname`
   - Or restart server for auto-load
   - Check console for errors

5. **Configure Plugin**
   - Edit config in `oxide/config/pluginname/`
   - Reload plugin: `plugins.reload pluginname`

### Popular Plugins

#### Admin Tools

**ServerRewards** - Player reward and economy system
```bash
# Commands
/sr add player 100 100                       # Add points
/sr remove player 50                         # Remove points
/reward give player itemname                 # Give reward
```

**Players Extended** - Player information
```bash
# Commands
/players                                     # Show online players
/playerinfo playername                       # Get player info
```

**No Decay** - Disable building decay
```bash
# Config: oxide/config/NoDecay.json
{
  "Enabled": true,
  "DecayTickRate": 10
}
```

#### PvP & Balance

**Clans** - Player clan system
```bash
/clan create myclanupdated                   # Create clan
/clan invite playername                      # Invite player
/clan disband                                # Disband clan
```

**Teleportation** - Player teleport system
```bash
/home                                        # Go to home
/sethome                                     # Set home location
/tpa playername                              # Request teleport
/tpaccept                                    # Accept teleport
```

**Kits** - Give players items
```bash
/kit liststart                                # Show available kits
/kit kitname                                 # Claim kit
```

#### Protection & Security

**BetterChat** - Enhanced chat management
```bash
# Config: oxide/config/BetterChat.json
{
  "ChatPrefix": "[Server]",
  "MuteChatIfEmpty": false,
  "Clans": {
    "Enabled": true,
    "UseClanTag": true
  }
}
```

**AdminRadar** - Admin radar tool
```bash
/radar on                                    # Toggle radar
/radar solid                                 # Toggle walls
/radar animals                               # Toggle animals
```

**NoBlueprints** - Disable blueprints
```bash
# Config: oxide/config/NoBlueprints.json
{
  "Enabled": true,
  "NoBlueprints": true
}
```

### Plugin Configuration

Most plugins are configured via JSON files in `/oxide/config/`:

```json
{
  "Title": "Plugin Name",
  "Description": "What it does",
  "Author": "Author Name",
  "Version": "1.0.0",
  "Settings": {
    "Enabled": true,
    "Debug": false,
    "SomeOption": 100,
    "AnotherOption": "value"
  }
}
```

After editing config:
```bash
plugins.reload pluginname                    # Reload plugin
```

### Creating Custom Plugins

For advanced users, create custom Oxide plugins:

```csharp
using Oxide.Core;
using Oxide.Core.Plugins;

namespace Oxide.Plugins
{
    [Info("My Plugin", "Your Name", "1.0.0")]
    public class MyPlugin : RustPlugin
    {
        void Init()
        {
            Puts("Plugin initialized!");
        }

        [ChatCommand("mycommand")]
        void MyChatCommand(BasePlayer player, string command, string[] args)
        {
            player.ChatMessage("Hello from my plugin!");
        }
    }
}
```

## Server Management

### Scheduling Wipes

1. **Access OTH Dashboard**
   - Go to server settings
   - Select "Wipe Schedule"

2. **Set Wipe Schedule**
   ```
   Frequency: Monthly
   Day: First Thursday
   Time: 2:00 AM UTC
   Wipe Type: Full (map and blueprints)
   ```

3. **Notification**
   - Automatic Discord notification
   - Server warning 1 hour before wipe
   - Auto-backup before wipe

### Creating Backups

**Automatic Backups**
- Daily at 3:00 AM UTC
- Stored for 30 days
- Automatic rotation

**Manual Backup**
1. Open OTH dashboard
2. Click "Backups"
3. Click "Create Backup Now"
4. Label with description
5. Download or restore from here

### Team Management

**Add Admin/Moderator**
```bash
# Get Steam ID
# In console:
ownerid 76561198123456789                    # Add owner
moderatorid 76561198123456789                # Add moderator
```

**Create Admin Group** (with plugin)
```bash
permission.group.add admins                  # Create group
permission.grant group admins command.*      # Grant permissions
```

## Optimization

### Performance Tuning

#### Reduce CPU Usage

```cfg
# server.cfg
server.tickrate 20                           # Reduce from 30
server.netcache_enabled 0                    # Disable net cache
server.entityrate 30                         # Entity update rate
```

#### Memory Optimization

```cfg
# Decrease spawn rates
spawn.max_rate 0.5                           # Reduce spawns 50%
spawn.min_rate 0.1

# Optimize garbage collection
server.gc_interval 600                       # Run GC every 600 ticks
gc.buffer 256                                # Buffer size
```

#### Network Optimization

```cfg
# Reduce bandwidth usage
ent.tickrate_lod0 15                         # LOD0 tick rate
ent.tickrate_lod1 10                         # LOD1 tick rate
ent.tickrate_lod2 2                          # LOD2 tick rate
```

### Plugin Optimization

- **Load only necessary plugins**
- **Monitor plugin CPU usage**
- **Update plugins regularly**
- **Remove unused plugins**

Check plugin impact:
```bash
# In console, check plugin load times
plugins.info                                 # Show plugin details
```

### Map Optimization

- **Use default world size** (3000x3000) for 100 players
- **Reduce from 4000+ for small servers**
- **Increase to 4000+ for large servers**
- **Custom seeds can impact performance**

## Troubleshooting

### Server Won't Start

**Issue**: Server fails to launch

**Solutions**:
1. Check available system resources
2. Verify configuration file syntax
3. Review startup logs
4. Ensure no port conflicts
5. Contact OTH support if persists

### Players Can't Connect

**Issue**: Connection timeout or unable to find server

**Solutions**:
1. Verify server is running
2. Check correct IP and port
3. Verify ports 28015, 28016 are open
4. Check Steam servers are online
5. Ensure player isn't banned

### Plugin Errors

**Issue**: Plugins not loading or causing crashes

**Solutions**:
1. Check plugin compatibility with server version
2. Review console logs for errors
3. Try loading plugin individually
4. Check plugin config syntax
5. Reinstall plugin from latest source
6. Contact plugin author if issue persists

### Performance Issues (FPS/TPS)

**Issue**: Server lagging, low FPS

**Solutions**:
1. Reduce server tickrate to 20
2. Disable unnecessary plugins
3. Lower entity spawn rates
4. Reduce player slots
5. Monitor CPU usage in dashboard
6. Upgrade server resources

### Building Decay Issues

**Issue**: Buildings decaying too fast or not at all

**Solutions**:
1. Check decay settings in server.cfg
2. Install NoDecay plugin if desired
3. Adjust decay.scale multiplier
4. Verify building integrity
5. Check cupboard authorization

### Missing Items/Inventory Reset

**Issue**: Players lose items after wipe or crash

**Solutions**:
1. Restore from backup before wipe
2. Check automatic backup in dashboard
3. Verify no crashes in logs
4. Contact OTH support for recovery

## Advanced Topics

### Custom Maps

1. **Create Custom Map**
   - Use Rust map editor or tools
   - Save as .map file

2. **Upload to Server**
   - Use FTP to upload
   - Place in server directory

3. **Configure server.cfg**
   ```cfg
   server.level mymap                        # Load custom map
   server.seed 12345                         # Map seed
   server.worldsize 3000
   ```

4. **Restart Server**
   - Server loads custom map

### Custom Startup Arguments

Edit startup parameters in OTH dashboard:

```bash
-logfile logfile.log                         # Log file
+server.tickrate 30                          # Tick rate
+server.pvp true                             # PvP enabled
+decay.scale 1.0                             # Decay speed
```

### Event Scheduling

With plugins, schedule automatic events:

```csharp
// Example: Daily night hunt event
void ScheduleEvent()
{
    timer.Every(86400, () => {
        // Run event every 24 hours
        Server.Broadcast("Night Hunt starts in 30 minutes!");
    });
}
```

### Database Integration

Plugins can use SQLite for data storage:

```csharp
private Connection db;

void InitDB()
{
    db = new Connection("oxide/data/myplugin.db");
    db.ExecuteNonQuery(CREATE TABLE IF NOT EXISTS players...);
}
```

## Related Documentation

- [OTH Game Servers Overview](./README.md)
- [Server Management API](../api/)
- [FAQ & Common Issues](../faq/)

## Support Resources

- OTH Dashboard Help Center
- Oxide.io Plugin Repository: https://oxide.io
- Rust Dev Community: https://developer.valvesoftware.com/
- Email Support: support@oth.io

## Last Updated

2024-12-10 | Documentation v2.1.0
