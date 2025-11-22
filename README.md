# VoxDrop 🎤➡️🎬

Drop a voice, get a talking video powered by Gemini AI.

Record your voice, get it transcribed, and watch an animated character speak your words with AI-generated voice synthesis.

## Features

🎤 **Voice Recording** - Record directly from your microphone  
🧠 **AI Transcription** - Gemini converts speech to text exactly as spoken  
🎵 **Voice Synthesis** - 5 different AI voices to choose from  
🎨 **Animated Characters** - Blue Robot, Pink Alien, Green Monster, Yellow Blob  
⚡ **Real-time Animation** - Character reacts to audio volume  
🎥 **Video Export** - Download as WebM video file  
🚀 **Serverless Backend** - Runs on Vercel with no server management  

## Quick Start

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/voxdrop.git
   cd voxdrop
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   ```
   Get your Gemini API key from https://aistudio.google.com/app/apikey and add it to `.env.local`

4. **Run locally**
   ```bash
   npm run dev
   ```
   Visit `http://localhost:3000`

### Deploy to Vercel

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial VoxDrop commit"
   git push origin main
   ```

2. **Deploy via Vercel**
   - Go to https://vercel.com/new
   - Import your GitHub repository
   - Add environment variable:
     - Name: `GEMINI_API_KEY`
     - Value: Your API key from https://aistudio.google.com/app/apikey
   - Click Deploy

Your app will be live at `https://voxdrop-yourname.vercel.app` 🎉

## Project Structure

```
voxdrop/
├── public/
│   └── index.html              # Frontend UI (static)
├── api/
│   └── synthesize.js           # Serverless function (Gemini proxy)
├── .env.example                # Environment template
├── .gitignore                  # Git exclusions
├── package.json                # Dependencies & scripts
├── vercel.json                 # Vercel configuration
└── README.md                   # This file
```

## How It Works

1. **Record** - Click the mic button and speak
2. **Transcribe** - Gemini 2.5 Flash converts your audio to text
3. **Synthesize** - Gemini TTS converts text to AI voice (5 voice options)
4. **Render** - Canvas animation + audio combined into video
5. **Download** - Save as WebM or share directly

## API Keys

### Getting a Gemini API Key

1. Visit https://aistudio.google.com/app/apikey
2. Create a new API key (free tier available)
3. Copy the key
4. **Local**: Add to `.env.local` (never commit this)
5. **Vercel**: Add as environment variable in project settings

⚠️ **Security**: Your API key stays on the backend (Vercel serverless function). The frontend never sees it.

## Voice Options

Choose from 5 AI voices:

- **Kore** - Firm, confident tone
- **Puck** - Upbeat, energetic
- **Charon** - Informative, clear
- **Fenrir** - Excitable, enthusiastic
- **Aoede** - Breezy, casual

## Character Options

4 animated characters to choose from:

- 🤖 Blue Robot
- 👽 Pink Alien
- 👹 Green Monster
- 💛 Yellow Blob

Each character animates based on audio volume in real-time.

## Browser Compatibility

**Recommended:**
- Chrome/Chromium 60+
- Edge 79+
- Firefox 53+
- Safari 14.1+

**Requirements:**
- Microphone access
- MediaRecorder API
- Canvas 2D API
- Web Audio API
- Modern JavaScript (ES6+)

## Environment Variables

Create `.env.local` in the root directory:

```bash
# Required: Your Gemini API key from https://aistudio.google.com/app/apikey
GEMINI_API_KEY=your_key_here
```

⚠️ Never commit `.env.local` to Git. It's in `.gitignore` by default.

## Troubleshooting

### "Microphone Error"
- Check browser permissions for microphone access
- Allow microphone in browser settings
- Try a different browser

### "API Error"
- Verify your Gemini API key is valid
- Check Vercel environment variables are set correctly
- Ensure API key has no extra spaces

### "Video not rendering"
- Keep recordings 10-30 seconds for best results
- Check browser console for detailed errors (F12)
- Try clearing browser cache

### "Transcription is empty"
- Speak clearly and loud enough
- Check audio is being captured (test with another app)
- Verify Gemini API key is active

## Development

### Scripts

```bash
# Start local development server
npm run dev

# Build for production
npm run build

# Start production server
npm start
```

### File Locations

- **Frontend**: `public/index.html` - Edit UI/styling here
- **Backend**: `api/synthesize.js` - Edit API proxy here
- **Config**: `vercel.json` - Edit deployment settings

### Local Testing

Test API calls locally with:
```bash
curl -X POST http://localhost:3000/api/synthesize \
  -H "Content-Type: application/json" \
  -d '{"action":"transcribe","payload":{...}}'
```

## Performance

- Transcription: 2-5 seconds (Gemini 2.5 Flash)
- Synthesis: 3-10 seconds (TTS processing)
- Rendering: 5-20 seconds (video creation)
- **Total**: ~10-35 seconds for full process

Video file size: 500KB - 3MB depending on length

## Limits

- Recording length: Up to 5 minutes
- Video size: Limited by browser memory
- API rate limits: Depends on your Gemini API tier
- Vercel timeout: 5 minutes per request

## Contributing

Contributions welcome! Feel free to:
- Open issues for bugs
- Submit pull requests for improvements
- Suggest new features

## License

MIT - Feel free to use for personal or commercial projects

## Credits

Built with:
- [Gemini 2.5 Flash](https://ai.google.dev) - Transcription & TTS
- [Vercel](https://vercel.com) - Deployment & serverless functions
- [Tailwind CSS](https://tailwindcss.com) - Styling
- [Canvas Confetti](https://www.npmjs.com/package/canvas-confetti) - Celebration effects

## Support

Have questions? Try:
- [Gemini API Docs](https://ai.google.dev/tutorials)
- [Vercel Documentation](https://vercel.com/docs)
- [MDN Web Docs](https://developer.mozilla.org)
- Open an issue on GitHub

---

**Made with ❤️ using Gemini AI**
