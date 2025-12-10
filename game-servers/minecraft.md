# Minecraft Server Hosting Guide

> Complete guide to hosting both Java and Bedrock Edition Minecraft servers on OTH

## Table of Contents

- [Minecraft Java Edition](#minecraft-java-edition)
- [Minecraft Bedrock Edition](#minecraft-bedrock-edition)
- [Server Types Comparison](#server-types-comparison)
- [Configuration Reference](#configuration-reference)
- [Plugin Management](#plugin-management)
- [Common Commands](#common-commands)
- [Troubleshooting](#troubleshooting)
- [Performance Optimization](#performance-optimization)

## Overview

Minecraft is one of the most popular games globally, and OTH provides full support for both Java and Bedrock editions. This guide covers setup, configuration, plugin installation, and optimization for both versions.

### Key Features

- **One-Click Deploy**: Get your server running in minutes
- **Full EULA Compliance**: Proper licensing and terms adherence
- **Plugin Support**: Bukkit, Spigot, Paper server types
- **Auto Backups**: Daily automatic world backups
- **World Import/Export**: Move worlds between servers
- **Performance Monitoring**: Real-time metrics and analytics

## Minecraft Java Edition

### Server Requirements

| Player Count | Recommended RAM | Recommended CPU | Storage |
|---|---|---|---|
| 1-5 | 2-3 GB | 1-2 cores | 10-20 GB |
| 6-15 | 4-6 GB | 2-4 cores | 20-40 GB |
| 16-30 | 8-12 GB | 4-8 cores | 40-100 GB |
| 30+ | 16+ GB | 8+ cores | 100+ GB |

Note: These are minimum recommendations. Actual requirements vary based on:
- Number of plugins/mods installed
- World complexity and size
- Rendering distance and view distance
- Server software (Paper > Spigot > Bukkit > Vanilla)

### Java Edition Setup

#### Step 1: Create Server in OTH Dashboard

1. Log in to [OTH Dashboard](https://oth.cloud/dashboard)
2. Click "Create New Server"
3. Select "Minecraft Java Edition"
4. Choose your server region (closest to your players)
5. Select player slot count:
   - Shared: 1-10 players, $2.99/month
   - Standard: 11-20 players, $5.99/month
   - Professional: 21-40 players, $11.99/month
   - Enterprise: 40+ players, custom pricing

#### Step 2: Configure Basic Settings

1. Enter server name (e.g., "MyAwesomeServer")
2. Set Game Mode:
   - Creative: Unlimited resources, building focus
   - Survival: Standard gameplay with resources
   - Adventure: Custom maps and experiences
   - Hardcore: Permadeath enabled
3. Select Difficulty:
   - Peaceful: No hostile mobs
   - Easy: Low damage from mobs
   - Normal: Standard difficulty
   - Hard: High damage, limited healing
4. Set World Type:
   - Default: Standard terrain generation
   - Flat: Flat world for building
   - Large Biomes: Larger biome areas
   - Amplified: Extreme terrain generation

#### Step 3: Select Server Software

Choose from available server software:

**Paper** (Recommended)
- Best performance and reliability
- Full plugin support
- Active community and updates
- Most popular choice

```
Benefits:
- 20-40% better performance than Spigot
- Async chunk loading
- Better mob AI optimization
- Regular updates and security patches
```

**Spigot**
- Good balance of features and performance
- Full plugin ecosystem
- Customizable configuration
- Smaller player count best

**Bukkit**
- Original plugin server
- Wide plugin compatibility
- Less maintenance and updates
- Suitable for small servers

**Vanilla**
- Official Minecraft server
- No plugins supported
- Highest resource usage
- Pure vanilla gameplay

#### Step 4: Deploy Server

1. Review configuration
2. Click "Deploy Server"
3. Wait for server to initialize (typically 2-5 minutes)
4. Receive server IP address and port
5. Share IP with players: `your-ip:25565`

#### Step 5: Initial Connection

1. Launch Minecraft Java Edition
2. Go to Multiplayer
3. Click "Add Server"
4. Enter server name and IP:port
5. Click "Done" and "Join Server"

### Server Properties Configuration

Access `server.properties` through OTH dashboard:

```properties
# Server Settings
server-name=MyAwesomeServer
server-port=25565
level-seed=                          # Random seed if blank
difficulty=normal                    # peaceful, easy, normal, hard
game-mode=0                         # 0=survival, 1=creative, 2=adventure, 3=spectator
max-players=20
view-distance=12                    # 3-32, lower = better performance
simulation-distance=10              # Chunk updates, 5-12 recommended

# World Settings
pvp=true                            # Player vs Player combat
spawn-protection=16                 # Protection around spawn
spawn-animals=true
spawn-monsters=true
spawn-npcs=true
online-mode=true                    # Verify player accounts

# Performance
max-tick-time=60000                 # Max time per tick (ms)
network-compression-threshold=256   # Compress packets over this size
entity-broadcast-range-percentage=100

# Other Settings
enable-rcon=true                    # Remote console access
rcon.port=25575
rcon.password=your-secure-password  # Change this!
motd=Welcome to MyAwesomeServer
allow-flight=false
allow-nether=true
allow-end=true
```

### Whitelist Configuration

Enable whitelist to restrict player access:

1. In OTH dashboard, go to "Server Settings"
2. Click "Whitelist" tab
3. Toggle "Enable Whitelist"
4. Click "Add Player"
5. Enter player username
6. Click "Add"

Players on whitelist can join; others are rejected.

To add whitelist via console:
```
/whitelist add PlayerName
/whitelist remove PlayerName
/whitelist list
/whitelist reload
```

## Minecraft Bedrock Edition

### Server Requirements

| Player Count | Recommended RAM | Recommended CPU | Storage |
|---|---|---|---|
| 1-4 | 1-2 GB | 1-2 cores | 10-20 GB |
| 5-10 | 2-4 GB | 2-4 cores | 20-40 GB |
| 10-20 | 4-8 GB | 4-8 cores | 40-100 GB |
| 20+ | 8+ GB | 8+ cores | 100+ GB |

Note: Bedrock requires less resources than Java Edition.

### Bedrock Edition Setup

#### Step 1: Create Bedrock Server

1. In OTH Dashboard, click "Create New Server"
2. Select "Minecraft Bedrock Edition"
3. Choose region (US-East, US-West, EU, Asia)
4. Select player slot count
5. Click "Create"

#### Step 2: Configure Bedrock Settings

Bedrock uses `server.properties` similar to Java:

```properties
# Server Identity
server-name=My Bedrock Server
gamemode=Survival                    # Survival, Creative, Adventure
difficulty=Normal                   # Peaceful, Easy, Normal, Hard
max-players=20

# World
level-name=Bedrock level
level-seed=                         # Leave blank for random
level-type=Default                  # Default, Flat, Limited, Old

# Network
server-port=19132
server-portv6=19133
ipv6=true

# Performance
tick-distance=4                     # 4-12, affects loading distance
max-threads=-1                      # -1 = auto detect

# Features
pvp=true
force-gamemode=false                # Force players to server gamemode
allow-cheats=false
enable-lan-visibility=true
```

#### Step 3: Cross-Platform Support

Bedrock supports cross-platform play:
- Windows 10/11
- Xbox One/Series X|S
- Nintendo Switch
- Mobile (iOS via Game Pass, Android)

Players on any platform can join your server.

#### Step 4: Connecting to Bedrock Server

**Windows 10+**
1. Open Minecraft Bedrock
2. Go to "Play"
3. Click "Servers"
4. Click "Add Server"
5. Enter server name and IP
6. Click "Add"

**Mobile**
1. Open Minecraft
2. Go to "Play"
3. Click "Servers"
4. Add server with IP
5. Join server

**Xbox**
1. Open Minecraft
2. Select "Play"
3. Choose "Servers"
4. Add server
5. Join

## Server Types Comparison

| Feature | Vanilla | Bukkit | Spigot | Paper |
|---|---|---|---|---|
| Plugins | No | Yes | Yes | Yes |
| Performance | Low | Medium | Good | Excellent |
| Updates | Frequent | Slow | Regular | Regular |
| Community | Huge | Medium | Large | Large |
| Customization | Limited | Good | Good | Excellent |
| Async | No | No | Limited | Yes |

### Which to Choose?

- **Vanilla**: Pure vanilla experience, no plugins
- **Bukkit**: Start with plugins, older setup
- **Spigot**: Good balance, stable plugins
- **Paper**: Best performance, modern features (recommended)

## Configuration Reference

### Game Rules

Configure game mechanics via commands in console:

```
/gamerule command-feedback true|false
/gamerule daylight-cycle true|false
/gamerule do-fire-tick true|false
/gamerule do-mob-spawning true|false
/gamerule do-tile-drops true|false
/gamerule keep-inventory true|false
/gamerule log-admin-commands true|false
/gamerule max-entity-cramming 24
/gamerule mob-griefing true|false
/gamerule natural-regeneration true|false
/gamerule pvp true|false
/gamerule random-tick-speed 3
/gamerule send-command-feedback true|false
```

### Server Settings

Common administrative settings:

```properties
# MOTD (Message of the Day)
motd=Welcome to our awesome server!

# PvP
pvp=true

# Difficulty
difficulty=normal

# Game Mode
game-mode=0

# Performance
view-distance=12
simulation-distance=10
max-tick-time=60000

# Online Mode (verify Mojang accounts)
online-mode=true

# Spawn Protection
spawn-protection=16

# Nether and End
allow-nether=true
allow-end=true

# Flight in Survival
allow-flight=false

# Command Blocks
enable-command-block=true

# RCON (Remote Console)
enable-rcon=true
rcon.port=25575
rcon.password=SecurePassword123!
```

## Plugin Management

### Installing Plugins

#### Paper Plugins

Paper uses modern plugin architecture. To install plugins:

1. Navigate to OTH Dashboard -> Your Server
2. Go to "Mods & Plugins" section
3. Search for desired plugin (e.g., "EssentialsX")
4. Click "Install"
5. Server restarts automatically
6. Plugin is active

Popular Paper plugins:

- **EssentialsX**: Core commands, homes, warps
- **LiteBans**: Player bans and moderation
- **WorldEdit**: Terrain and structure editing
- **WorldGuard**: Region protection
- **Vault**: Permission and economy management
- **PlaceholderAPI**: Variable support for other plugins
- **Citizens**: NPC creation
- **Shopkeepers**: Easy shop creation

#### Spigot/Bukkit Plugins

Process similar to Paper:

1. OTH Dashboard -> Plugins
2. Search for plugin
3. Install and restart

Popular Spigot plugins:

- **EssentialsX**: Essential commands
- **PermissionsEx**: Permission management
- **Multiverse**: Multiple world management
- **CommandHelper**: Script-like commands
- **GriefPrevention**: Claim protection
- **Vault**: Economy and permission API

### Plugin Configuration

After installation, configure plugins via:

1. In-game commands (e.g., `/essentials help`)
2. Configuration files (OTH Dashboard -> Server Files)
3. Admin panel (some plugins)

Example EssentialsX configuration path:
```
/plugins/Essentials/config.yml
```

Edit via OTH Dashboard file manager.

### Removing Plugins

1. In OTH Dashboard, go to "Mods & Plugins"
2. Find installed plugin
3. Click "Uninstall"
4. Server restarts
5. Plugin is removed

## Common Commands

### Server Administration

```
# Server Information
/seed                              # Show world seed
/difficulty <level>                # Change difficulty
/time set <time>                   # Set time of day
/weather <clear|rain|thunder>      # Change weather
/gamerule <rule> <value>          # Set game rule

# Player Management
/kick <player> <reason>            # Kick player
/ban <player> <reason>             # Ban player
/banlist                           # List banned players
/unban <player>                    # Unban player
/op <player>                       # Make player operator
/deop <player>                     # Remove operator
/whitelist add <player>            # Add to whitelist
/whitelist remove <player>         # Remove from whitelist

# World Management
/save-all                          # Save world
/save-off                          # Disable auto-save
/save-on                           # Enable auto-save
/stop                              # Graceful shutdown
/reload                            # Reload configurations

# Teleportation
/tp <player> <x> <y> <z>         # Teleport player
/spawnpoint <player> <x> <y> <z> # Set spawn point
/setworldspawn <x> <y> <z>       # Set world spawn

# Spawn/Entity
/give <player> <item> <amount>     # Give item
/kill <player>                     # Kill player
/summon <entity> <x> <y> <z>     # Summon entity
```

### Essential Server Commands

```
# From EssentialsX plugin
/home                              # Go to home
/sethome                           # Set home
/tpa <player>                      # Request teleport
/tpaccept                          # Accept teleport request
/spawn                             # Go to spawn
/back                              # Return to previous location
/afk                               # Set AFK status
/msg <player> <message>            # Send private message

# Administration
/mute <player>                     # Mute player
/unmute <player>                   # Unmute player
/warn <player> <reason>            # Warn player
/tempban <player> <time> <reason> # Temporary ban
```

### WorldGuard Commands (Region Protection)

```
/wg region claim <region>          # Claim region
/wg region info <region>           # Show region info
/wg region remove <region>         # Delete region
/wg region addmember <region> <player> # Add member
/wg region removemember <region> <player> # Remove member
/wg flag <region> <flag> <value>  # Set region flag
```

## Troubleshooting

### Server Won't Start

**Symptom**: Server shows "Starting" but never goes online

**Solutions**:
1. Check server logs in OTH Dashboard
2. Look for port conflicts (25565 already in use)
3. Verify sufficient RAM allocated
4. Check for plugin errors in console
5. Restart server via dashboard

**Log Location**: OTH Dashboard -> Server Logs

### Players Getting Kicked with "Out of Memory"

**Symptom**: Random players disconnect with memory error

**Solutions**:
1. Increase allocated RAM
   - OTH Dashboard -> Server Settings -> Memory
   - Increase by 1-2 GB
2. Reduce view-distance
   - Change in server.properties: `view-distance=10`
3. Disable unnecessary plugins
4. Reduce player count
5. Clear old entity data

### High Ping/Lag

**Symptom**: Players report latency issues

**Solutions**:
1. Check if geographically close to server region
2. Verify network connection quality
3. Reduce render distance:
   - server.properties: `view-distance=10`
4. Disable mob AI during off-peak:
   - `/gamerule doMobSpawning false`
5. Update plugins to latest version
6. Upgrade server specifications

### Plugins Not Loading

**Symptom**: Installed plugins don't appear in-game

**Solutions**:
1. Verify plugin installed successfully
2. Check server logs for errors
3. Restart server via dashboard
4. Verify plugin compatibility with server version
5. Remove and reinstall plugin
6. Check plugin dependencies

### World Corruption

**Symptom**: World doesn't load or has errors

**Solutions**:
1. Restore from automatic backup
   - OTH Dashboard -> Backups tab
   - Select date and restore
2. Try regenerating corrupted region
3. Use WorldEdit to fix chunk issues
4. Contact OTH support if unresolvable

### Mod/Plugin Conflicts

**Symptom**: Crash loop or unexpected behavior

**Solutions**:
1. Check error logs in console
2. Disable plugins one at a time
3. Test each plugin independently
4. Check plugin compatibility
5. Update plugins to latest version
6. Consult plugin documentation

## Performance Optimization

### Essential Optimizations

#### 1. View Distance Configuration

```properties
# Lower = Better performance, less detail
# Recommended: 8-12
view-distance=10
simulation-distance=8
```

Impact: Each +1 = ~20% more CPU usage

#### 2. Disable Unnecessary Mob Spawning

```
/gamerule doMobSpawning false
/gamerule doTileDrops false
/gamerule doFireTick false
```

Or in server.properties:
```properties
spawn-monsters=false
spawn-animals=false
spawn-npcs=false
```

#### 3. Plugin Optimization

- Keep plugins updated
- Remove unused plugins
- Use lightweight alternatives:
  - Replace old plugins with modern versions
  - Example: EssentialsX instead of EssentialsX + 5 other plugins

#### 4. Entity Limit Configuration

```properties
max-entity-cramming=24
```

Lower value = fewer entity collisions

#### 5. Async Chunk Loading

Paper automatically does this. Spigot requires:
- Disable during load: `save-off`
- Use Paper for best performance

### Advanced Optimizations

#### Chunk Loading

For Paper servers in spigot.yml:
```yaml
chunk-loading:
  static-delay: 20
  dynamic-delay: 20
  dynamic-range: 2
```

#### Network Optimization

```properties
network-compression-threshold=256
```

Compress packets over this size (bytes).

#### Ticking Configuration

```properties
max-tick-time=60000
```

Maximum milliseconds per tick. Lower = more responsive.

### RAM Allocation Guidelines

| Player Count | Minimum | Recommended | Optimal |
|---|---|---|---|
| 1-5 | 1 GB | 2 GB | 3 GB |
| 6-10 | 2 GB | 3 GB | 4 GB |
| 11-20 | 4 GB | 6 GB | 8 GB |
| 21-40 | 8 GB | 12 GB | 16 GB |
| 40+ | 16+ GB | 32+ GB | 48+ GB |

Increase in 1-2 GB increments as player count grows.

### CPU Performance Tips

1. **Reduce tick rate**: Increase `max-tick-time` for lower CPU
2. **Paper over Spigot**: 30-40% better performance
3. **Disable unnecessary AI**: `/gamerule doMobSpawning false`
4. **Limit hopper activity**: Reduce clock mechanisms
5. **Disable redstone dust**: If excessive

### Storage Optimization

- **World size**: Average is 500MB - 2GB per player
- **Backups**: Daily backups use 1x world size
- **Logs**: Rotate logs monthly
- **Delete old backups**: Keep last 30 days only

Estimate storage:
```
Base: 50 GB
Per 10 players: +100 MB/day
Backups: Keep 30 days = 1x world size
Total: 50 GB + (players * 10 MB) + world size
```

## Backing Up and Restoring

### Automatic Backups

OTH creates automatic backups:
- **Daily**: Every 24 hours
- **Retention**: 30 days
- **Location**: Automatic, no action needed

### Manual Backups

1. In OTH Dashboard -> Backups
2. Click "Create Manual Backup"
3. Enter description (optional)
4. Wait for completion
5. Backup appears in list

### Restoring from Backup

1. Go to Backups tab
2. Find desired backup
3. Click "Restore"
4. Confirm restoration
5. Server restarts
6. World is restored

Warning: This overwrites current world data.

## Version Information

Last Updated: December 2024
Minecraft Version: 1.20.x
Documentation Version: 2.0.0

## Related Documentation

- [Game Server README](./README.md)
- [Performance Optimization Guide](./performance-guide.md)
- [Plugin Directory](./plugins/README.md)
- [Network Configuration](./network-configuration.md)

## Support

For additional help:
- OTH Support: support@oth.cloud
- Community Discord: https://discord.gg/oth
- Wiki: https://wiki.oth.cloud/minecraft

---

Happy hosting!
