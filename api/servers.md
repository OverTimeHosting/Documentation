# Servers API

Manage your game servers programmatically.

## List Servers

Get all servers for the authenticated user.

```http
GET /v1/servers
```

### Query Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `page` | integer | Page number (default: 1) |
| `limit` | integer | Items per page (default: 20) |
| `status` | string | Filter by status: `running`, `stopped`, `suspended` |

### Response

```json
{
  "success": true,
  "data": [
    {
      "id": "srv_abc123",
      "name": "My Minecraft Server",
      "game": "minecraft",
      "status": "running",
      "ip": "play.oth.gg",
      "port": 25565,
      "players": {
        "online": 5,
        "max": 20
      },
      "resources": {
        "ram": "4GB",
        "storage": "20GB",
        "cpu": "2 cores"
      }
    }
  ],
  "meta": {
    "page": 1,
    "total": 3
  }
}
```

## Get Server

Retrieve details for a specific server.

```http
GET /v1/servers/{server_id}
```

### Response

```json
{
  "success": true,
  "data": {
    "id": "srv_abc123",
    "name": "My Minecraft Server",
    "game": "minecraft",
    "version": "1.20.4",
    "status": "running",
    "ip": "play.oth.gg",
    "port": 25565,
    "created_at": "2024-01-01T00:00:00Z"
  }
}
```

## Start Server

Start a stopped server.

```http
POST /v1/servers/{server_id}/start
```

### Response

```json
{
  "success": true,
  "message": "Server is starting"
}
```

## Stop Server

Stop a running server.

```http
POST /v1/servers/{server_id}/stop
```

### Response

```json
{
  "success": true,
  "message": "Server is stopping"
}
```

## Restart Server

Restart a server.

```http
POST /v1/servers/{server_id}/restart
```

### Response

```json
{
  "success": true,
  "message": "Server is restarting"
}
```

## Send Command

Send a console command to the server.

```http
POST /v1/servers/{server_id}/command
```

### Request Body

```json
{
  "command": "say Hello everyone!"
}
```

### Response

```json
{
  "success": true,
  "message": "Command sent"
}
```
