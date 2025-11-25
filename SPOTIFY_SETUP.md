# Spotify Now Playing Widget Setup

This guide will help you set up the Spotify "Now Playing" widget on your website.

## Option 1: Using Spotify Web API (Recommended)

### Step 1: Create a Spotify App

1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Click **Create App**
3. Fill in:
   - **App name**: Your website name
   - **App description**: Personal website
   - **Redirect URI**: `http://localhost:4321` (for development)
4. Click **Save**
5. Note your **Client ID** and **Client Secret**

### Step 2: Get an Access Token

You'll need to get an access token. There are two approaches:

#### Approach A: Using a Refresh Token (Recommended for Personal Sites)

1. Use the [Spotify Authorization Code Flow](https://developer.spotify.com/documentation/web-api/tutorials/code-flow)
2. Get a refresh token (this is a one-time setup)
3. Store the refresh token securely

#### Approach B: Using a Serverless Function

Create an API endpoint that refreshes the token automatically. You can use:
- Vercel Serverless Functions
- Netlify Functions
- Cloudflare Workers

### Step 3: Add Environment Variables

Add to your `.env` file:

```env
PUBLIC_SPOTIFY_ACCESS_TOKEN=your_access_token_here
```

**Note**: For production, you should use a serverless function to refresh tokens automatically, as access tokens expire after 1 hour.

## Option 2: Using a Third-Party Service (Simpler)

### Last.fm Integration

1. Sign up at [Last.fm](https://www.last.fm/)
2. Connect your Spotify account
3. Get your Last.fm API key
4. Use Last.fm's API to fetch currently playing tracks

### Spotify Widget Services

- [Spotify Widget Generator](https://spotifywidgets.com/)
- [Spotify Now Playing Widget](https://github.com/natemoo-re/spotify-now-playing)

## Option 3: Manual Update (Simplest)

If you don't want to set up API access, you can manually update a track in your database or use a simple form to update what you're listening to.

## Implementation Notes

The current implementation uses `PUBLIC_SPOTIFY_ACCESS_TOKEN` which works for development but has limitations:
- Access tokens expire after 1 hour
- You'll need to refresh them regularly

For a production site, consider:
1. Creating a serverless function that refreshes tokens
2. Using a service like Last.fm
3. Using a simpler manual update system

## Quick Start (Development Only)

For quick testing, you can get a temporary access token:

1. Go to [Spotify Web API Console](https://developer.spotify.com/console/get-users-currently-playing-track/)
2. Click **Get Token**
3. Select scopes: `user-read-currently-playing`
4. Copy the token to your `.env` file

**Warning**: This token expires quickly. For production, use a proper refresh token flow.

