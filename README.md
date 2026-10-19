# Accent Lab

A personal web app for practicing American English pronunciation on iPhone (Safari).

## What works now (step 1)
- 13 sounds that learners often find hard (θ, ð, American r, æ, ship/sheep, ʌ, ɑ, schwa, flap t, v/w, ŋ, dark l, full/fool).
- Each sound has: practice items (words and sentences), a model voice (the phone's built-in US voice, with a slow option), recording and playback, "model, then me" comparison, self-rating, mouth/tongue steps, and tap-to-hear minimal pairs.
- Ratings are saved on the device (localStorage).
- Recording needs the app to be opened from an https address (for example GitHub Pages). Opened as a local file, it offers a voice-memo upload instead.

## Pronunciation scores (step 2)
- After each recording, the take is sent to Azure AI Speech Pronunciation Assessment (en-US) and the "Pronunciation score" card shows overall, accuracy, fluency and completeness, plus a score for every word and every sound. Weak sounds are red, and the sound of the current page is outlined.
- iPhone Safari records AAC (audio/mp4), which the Azure REST API doesn't accept, so the app converts each take to 16 kHz mono WAV in the browser (max 30 s) before sending it.
- Setup: create a Speech resource in the Azure portal (Free F0 tier, 5 audio hours a month), then open the app, tap ⚙ Settings, paste KEY 1 and the region (for example `westeurope`), and tap Check key.

## AI tutor (step 3)
- After a score comes in, tap **Get a tip**. The app sends the Azure scores (text only, no audio) to a model on OpenRouter, which replies with a short tip on tongue, lips and jaw plus 2-3 drills. Tap a drill to hear it.
- The tutor only coaches; Azure does the scoring.
- Model is chosen in Settings: Claude Haiku 5.5 (default, cheapest), GPT-4.1 mini, Claude Sonnet 5.5, or any other OpenRouter model ID.
- Setup: create a key at openrouter.ai/settings/keys with a small credit limit, then paste it in ⚙ Settings → AI tutor and tap Check key.

## Updates
Phones keep a saved copy of the page for a while. The app compares its `APP_VERSION` with the copy on GitHub when it opens or comes back to the foreground, and shows an "Update" button when a newer one is online. Settings also has "Check for updates". **Bump `APP_VERSION` in `index.html` with every change you push**, or the update button won't appear.

## API keys
There is no server. Keys are typed into the app's Settings screen and stored only in that device's localStorage. Never put keys in `index.html` or anywhere in this repo: the repo is public.

## Tongue animations
Each sound page has an animated side view of the mouth (lips, teeth, tongue, roof of the mouth, soft palate), drawn as SVG in `index.html` (`POSES` and `MOUTH`). It moves from rest into the sound's position and back; tap it to pause. A blue arrow shows air, a red zigzag shows voice. With "Reduce motion" turned on, it shows the target position without moving.

Below the steps, "Watch a real speaker" links open the matching MRI video on Seeing Speech (University of Glasgow, CC BY-NC-ND 4.0). The videos are linked, not copied into this repo.

To replace a drawing with your own animation, put a GIF at `gifs/<sound-id>.gif` (ids: th-voiceless, th-voiced, r, ae, ih-ee, uh, ah, schwa, flap-t, v-w, ng, dark-l, oo). If the file exists, the app shows it instead.

## Pronunciation scores (step 2)
- After each recording, the take is sent to Azure AI Speech Pronunciation Assessment (en-US) and the "Pronunciation score" card shows overall, accuracy, fluency and completeness, plus a score for every word and every sound. Weak sounds are red, and the sound of the current page is outlined.
- iPhone Safari records AAC (audio/mp4), which the Azure REST API doesn't accept, so the app converts each take to 16 kHz mono WAV in the browser (max 30 s) before sending it.
- Setup: create a Speech resource in the Azure portal (Free F0 tier, 5 audio hours a month), then open the app, tap ⚙ Settings, paste KEY 1 and the region (for example `westeurope`), and tap Check key.

## AI tutor (step 3)
- After a score comes in, tap **Get a tip**. The app sends the Azure scores (text only, no audio) to a model on OpenRouter, which replies with a short tip on tongue, lips and jaw plus 2-3 drills. Tap a drill to hear it.
- The tutor only coaches; Azure does the scoring.
- Model is chosen in Settings: Claude Haiku 5.5 (default, cheapest), GPT-4.1 mini, Claude Sonnet 5.5, or any other OpenRouter model ID.
- Setup: create a key at openrouter.ai/settings/keys with a small credit limit, then paste it in ⚙ Settings → AI tutor and tap Check key.

## API keys
There is no server. Keys are typed into the app's Settings screen and stored only in that device's localStorage. Never put keys in `index.html` or anywhere in this repo: the repo is public.

## Tongue animations
Put one GIF per sound in the `gifs/` folder, named after the sound id. The app shows it automatically; if the file is missing, it shows a placeholder.

| Sound | File |
|---|---|
| θ think | gifs/th-voiceless.gif |
| ð this | gifs/th-voiced.gif |
| American r | gifs/r.gif |
| æ cat | gifs/ae.gif |
| ship vs sheep | gifs/ih-ee.gif |
| ʌ cup | gifs/uh.gif |
| ɑ hot | gifs/ah.gif |
| schwa | gifs/schwa.gif |
| flap t | gifs/flap-t.gif |
| v vs w | gifs/v-w.gif |
| ŋ sing | gifs/ng.gif |
| dark l | gifs/dark-l.gif |
| full vs fool | gifs/oo.gif |

## Still to do
- Nothing planned. Ideas: progress history per sound, more practice items.
