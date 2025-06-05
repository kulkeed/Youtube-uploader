# YouTube Video Upload AI Agent

An automated system for uploading videos to YouTube with support for metadata management and scheduled uploads.

## Features

- OAuth 2.0 authentication with YouTube API
- Automated video uploads
- Scheduled uploads with flexible timing
- Metadata management (title, description, tags, privacy settings)
- Secure credential management

## Setup

1. **Prerequisites**
   - Node.js (v14 or higher)
   - A Google Cloud Project with YouTube Data API v3 enabled
   - OAuth 2.0 credentials from Google Cloud Console

2. **Installation**
   ```bash
   npm install
   ```

3. **Configuration**
   - Copy `.env.example` to `.env`
   - Fill in your YouTube API credentials:
     - `YOUTUBE_CLIENT_ID`: Your OAuth 2.0 client ID
     - `YOUTUBE_CLIENT_SECRET`: Your OAuth 2.0 client secret
     - `YOUTUBE_REDIRECT_URI`: Your OAuth 2.0 redirect URI
     - `YOUTUBE_REFRESH_TOKEN`: (Optional) Your refresh token once obtained

4. **Build the Project**
   ```bash
   npm run build
   ```

## Usage

1. **First-time Authorization**
   - Run the application: `npm start`
   - Follow the authorization URL printed in the console
   - Grant access to your YouTube account
   - Copy the authorization code from the redirect URL
   - The refresh token will be saved automatically

2. **Uploading Videos**
   - Configure your upload in `src/index.ts`
   - Run `npm start`

## Video Upload Configuration

```typescript
const uploadConfig: UploadConfig = {
    filePath: './video.mp4',
    metadata: {
        title: 'Your Video Title',
        description: 'Video description',
        tags: ['tag1', 'tag2'],
        privacyStatus: 'private', // or 'public' or 'unlisted'
        categoryId: '22' // See YouTube API documentation for category IDs
    },
    scheduleTime: new Date('2025-06-05T10:00:00Z') // Optional scheduling
};
```

## Development

- Run in development mode (with watch mode): `npm run dev`
- Build the project: `npm run build`
- Start the application: `npm start`

## Security Notes

- Never commit your `.env` file
- Store credentials securely
- Use environment variables for sensitive information
- Regularly rotate your OAuth credentials

## Error Handling

The application includes error handling for:
- Failed uploads
- Authentication errors
- Invalid file paths
- Scheduling conflicts

## License

MIT License
