# Accent Lab

A personal web app for practicing American English pronunciation on iPhone (Safari).

## What works now (step 1)
- 13 sounds that learners often find hard (θ, ð, American r, æ, ship/sheep, ʌ, ɑ, schwa, flap t, v/w, ŋ, dark l, full/fool).
- Each sound has: practice items (words and sentences), a model voice (the phone's built-in US voice, with a slow option), recording and playback, "model, then me" comparison, self-rating, mouth/tongue steps, and tap-to-hear minimal pairs.
- Ratings are saved on the device (localStorage).
- Recording needs the app to be opened from an https address (for example GitHub Pages). Opened as a local file, it offers a voice-memo upload instead.

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
- Step 2: send each recording to Azure Pronunciation Assessment (en-US) and show phoneme scores in the "Pronunciation score" card. The hook is marked `Step 2` in `index.html`, inside the Record button handler.
- Step 3: AI tutor that reads the scores and gives tips and drills. Placeholder card is marked `Step 3`. For now a "Copy for Claude" button copies a ready-made prompt.
- API keys must not be put in the page itself; steps 2 and 3 need a small server-side piece to hold them.
