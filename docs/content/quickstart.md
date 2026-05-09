# Jewel Fleet Management API

A RESTful API for managing a travel company's fleet operations. Administrators manage vehicles, destinations, and journeys. Passengers browse schedules and book tickets. Drivers file post-journey reports.

## Base URL

The production API is available at:

`https://jewels-fleet-management-api.onrender.com`

## Authentication

All endpoints except `POST /api/auth/register` and `POST /api/auth/login` require a valid JWT token passed in the `Authorization` header using the Bearer scheme.

`Authorization: Bearer <your_token>`

Get your token by calling the register or login endpoint first. Tokens expire after 24 hours. Re-authenticate via the login endpoint to get a fresh token.

## Roles & Permissions

Every user account is assigned one of three roles at registration. The role determines which endpoints the user may access.

| Role | Access |
|---|---|
| `admin` | Full access to all endpoints |
| `driver` | Submit and view their own journey reports only |
| `user` | Browse journeys, book and cancel their own tickets only |

## Rate Limiting

All endpoints are rate-limited to 100 requests per 15-minute window per IP address. Exceeding this limit returns a `429 Too Many Requests` response.

## Error Format

General errors return a `message` string:

`{ "message": "Journey not found" }`

Validation errors return an `error` array, one entry per failed field:

`{ "error": ["\"email\" is required", "\"password\" must be at least 6 characters long"] }`
