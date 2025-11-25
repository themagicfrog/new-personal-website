# Last.fm Now Playing Widget Setup

This guide will help you set up the Last.fm "Now Playing" widget on your website.

## Step 1: Create a Last.fm Account

1. Go to [Last.fm](https://www.last.fm/)
2. Click **Sign Up** and create an account
3. Verify your email address

## Step 2: Connect Spotify to Last.fm

1. Go to [Last.fm Settings](https://www.last.fm/settings/applications)
2. Scroll down to **Connect Spotify**
3. Click **Connect** and authorize Last.fm to access your Spotify account
4. Now your Spotify plays will automatically scrobble to Last.fm

## Step 3: Get Your Last.fm API Key

1. Go to [Last.fm API Account](https://www.last.fm/api/account/create)
2. Fill in the form:
   - **Application name**: Your website name (e.g., "Personal Website")
   - **Application description**: Brief description
   - **Callback URL**: Your website URL (e.g., `https://your-site.vercel.app`)
   - **Application website**: Your website URL
3. Click **Submit**
4. Copy your **API Key** (you'll see it immediately after creation)

## Step 4: Add Environment Variables

### For Local Development

Add to your `.env` file:

```env
PUBLIC_LASTFM_API_KEY=your_api_key_here
PUBLIC_LASTFM_USERNAME=your_lastfm_username
```

### For Vercel Deployment

1. Go to your Vercel project dashboard
2. Click **Settings** → **Environment Variables**
3. Add:
   - **Name**: `PUBLIC_LASTFM_API_KEY`
   - **Value**: Your Last.fm API key
   - **Environment**: Production, Preview, Development (check all)
4. Add:
   - **Name**: `PUBLIC_LASTFM_USERNAME`
   - **Value**: Your Last.fm username
   - **Environment**: Production, Preview, Development (check all)
5. Click **Save**

## Step 5: Test It

1. Make sure Spotify is connected to Last.fm
2. Play a song on Spotify
3. Refresh your website
4. The widget should appear showing your currently playing track!

## How It Works

- Last.fm automatically tracks what you're playing on Spotify (if connected)
- The widget fetches your most recent track from Last.fm
- If the track is marked as "now playing", it displays on your website
- The widget only shows when you're actively listening to something

## Troubleshooting

**Widget not showing?**
- Make sure you're actively playing music on Spotify
- Verify Spotify is connected to Last.fm (check Last.fm settings)
- Check that your Last.fm username is correct in environment variables
- Make sure your API key is correct

**Track not updating?**
- Last.fm updates in real-time, but there may be a few seconds delay
- Make sure scrobbling is enabled in your Last.fm settings

## Benefits of Last.fm

- ✅ No OAuth or complex authentication needed
- ✅ Free API with generous rate limits
- ✅ Works with multiple music services (Spotify, Apple Music, etc.)
- ✅ Tracks your listening history automatically
- ✅ Simple API key setup

