# Authentication API

Endpoints for user authentication and session management.

## Login

Authenticate a user and receive an access token.

```http
POST /v1/auth/login
```

### Request Body

```json
{
  "email": "user@example.com",
  "password": "your-password"
}
```

### Response

```json
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIs...",
    "user": {
      "id": 1,
      "email": "user@example.com",
      "name": "John Doe",
      "role": "user"
    },
    "expires_at": "2025-01-10T12:00:00Z"
  }
}
```

## Register

Create a new user account.

```http
POST /v1/auth/register
```

### Request Body

```json
{
  "name": "John Doe",
  "email": "user@example.com",
  "password": "secure-password",
  "password_confirmation": "secure-password"
}
```

### Response

```json
{
  "success": true,
  "data": {
    "user": {
      "id": 1,
      "email": "user@example.com",
      "name": "John Doe"
    },
    "message": "Please verify your email address"
  }
}
```

## Logout

Invalidate the current session.

```http
POST /v1/auth/logout
```

### Headers

```
Authorization: Bearer YOUR_TOKEN
```

### Response

```json
{
  "success": true,
  "message": "Successfully logged out"
}
```

## Get Current User

Retrieve the authenticated user's profile.

```http
GET /v1/auth/me
```

### Headers

```
Authorization: Bearer YOUR_TOKEN
```

### Response

```json
{
  "success": true,
  "data": {
    "id": 1,
    "name": "John Doe",
    "email": "user@example.com",
    "role": "user",
    "created_at": "2024-01-01T00:00:00Z"
  }
}
```
