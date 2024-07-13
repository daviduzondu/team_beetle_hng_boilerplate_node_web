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
- `POST /auth/change-password`: Reset user password

## Users
- `GET /users`: List users
- `POST /users`: Create a new user
- `GET /users/{userId}`: Get user details
- `PUT /users/{userId}`: Update user details
- `DELETE /users/{userId}`: Delete a user
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

### Settings
- `GET /settings`: Get user settings
- `PUT /settings`: Update user settings

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

