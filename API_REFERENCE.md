# API Reference

## Base URL

All API requests should be made to: `https://api.example.com/v1`

## Authentication

Most endpoints require authentication using a Bearer token. Include the token in the Authorization header:

## Endpoints

### Authentication

- `POST /auth/login`: Authenticate a user
- `POST /auth/register`: Register a new user
- `POST /auth/logout`: Log out a user
- `POST /auth/refresh`: Refresh an access token
- `POST /auth/forgot-password`: Request a password reset
- `POST /auth/reset-password`: Reset a user's password

### Users

- `GET /users`: List users
- `POST /users`: Create a new user
- `GET /users/{userId}`: Get user details
- `PUT /users/{userId}`: Update user details
- `DELETE /users/{userId}`: Delete a user
- `GET /users/{userId}/settings`: Get user settings
- `PUT /users/{userId}/settings`: Update user settings
- `GET /users/{userId}/export`: Export user data

### Organizations

- `GET /organizations`: List organizations
- `POST /organizations`: Create a new organization
- `GET /organizations/{orgId}`: Get organization details
- `PUT /organizations/{orgId}`: Update organization details
- `DELETE /organizations/{orgId}`: Delete an organization

### Payments

- `POST /payments`: Create a new payment
- `GET /payments/{paymentId}`: Get payment details
- `GET /payments`: List payments

### Messages

- `POST /messages`: Send a new message
- `GET /messages`: List messages
- `GET /messages/{messageId}`: Get message details

### Widgets

- `GET /widgets`: List widgets
- `POST /widgets`: Create a new widget
- `GET /widgets/{widgetId}`: Get widget details
- `PUT /widgets/{widgetId}`: Update widget details
- `DELETE /widgets/{widgetId}`: Delete a widget

### Blog

- `GET /blog`: List blog posts
- `POST /blog`: Create a new blog post
- `GET /blog/{postId}`: Get blog post details
- `PUT /blog/{postId}`: Update a blog post
- `DELETE /blog/{postId}`: Delete a blog post

### Notifications

- `GET /notifications`: List notifications
- `POST /notifications`: Create a new notification
- `PUT /notifications/{notificationId}/read`: Mark a notification as read

### Invites

- `POST /invites`: Create a new invite
- `GET /invites/{inviteId}`: Get invite details
- `POST /invites/{inviteId}/accept`: Accept an invite

### Email Templates

- `GET /email-templates`: List email templates
- `POST /email-templates`: Create a new email template
- `GET /email-templates/{templateId}`: Get email template details
- `PUT /email-templates/{templateId}`: Update an email template
- `DELETE /email-templates/{templateId}`: Delete an email template

### AI Integration

- `POST /ai/analyze`: Analyze data using AI
- `POST /ai/generate`: Generate content using AI

### Activity Log

- `GET /activity-log`: Get activity log
- `GET /activity-log/{userId}`: Get activity log for a specific user

## Common Parameters

### Pagination

Many list endpoints support pagination using the following query parameters:

- `page`: The page number (default: 1)
- `limit`: The number of items per page (default: 20, max: 100)

Example: `GET /users?page=2&limit=50`

### Sorting

Some list endpoints support sorting using the following query parameter:

- `sort`: The field to sort by, prefixed with `-` for descending order

Example: `GET /users?sort=-createdAt`

### Filtering

Some list endpoints support filtering using various query parameters. Refer to the specific endpoint documentation for available filters.

## Response Formats

All responses are returned in JSON format. Successful responses typically include the requested data, while error responses include an error message and sometimes additional details.

### Successful Response

```json
{
  "data": { ... },
  "meta": {
    "page": 1,
    "limit": 20,
    "totalCount": 100
  }
}