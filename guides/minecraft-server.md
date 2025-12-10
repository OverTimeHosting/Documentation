# Setting Up a Minecraft Server

This guide walks you through creating and configuring a Minecraft server on OTH.

## Prerequisites

- An OTH account
- A payment method (or account balance)

## Step 1: Create the Server

1. Log in to your [OTH Dashboard](https://oth.com/dashboard)
2. Click **Services** > **Create New**
3. Select **Game Servers** > **Minecraft**

## Step 2: Choose Your Edition

| Edition | Description |
|---------|-------------|
| **Java Edition** | The original PC version, supports mods |
| **Bedrock Edition** | Cross-platform (Xbox, Mobile, Windows 10) |

## Step 3: Select a Plan

Choose based on your player count:

| Players | RAM | Recommended Plan |
|---------|-----|------------------|
| 1-10 | 2GB | Starter |
| 10-30 | 4GB | Standard |
| 30-50 | 8GB | Pro |
| 50+ | 16GB+ | Enterprise |

## Step 4: Configure Settings

```yaml
Server Name: My Awesome Server
Game Mode: Survival
Difficulty: Normal
Max Players: 20
Enable PvP: true
```

## Step 5: Deploy

Click **Deploy Server** and wait about 30 seconds for your server to be ready.

## Connecting to Your Server

Once deployed, you'll see your connection details:

```
Server Address: play.oth.gg:25565
```

In Minecraft:
1. Click **Multiplayer**
2. Click **Add Server**
3. Enter your server address
4. Click **Done** and connect!

## Next Steps

- [Install plugins](plugins) to add features
- [Configure server.properties](configuration) for advanced settings
- [Set up automatic backups](backups)

## Troubleshooting

### Can't connect to server?

1. Make sure the server is running (check dashboard)
2. Verify you're using the correct IP and port
3. Check if you're using the right Minecraft version

### Server crashing?

1. Check console logs in the control panel
2. Ensure you have enough RAM allocated
3. Remove any recently added plugins/mods
