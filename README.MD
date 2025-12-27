# LLaVA Deno WebSocket – Multimodal Studio

Beautiful, latency-friendly front‑end for the Gemini 2.0 Flash multimodal live API. Chat with text, talk with audio, stream camera frames, and share your screen from one polished cockpit backed by a Deno/Cloudflare Worker.

## Features
- 🎙️ Realtime text + audio conversations with visual log stream
- 🎥 Camera frame streaming with quick stop/flip controls
- 🖥️ Screen sharing preview with inline close control
- 🛠️ Config drawer for language, voice, response type, FPS, and system prompts
- 🔐 Local storage of session preferences (API key, voice, FPS, prompt)

## Requirements
- Node.js 18+ (tested with 20)
- npm (for local dev scripts and tests)
- Cloudflare account for Worker deployment **or** Deno Deploy for serverless hosting
- Gemini API key (entered in the UI when connecting)

## Quickstart (Local UI)
1. Install dependencies  
   ```bash
   npm install
   ```
2. Start the Worker in dev mode  
   ```bash
   npm run dev
   ```
3. Open the served URL from Wrangler and:
   - Paste your Gemini API key
   - Click **Connect**
   - Use **settings** to tune language/voice/FPS/system prompt
   - Send text, toggle mic, camera, or screen share as needed

## Deployment

### Cloudflare Workers
1. Install Wrangler (`npm install -g wrangler` if you prefer global).  
2. Configure your account ID/API token in `wrangler.toml`.  
3. Deploy:  
   ```bash
   npm run deploy
   ```
4. Open the Worker URL, enter your Gemini key, and you are live.

### Deno Deploy
1. Create a new project at [Deno Deploy](https://dash.deno.com/).  
2. Set the entrypoint to `src/deno_index.ts`.  
3. Deploy and visit the generated domain to use the studio UI.

## Using the UI
1. **API Key** – add your Gemini key in the header field.  
2. **Configuration drawer** – choose language/voice, text vs. audio responses, FPS for camera frames, and set a custom system prompt. Hit **Confirm** to apply.  
3. **Messaging** – type into the composer and press **Send** (or Enter).  
4. **Mic/Camera/Screen** – tap the circular controls to stream audio, camera frames, or share your screen.  
5. **Activity feed** – system, user, and AI messages are color-coded with timestamps.

## Testing
```bash
npm test
```
Vitest is configured for the Cloudflare Workers runtime.

## Project Structure
- `src/static/` – UI (HTML/CSS/JS) served by the Worker  
- `src/index.js` – Cloudflare Worker entry for static assets + proxy  
- `src/deno_index.ts` – Deno Deploy entry  
- `src/api_proxy/` – Gemini ↔ OpenAI-style proxy logic  
- `test/` – Vitest specs for the Worker

## License
MIT License. See [LICENSE](LICENSE) for details.
