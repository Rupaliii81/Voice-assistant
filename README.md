# Voice-assistant
# ARIA — Voice Assistant
 
A sleek, single-file voice assistant for the browser. Speak or type to ARIA and hear her reply, using the Web Speech API for recognition and ElevenLabs (or built-in browser TTS) for speech output.
 
![HTML](https://img.shields.io/badge/HTML-5-orange) ![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla-yellow) ![License](https://img.shields.io/badge/License-MIT-blue)
 
## Features
 
- 🎙️ **Voice input** via the Web Speech API (Chrome / Edge)
- ⌨️ **Text input fallback** for unsupported browsers or quiet environments
- 🔊 **Text-to-speech** with ElevenLabs voices (Rachel, Domi, Bella, Antoni) or free **Browser TTS**
- 🔮 **Animated orb UI** with listening and speaking states, ripple rings and waveform bars
- 💬 **Live transcript panel** of the conversation
- ■ **Stop button** to interrupt speech instantly
- 📦 **Zero dependencies** — one HTML file, no build step
## Demo
 
Open `index.html` in Chrome or Edge, click the orb, and start talking.
 
> Add a screenshot or GIF here: `![ARIA screenshot](screenshot.png)`
 
## Getting Started
 
### 1. Clone the repository
 
```bash
git clone https://github.com/<your-username>/aria-voice-assistant.git
cd aria-voice-assistant
```
 
### 2. Run it
 
Just open `index.html` in your browser. For microphone access, some browsers require a secure context, so a local server is recommended:
 
```bash
# Python
python -m http.server 8000
 
# or Node
npx serve
```
 
Then visit `http://localhost:8000`.
 
### 3. (Optional) Enable ElevenLabs voices
 
1. Get a free API key at [elevenlabs.io](https://elevenlabs.io).
2. In `index.html`, replace the placeholder:
```js
   const ELEVEN_API_KEY = 'YOUR_ELEVENLABS_API_KEY';
```
 
3. Pick an ElevenLabs voice from the dropdown.
No key? Select **Browser TTS (Free)** and it works out of the box.
 
> ⚠️ **Never commit your real API key.** This is a client-side app, so any key in the source is visible to users. For production, proxy requests through a backend.
 
## Usage
 
| Action | How |
|---|---|
| Start / stop listening | Click the orb or the mic button |
| Type a message | Use the text box and press **Enter** |
| Change voice | Use the dropdown |
| Stop speaking | Click **■ Stop** |
 
### Built-in commands
 
ARIA currently responds to simple rule-based phrases: `hello`, `hi`, `how are you`, `what time is it`, `what day is it`, `tell me a joke`, `thank you`, `bye`. Anything else gets a fallback reply.
 
## Make ARIA Smarter
 
Replace the rule-based logic in `getAIResponse()` with a call to an LLM API such as Claude or OpenAI. The `ARIA_PERSONA` prompt and `conversationHistory` array are already set up for this:
 
```js
async function getAIResponse(userText) {
  conversationHistory.push({ role: 'user', content: userText });
  // Call your AI API here with ARIA_PERSONA + conversationHistory
}
```
 
Route the API call through a backend so your keys stay private.
 
## Browser Support
 
| Feature | Chrome | Edge | Firefox | Safari |
|---|---|---|---|---|
| Speech recognition | ✅ | ✅ | ❌ | ⚠️ Partial |
| Browser TTS | ✅ | ✅ | ✅ | ✅ |
| ElevenLabs TTS | ✅ | ✅ | ✅ | ✅ |
 
Unsupported browsers can still use the text input.
 
## Tech Stack
 
- HTML5, CSS3 (custom properties, keyframe animations)
- Vanilla JavaScript
- Web Speech API (`SpeechRecognition`, `SpeechSynthesis`)
- ElevenLabs Text-to-Speech API
- Google Fonts: Syne, Syne Mono
## Project Structure
 
```
aria-voice-assistant/
├── index.html    # Entire app: markup, styles, and scripts
└── README.md
```
 
## Roadmap
 
- [ ] Connect to an LLM backend
- [ ] Multi-language recognition
- [ ] Wake word ("Hey ARIA")
- [ ] Persistent conversation history
- [ ] Real audio-reactive waveform
 
 
 
