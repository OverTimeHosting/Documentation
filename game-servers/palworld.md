# Palworld Server Hosting on OTH

> Complete guide to hosting Palworld dedicated servers with customization and player management

## Table of Contents

- [Overview](#overview)
- [System Requirements](#system-requirements)
- [Setup Instructions](#setup-instructions)
- [Configuration](#configuration)
- [Common Commands](#common-commands)
- [Server Management](#server-management)
- [Optimization](#optimization)
- [Troubleshooting](#troubleshooting)
- [Advanced Configuration](#advanced-configuration)

## Overview

OTH Palworld server hosting provides fully managed dedicated servers with extensive customization options, automatic backups, and comprehensive player management tools for this Pokemon-inspired creature collecting game.

### Features

- **Full Server Customization**: Adjust difficulty, spawn rates, and resource multipliers
- **Player Management**: Ban lists, whitelist, and admin controls
- **Automatic Backups**: Daily snapshots with full recovery options
- **Performance Monitoring**: Real-time metrics and server health tracking
- **Discord Integration**: Server status and event notifications
- **Cross-Platform Support**: PC dedicated servers
- **Web Console**: Remote management interface
- **Team System**: Guild/organization management
- **Custom Settings**: Fine-tune gameplay for your community
- **Economy Customization**: Adjust EXP, drops, and resource rates

## System Requirements

| Player Count | RAM    | CPU Cores | Storage | Bandwidth |
|--------------|--------|-----------|---------|-----------|
| 1-20         | 8GB    | 4         | 40GB    | 6Mbps     |
| 20-32        | 12GB   | 6         | 60GB    | 8Mbps     |
| 32-50        | 16GB   | 8         | 80GB    | 12Mbps    |
| 50+          | 20GB+  | 8+        | 100GB+  | 15Mbps+   |

### Recommended Configuration

**Small Group (20 players)**: 8GB RAM, 4 CPU cores, 40GB storage
**Medium Server (32 players)**: 12GB RAM, 6 CPU cores, 60GB storage
**Large Server (50+ players)**: 16GB+ RAM, 8 CPU cores, 80GB+ storage

## Setup Instructions

### Creating a Palworld Server

1. **Access OTH Dashboard**
   - Log in to your account
   - Navigate to "Game Servers"
   - Click "Create New Server"

2. **Select Palworld**
   - Choose Palworld from game list
   - Select preferred region
   - Confirm latest version

3. **Configure Server Details**
   ```
   Server Name: My Palworld Server
   Server Description: Fun Palworld Adventures
   Server Password: Optional (leave blank for public)
   Player Limit: 32 (1-32 available)
   Server Region: Select closest to players
   Public Listing: Enable/Disable
   ```

4. **Select Resources**
   ```
   RAM: 12GB (32 players)
   CPU: 6 cores
   Storage: 60GB
   Auto-scaling: Enabled
   ```

5. **Gameplay Settings**
   - Difficulty: Normal
   - Experience Rate: 1x (default)
   - Pal Drop Rate: 1x (default)
   - Capture Rate: 1x (default)

6. **Launch Server**
   - Complete payment
   - Server launches in 5-10 minutes
   - Share server details with players

### Connecting to Your Server

**For Private Server (Password Protected)**
1. Open Palworld
2. Click "Play"
3. Select "Dedicated Server"
4. Click "Create Dedicated Server"
5. Or input IP and password manually

**For Public Server (No Password)**
1. Open Palworld
2. Click "Play"
3. Browse Server List
4. Search your server name or IP
5. Click Join

## Configuration

### Main Configuration File

PalWorldSettings.ini - Main server configuration:

```ini
[/Script/Pal.PalGameWorldSettings]
; Server Settings
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Int,SettingName="Difficulty",IntValue=1)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Int,SettingName="Day Length Minutes",IntValue=72)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Exp Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Pal Damage Rate Decrease",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Pal Capture Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Element Damage Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Pal Spawn Interval Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Pal Appearance Rate",FloatValue=1.0)

; Gameplay Tuning
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Work Speed Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Player Damage Rate Decrease",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Stamina Decrease Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Auto HP Regen Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Auto Hp Regen Rate In Sleep",FloatValue=1.0)

; Resource Rates
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Damage To Friendly Disabled",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Build Object Damage Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Collection Drop Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingName="Collection Amount Rate",FloatValue=1.0)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Float,SettingValueType=Float,SettingName="Crop Growth Rate",FloatValue=1.0)

; Player Settings
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Int,SettingName="MaxPlayers",IntValue=32)
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=String,SettingName="Server Name",StringValue="My Palworld Server")
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=String,SettingName="Server Description",StringValue="Welcome to my server!")
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=String,SettingName="Admin Password",StringValue="")
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=String,SettingName="Server Password",StringValue="")
OptionSettings=(SettingContainerName="GameWorldOption",SettingValueType=Bool,SettingName="Enable Password",BoolValue=False)
```

### Configuration Parameters Explained

#### Difficulty Settings

```ini
; Difficulty Levels (0=Easy, 1=Normal, 2=Hard, 3=Nightmare)
OptionSettings=(SettingName="Difficulty",IntValue=1)
```

#### Experience & Economy Multipliers

```ini
; Experience Rate (1.0=normal, 2.0=2x faster leveling)
OptionSettings=(SettingName="Exp Rate",FloatValue=1.0)

; Pal Catch Rate (1.0=normal, 0.5=harder to catch, 2.0=easier)
OptionSettings=(SettingName="Pal Capture Rate",FloatValue=1.0)

; Work Speed (affects Pal work in base, 1.0=normal)
OptionSettings=(SettingName="Work Speed Rate",FloatValue=1.0)
```

#### Damage & Balance

```ini
; Damage to Pals (higher = more damage to pals, 1.0=normal)
OptionSettings=(SettingName="Pal Damage Rate Decrease",FloatValue=1.0)

; Damage to Player (higher = more damage to you, 1.0=normal)
OptionSettings=(SettingName="Player Damage Rate Decrease",FloatValue=1.0)

; Stamina Drain (1.0=normal drain rate)
OptionSettings=(SettingName="Stamina Decrease Rate",FloatValue=1.0)
```

#### Resource Rates

```ini
; Item Drop Rate from defeated Pals (1.0=normal)
OptionSettings=(SettingName="Pal Drop Rate",FloatValue=1.0)

; Resource Collection Amount (1.0=normal)
OptionSettings=(SettingName="Collection Amount Rate",FloatValue=1.0)

; Crop Growth (1.0=normal, higher=faster growth)
OptionSettings=(SettingName="Crop Growth Rate",FloatValue=1.0)
```

#### Spawning

```ini
; How often Pals spawn (1.0=normal)
OptionSettings=(SettingName="Pal Spawn Interval Rate",FloatValue=1.0)

; How common rare Pals are (1.0=normal)
OptionSettings=(SettingName="Pal Appearance Rate",FloatValue=1.0)
```

## Common Commands

### Admin Commands

Admin commands are executed via console or with admin password privileges:

```bash
# Server Control
/save                                    # Force save world
/shutdown <seconds>                      # Shutdown with warning
/broadcast "message"                     # Server-wide message

# Player Management
/players                                 # List online players
/kick <PlayerID>                         # Kick player
/ban <PlayerID>                          # Ban player
/unban <PlayerID>                        # Unban player
/banlist                                 # Show ban list

# Guild Management
/guild <PlayerID> <GuildID>              # Change guild
/guildinfo <GuildID>                     # Show guild info
```

### In-Game Hotkey Commands

With admin privileges enabled:

```bash
; Server Management
/help                                    # Show help
/status                                  # Server status
/online                                  # Show online players
/uptime                                  # Server uptime

; Map & Exploration
/teleport <X> <Y> <Z>                    # Teleport to location
/playertp <PlayerID>                     # Teleport to player
/tpall                                   # Teleport all to you

; Item Spawning
/give <ItemID> <Quantity>                # Spawn item
/giveplayer <PlayerID> <ItemID>          # Give item to player
```

## Server Management

### Player Management

**Banning Players**
1. Identify problematic player
2. Get PlayerID from /players command
3. Execute: `/ban <PlayerID>`
4. Player banned from server

**Whitelisting** (if enabled)
1. Enable whitelist in config
2. Add allowed PlayerIDs
3. Only whitelisted players can join

**Admin Assignment**
1. Use admin password to login
2. `/admin <PlayerID>` (if available)
3. Grant admin privileges

### Backup Management

**Automatic Backups**
- Daily at 3:00 AM UTC
- Stored for 30 days
- Automatic rotation

**Manual Backup**
1. OTH Dashboard > Your Server
2. Click "Backups"
3. Click "Create Backup Now"
4. Label with description

### Scheduling Resets

Configure in OTH Dashboard:

1. **Server Settings > Auto-Restart**
2. Select time (e.g., 6:00 AM UTC)
3. Set frequency (Daily, Weekly)
4. Enable auto-backup before restart

### Discord Integration

1. **Create Discord Webhook**
   - Create server and channel
   - Go to channel settings > Webhooks
   - Create webhook and copy URL

2. **Configure in OTH Dashboard**
   - Server Settings > Discord Webhook
   - Paste webhook URL
   - Select events to notify

3. **Events Notified**
   - Server status changes
   - Player joins/leaves
   - Server crashes
   - Backup creation

## Optimization

### Performance Tuning

#### Reduce CPU Usage

```ini
; Lower tick rate
OptionSettings=(SettingName="Pal Spawn Interval Rate",FloatValue=0.5)

; Reduce appearance rate
OptionSettings=(SettingName="Pal Appearance Rate",FloatValue=0.7)

; Reduce work speed
OptionSettings=(SettingName="Work Speed Rate",FloatValue=0.8)
```

#### Memory Optimization

```ini
; Limit concurrent Pals
OptionSettings=(SettingName="Max Guild Members",IntValue=20)

; Reduce base complexity
OptionSettings=(SettingName="Build Object Damage Rate",FloatValue=2.0)
```

#### Network Optimization

- Use region closest to players
- Monitor bandwidth in dashboard
- Reduce player count if necessary

### Best Practices

1. **Regular Backups**
   - Enable automatic daily backups
   - Create manual backups before major changes
   - Test backup restoration

2. **Monitor Resources**
   - Check CPU/RAM usage regularly
   - Alert when approaching limits
   - Upgrade resources as needed

3. **Player Management**
   - Monitor for problematic players
   - Enforce clear server rules
   - Ban cheaters quickly
   - Whitelist if moderation needed

4. **Server Maintenance**
   - Restart weekly for stability
   - Check logs for errors
   - Update server when patches release
   - Document configuration changes

## Troubleshooting

### Server Won't Start

**Issue**: Server fails to launch

**Solutions**:
1. Check available system resources
2. Verify configuration file syntax
3. Review startup logs in dashboard
4. Ensure sufficient disk space (need 100GB+)
5. Contact OTH support

### Players Can't Connect

**Issue**: Connection timeout or "Cannot join"

**Solutions**:
1. Verify server is running (dashboard status)
2. Check correct IP and port
3. Verify game version matches server
4. Check password is correct (if applicable)
5. Ensure not at player limit
6. Try direct IP connection vs. server list

### Performance Issues

**Issue**: Server lagging, frame drops, creatures freezing

**Solutions**:
1. Check CPU/RAM usage in dashboard
2. Reduce player count
3. Lower Pal spawn rates in config
4. Disable non-essential features
5. Reduce base complexity
6. Upgrade server resources

### Data Loss

**Issue**: Character/world data missing

**Solutions**:
1. Restore from automatic backup
2. Check backup in OTH dashboard
3. Use manual restore function
4. Contact OTH support for recovery

### Mod Compatibility Issues

**Issue**: Server crash or unexpected behavior

**Solutions**:
1. Verify mod compatibility with server version
2. Remove recently added mods
3. Test with mods disabled
4. Re-add mods one at a time
5. Review server logs for errors

## Advanced Configuration

### Difficulty Presets

**Casual Server** (Beginner-Friendly)
```ini
OptionSettings=(SettingName="Difficulty",IntValue=0)
OptionSettings=(SettingName="Pal Capture Rate",FloatValue=1.5)
OptionSettings=(SettingName="Exp Rate",FloatValue=1.5)
OptionSettings=(SettingName="Pal Damage Rate Decrease",FloatValue=1.5)
OptionSettings=(SettingName="Player Damage Rate Decrease",FloatValue=0.8)
OptionSettings=(SettingName="Collection Amount Rate",FloatValue=1.5)
```

**Hardcore Server** (Challenge Mode)
```ini
OptionSettings=(SettingName="Difficulty",IntValue=3)
OptionSettings=(SettingName="Pal Capture Rate",FloatValue=0.5)
OptionSettings=(SettingName="Exp Rate",FloatValue=0.8)
OptionSettings=(SettingName="Pal Damage Rate Decrease",FloatValue=0.5)
OptionSettings=(SettingName="Player Damage Rate Decrease",FloatValue=1.5)
OptionSettings=(SettingName="Collection Amount Rate",FloatValue=0.8)
```

**Balanced Server** (Standard Play)
```ini
OptionSettings=(SettingName="Difficulty",IntValue=1)
OptionSettings=(SettingName="Pal Capture Rate",FloatValue=1.0)
OptionSettings=(SettingName="Exp Rate",FloatValue=1.0)
OptionSettings=(SettingName="Pal Damage Rate Decrease",FloatValue=1.0)
OptionSettings=(SettingName="Player Damage Rate Decrease",FloatValue=1.0)
OptionSettings=(SettingName="Collection Amount Rate",FloatValue=1.0)
```

### Economy Customization

Control server economy through multipliers:

```ini
; Fast progression for casual players
OptionSettings=(SettingName="Exp Rate",FloatValue=2.0)
OptionSettings=(SettingName="Collection Amount Rate",FloatValue=2.0)
OptionSettings=(SettingName="Pal Drop Rate",FloatValue=1.5)

; Slow progression for hardcore
OptionSettings=(SettingName="Exp Rate",FloatValue=0.5)
OptionSettings=(SettingName="Collection Amount Rate",FloatValue=0.5)
OptionSettings=(SettingName="Pal Drop Rate",FloatValue=0.5)
```

### Guild System Configuration

If guild system enabled:

```ini
; Maximum guild members
OptionSettings=(SettingName="Max Guild Members",IntValue=30)

; Guild leveling speed
OptionSettings=(SettingName="Guild Level Up Rate",FloatValue=1.0)
```

## Related Documentation

- [OTH Game Servers Overview](./README.md)
- [Server Management API](../api/)
- [Troubleshooting Guide](../faq/)

## Support Resources

- OTH Dashboard Help Center
- Palworld Community: https://www.reddit.com/r/Palworld
- Steam Community: https://steamcommunity.com/app/1623730
- Official Wiki: https://palworld.wiki
- Email Support: support@oth.io

## Last Updated

2024-12-10 | Documentation v2.1.0
