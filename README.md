# Riya Voice Sales Desk

A single-file web app (`index.html`) where an AI sales agent holds a real voice conversation to sell a SaaS product.

## How it works
- **Voice in:** browser Speech Recognition (Chrome or Edge), in English, Hindi or Telugu.
- **Brain:** Gemini (free key from aistudio.google.com) or any OpenAI-compatible API such as Groq. It is told the product facts, replies in one or two spoken sentences, handles objections and pushes for a trial, purchase or demo.
- **Voice out:** browser Speech Synthesis.
- **Live chat:** every bot and customer line appears as it happens, with a dashed bubble for what the customer is saying right now.
- **Call controls:** Start Call, End Call, status pill, running timer.
- **Recording:** a consent dialog appears first. The customer's microphone is recorded with MediaRecorder and stored in the browser (IndexedDB), then played back from Call History. Clicking a transcript line jumps to that moment.
- **After the call:** the AI writes a summary, customer needs, objections and next steps, and assigns one of the six statuses (Converted, Interested, Follow-up Required, Not Interested, Demo Requested, No Response).
- **Call History:** every call with recording, summary, transcript and status. Summaries can be regenerated.

## Run it
1. Host the file over HTTPS (the microphone does not work from plain http). Free options: Netlify Drop (drag the folder onto app.netlify.com/drop), GitHub Pages, Vercel.
2. Open the site in Chrome or Edge, click Settings, paste an API key, press Test connection, Save.
3. Click Start Call, agree to recording, and talk.

Never put an API key inside `index.html` or anywhere in a public repository: anyone can read it, and Google may disable a leaked key. Evaluators paste a key into Settings instead (it stays in their own browser). Free keys come from aistudio.google.com/apikey.

## Host on GitHub Pages
1. Create a public repository and upload `index.html` (in the root) and this README.
2. Settings, then Pages: Source "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
3. After a minute or two the site is at `[https://<username>.github.io/<repository>/](https://vanshika-gupta001.github.io/Riya_chatbot/)`.

## Known limits
- With a Gemini key and "Use Gemini voice" on (the default), the recording holds both sides: your microphone and Riya's voice are mixed together. This also gives Hindi and Telugu speech without any installed voice. Gemini's free voice quota is small; if it runs out mid-call the app switches to the browser voice, and from then on only the customer's side is recorded (the transcript still has everything).
- With Groq/OpenAI or Gemini voice off, the browser's own voice is used. It cannot be recorded, so only the customer's side is saved, and Hindi/Telugu need a voice installed on the device.
- Call history lives in the browser it was recorded in.
