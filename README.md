# 👁️ IRIS — Talking AI Eyes for Visually Impaired People

**See, read and hear the world — in English and Urdu. Powered by Gemma 4, an open-weight AI model.**

Built at Hacktoberfest 2026 Hack Day, ACM UET New Campus, Lahore.

## The problem
Pakistan has over a million blind people and many more with low vision. Reading a medicine box, checking an expiry date, counting money or knowing what is in front of them all depend on asking someone else for help.

## The solution
IRIS is a voice-first assistant. Point the camera, and IRIS:
- **Guides you to hold the object right** — spoken tips for each mode, plus live checks for low light and shaking
- **Tells you how long to wait** — with a countdown that learns from real response times
- **Sees and speaks** — describes scenes, reads text, reads medicine labels (name, strength, expiry), and counts Pakistani money
- **Talks in English and Urdu** — text and voice
- **Lets you chat** — ask follow-up questions by voice or text ("What is the expiry date?")
- **Repeats on command** — say "repeat" or "dobara", or press R

### Keyboard shortcuts (no screen needed)
| Key | Action |
|---|---|
| Space | Talk to IRIS |
| R | Repeat last answer |
| C | Capture and analyze |

## Why open-source AI
Gemma 4 is an open-weight model. It can be run by anyone for free and, in future, fully offline on a phone — no internet needed, no data leaving the device. AI belongs to everyone, including people who cannot see.

## How to run
1. Download `index.html` and open it in **Google Chrome**.
2. Open **API key settings** and paste a free Gemini API key from [Google AI Studio](https://aistudio.google.com).
3. Choose a mode, turn on the camera, and press **See For Me** (or press C).

## Tech
- HTML, CSS, JavaScript — a single file, no installs
- Gemma 4 (`gemma-4-26b-a4b-it`) via the Gemini API: image input + multi-turn conversation
- Browser camera (getUserMedia) with live light and motion checks
- Browser speech synthesis (text-to-speech) and speech recognition (voice input)

## Future plans
- Run Gemma fully offline on the phone
- Continuous "walking mode" that warns about obstacles automatically
- More local languages (Punjabi, Sindhi, Pashto)

> IRIS is an assistant, not a replacement for a doctor, pharmacist or white cane.
