# API Reference

The OTH API allows you to programmatically manage your services, billing, and more.

## Base URL

```
https://api.oth.com/v1
```

## Authentication

All API requests require authentication using an API key.

### Getting Your API Key

1. Go to **Account** > **API Keys**
2. Click **Generate New Key**
3. Copy and store your key securely

### Using Your API Key

Include your API key in the `Authorization` header:

```bash
curl -X GET "https://api.oth.com/v1/servers" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## Response Format

All responses are JSON:

```json
{
  "success": true,
  "data": { ... },
  "meta": {
    "page": 1,
    "total": 100
  }
}
```

## Error Handling

Errors return appropriate HTTP status codes:

| Code | Meaning |
|------|---------|
| 400 | Bad Request - Invalid parameters |
| 401 | Unauthorized - Invalid API key |
| 403 | Forbidden - Insufficient permissions |
| 404 | Not Found - Resource doesn't exist |
| 429 | Too Many Requests - Rate limited |
| 500 | Server Error - Something went wrong |

## Rate Limits

- **Standard**: 100 requests per minute
- **Pro**: 500 requests per minute
- **Enterprise**: Unlimited

## API Sections

- [Authentication](authentication) - Auth endpoints
- [Servers](servers) - Manage game servers
- [Billing](billing) - Invoices and payments
- [Webhooks](webhooks) - Event notifications
