# Discord Webhook Bot

A beautifully designed web application for sending custom messages to Discord channels through webhooks. Built with React, Express, and Discord's visual identity in mind.

## Overview

This application provides a simple, intuitive interface for Discord webhook management and message sending. Users can configure a Discord webhook URL, compose messages with custom usernames and avatars, and view their message history—all through a polished, Discord-themed UI.

## Features

### Current Features (MVP)
- **Webhook Configuration**: Save and manage Discord webhook URLs securely
- **Custom Message Composition**: 
  - Optional custom username override
  - Optional custom avatar URL
  - Live message preview with Discord-style formatting
  - Character counter (2000 character limit)
  - Clear form functionality
- **Message History**: View all sent messages with timestamps in Discord-style format
- **Beautiful UI**: Discord-themed design with blurple accent colors, smooth interactions, and responsive layout
- **Error Handling**: Comprehensive validation and user-friendly error messages
- **Loading States**: Visual feedback for all async operations

## Project Architecture

### Frontend
- **Framework**: React with TypeScript
- **Routing**: Wouter for client-side routing
- **State Management**: TanStack Query (React Query) for server state
- **Styling**: Tailwind CSS with custom Discord-themed design tokens
- **UI Components**: Shadcn UI component library
- **Forms**: React Hook Form with Zod validation

### Backend
- **Framework**: Express.js with TypeScript
- **Storage**: In-memory storage (MemStorage)
- **External API**: Axios for Discord webhook requests
- **Validation**: Zod schemas for type-safe API requests

### Data Models

#### Webhook
```typescript
{
  id: string;
  url: string;
  name: string | null;
}
```

#### Message
```typescript
{
  id: string;
  webhookId: string;
  content: string;
  username: string | null;
  avatarUrl: string | null;
  sentAt: Date;
}
```

## API Routes

### Webhook Management
- `GET /api/webhook` - Retrieve saved webhook configuration
- `POST /api/webhook` - Save new webhook URL (validates Discord URL format and connectivity)

### Message Management
- `GET /api/messages` - Get all sent messages (sorted by most recent)
- `POST /api/messages` - Send message to Discord and save to history

## How to Use

1. **Get a Discord Webhook URL**:
   - Go to your Discord server settings
   - Navigate to Integrations → Webhooks
   - Create a new webhook or copy an existing one
   - Copy the webhook URL

2. **Configure the Webhook**:
   - Paste your Discord webhook URL in the "Webhook Configuration" section
   - Click "Save Webhook"
   - You'll see a "Connected" badge when successful

3. **Send Messages**:
   - (Optional) Enter a custom username
   - (Optional) Enter a custom avatar URL
   - Type your message in the text area
   - Preview your message in real-time
   - Click "Send Message"

4. **View History**:
   - All sent messages appear in the "Message History" section
   - Messages are displayed in Discord-style format with timestamps

## Design System

The application follows a Discord-inspired design system:

- **Colors**: Discord blurple (#5865F2) as primary, with dark mode optimized palette
- **Typography**: Inter for UI, JetBrains Mono for code/URLs
- **Components**: Card-based layout with consistent spacing and rounded corners
- **Interactions**: Smooth hover effects and loading states
- **Accessibility**: Proper labels, ARIA attributes, and keyboard navigation

## User Preferences

None currently configured. Add user-specific preferences here as they're expressed during development.

## Recent Changes

- **October 19, 2025**: Initial implementation
  - Created complete MVP with webhook management, message composition, and history
  - Implemented Discord webhook validation and message sending
  - Built Discord-themed UI with shadcn components
  - Added comprehensive error handling and loading states
  - Fixed schema validation to properly handle webhookId injection on server side

## Technical Notes

### Webhook Validation
The backend validates webhook URLs by:
1. Checking URL format (must start with Discord webhook domain)
2. Making a GET request to verify the webhook exists
3. This ensures only valid, accessible webhooks are saved

### Message Sending Flow
1. Frontend sends message content + optional username/avatarUrl
2. Backend retrieves saved webhook
3. Backend posts to Discord webhook API
4. If successful, message is saved to history
5. Frontend receives confirmation and updates UI

### Testing Considerations
- Testing requires a real Discord webhook URL
- The app validates webhook connectivity before saving
- Message sending requires a saved, valid webhook
- Character limit is enforced at 2000 (Discord's limit)

## Future Enhancements

Potential features for future development:
- Discord embeds with rich formatting (titles, descriptions, colors, fields)
- Message scheduling for timed sends
- Multiple webhook profiles
- Message templates
- File/image attachment support
- Webhook URL encryption for enhanced security
- Export message history
