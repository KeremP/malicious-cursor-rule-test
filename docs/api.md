# API Documentation

## Overview
This document provides detailed information about the available API endpoints, request/response formats, and authentication requirements.

## Base URL
```
https://api.example.com/v1
```

## Authentication
All API requests require authentication using an API key. Include your API key in the request header:

```
Authorization: Bearer YOUR_API_KEY
```

## Rate Limiting
- 100 requests per minute
- 1000 requests per hour

## Endpoints

### Users

#### Get User Profile
```http
GET /users/{user_id}
```

**Parameters:**
- `user_id` (path parameter): The unique identifier of the user

**Response:**
```json
{
  "id": "string",
  "username": "string",
  "email": "string",
  "created_at": "string",
  "updated_at": "string"
}
```

#### Update User Profile
```http
PUT /users/{user_id}
```

**Parameters:**
- `user_id` (path parameter): The unique identifier of the user

**Request Body:**
```json
{
  "username": "string",
  "email": "string"
}
```

**Response:**
```json
{
  "id": "string",
  "username": "string",
  "email": "string",
  "updated_at": "string"
}
```

### Resources

#### List Resources
```http
GET /resources
```

**Query Parameters:**
- `page` (optional): Page number for pagination (default: 1)
- `limit` (optional): Number of items per page (default: 10)
- `sort` (optional): Sort field (default: "created_at")
- `order` (optional): Sort order ("asc" or "desc", default: "desc")

**Response:**
```json
{
  "data": [
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "created_at": "string"
    }
  ],
  "pagination": {
    "total": "number",
    "page": "number",
    "limit": "number",
    "pages": "number"
  }
}
```

#### Create Resource
```http
POST /resources
```

**Request Body:**
```json
{
  "name": "string",
  "description": "string"
}
```

**Response:**
```json
{
  "id": "string",
  "name": "string",
  "description": "string",
  "created_at": "string"
}
```

## Error Responses

All endpoints may return the following error responses:

### 400 Bad Request
```json
{
  "error": {
    "code": "BAD_REQUEST",
    "message": "Invalid request parameters"
  }
}
```

### 401 Unauthorized
```json
{
  "error": {
    "code": "UNAUTHORIZED",
    "message": "Invalid or missing API key"
  }
}
```

### 404 Not Found
```json
{
  "error": {
    "code": "NOT_FOUND",
    "message": "Resource not found"
  }
}
```

### 429 Too Many Requests
```json
{
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "Rate limit exceeded"
  }
}
```

### 500 Internal Server Error
```json
{
  "error": {
    "code": "INTERNAL_SERVER_ERROR",
    "message": "An unexpected error occurred"
  }
}
```

## Best Practices

1. Always include the API key in the Authorization header
2. Handle rate limiting by implementing exponential backoff
3. Cache responses when appropriate
4. Use HTTPS for all API requests
5. Implement proper error handling

## Support

For API support, please contact:
- Email: api-support@example.com
- Documentation: https://docs.example.com
- Status Page: https://status.example.com 