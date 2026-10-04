# BYOK — Bring Your Own Key

A free AI chat interface that lets you connect your own API keys, discover available models, and chat with your preferred providers.

Provider usage is billed by your API provider.

## Features

- Google sign-in
- Multiple provider connections
- OpenAI-compatible, Anthropic, and Gemini API formats
- Model discovery and manual model entry
- Saved conversations and connections
- Rename, pin, and delete conversations
- Custom accent colors and light/dark appearance
- Collapsible sidebar and expanded reading mode

## How It Works

This repository contains the static BYOK frontend.

- **Frontend hosting:** Vercel
- **Authentication:** Firebase Authentication
- **Saved workspace:** Existing Cloudflare backend and D1 database
- **AI requests:** Sent directly from your browser to your selected provider

The `vercel.json` file forwards `/api` requests to the existing BYOK backend.

## Deploy on Vercel

1. Import this GitHub repository into Vercel.
2. Select **Other** as the Framework Preset.
3. Leave the Build Command empty.
4. Set the Output Directory to `.`.
5. Click **Deploy**.
6. Add your deployed hostname to:
   **Firebase → Authentication → Settings → Authorized domains**.

The existing backend must remain available for saving and loading workspaces.

## Using BYOK

1. Sign in with Google.
2. Open **Connections**.
3. Choose a provider or enter a custom endpoint.
4. Enter your API key and discover models.
5. Select a model and start chatting.

Custom endpoints must support a compatible API format and allow browser requests through CORS. Some providers may require manual model entry.

## Project Files

| File | Purpose |
| --- | --- |
| `index.html` | Application interface |
| `style.css` | Styles and appearance |
| `app.js` | Chat, connections, and workspace controls |
| `firebase-login.js` | Google authentication |
| `vercel.json` | Backend proxy configuration |
| `byok-logo.png` | BYOK logo |

## Security

- Saved API keys are encrypted by the existing backend.
- Workspace access requires a verified Google sign-in.
- API keys are available in the signed-in browser when making provider requests.
- Connect only providers and endpoints you trust.
- Never commit private API keys, service account credentials, or `.env` files.

## Limitations

This frontend is configured for the original BYOK Firebase project and backend. Forks must configure their own authentication and backend services.

Deploying the frontend alone does not create a new database or migrate existing saved data.
