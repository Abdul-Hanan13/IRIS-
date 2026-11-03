# 👁️ IRIS — Hands-Free Talking Eyes for Blind People

🏆 **1st Place — Hacktoberfest 2026 Hack Day, ACM UET New Campus, Lahore**

IRIS is a voice-first AI agent for blind and low-vision people. It is controlled entirely by voice, speaks every step out loud, guides the user's hand into position, takes the picture by itself, and explains what it sees — in **English and Urdu**. Powered by **Gemini 3.8 Flash**, with **Gemma 4** (open-weight) as an automatic backup.

## The problem
Pakistan has over a million blind people. Reading a medicine box, checking an expiry date, counting money or knowing what is in front of them all depend on asking someone else for help. Most "AI vision" apps still expect the user to *see* the screen to aim the camera and press buttons.

## How IRIS works — no screen needed
1. **Start:** tap anywhere on the screen (or press any key). IRIS greets you and explains how to talk to it.
2. **Wake it any time:** say **"Hey IRIS"**, **"Listen"** or **"Hello"** (سنو / ہیلو), or **tap anywhere** on the screen. IRIS says *"Yes? I'm listening."* You can also say it in one go: *"Hey IRIS, what is this?"*
3. **Ask by voice:** "what is this", "read", "medicine", "money", "around me" — or any question.
3. **Guided aiming:** IRIS checks the camera live and tells you what to do:
   - "Move the phone a little to the right" · "Bring it closer" · "Too close, move back" · "Hold still" · "It's too dark"
   - **Beeps** get faster and higher as you get closer to the right position (like a parking sensor), with vibration on phones.
4. **Auto-capture:** when the object is centred, steady and well lit, IRIS takes the picture by itself (or say "take it").
5. **Tells you the wait:** "Analyzing now, about 8 seconds", with soft ticks while it works.
6. **Answers out loud**, warnings first if something is dangerous or expired.
7. **If the photo isn't good enough**, Gemma says so and IRIS guides you again automatically.
8. **After every answer** IRIS says *"Anything else? Ask me now. Later, just say Hey IRIS, or tap anywhere."* For about 8 seconds you can ask a follow-up without the wake word ("what is the expiry date?", "repeat", "details"). Then IRIS goes back to waiting with a soft sound. Say **"thank you"** to end straight away.
9. **The microphone is off while IRIS speaks**, so it never hears itself. To interrupt IRIS, tap the screen. A question asked while IRIS is busy is answered next.

### Voice commands (English / Urdu)
| Say | Does |
|---|---|
| Hey IRIS · Listen · Hello · سنو · ہیلو | Wake IRIS up |
| thank you · bye · شکریہ | Done for now (IRIS waits) |
| what is this · یہ کیا ہے | Identify the object |
| read · پڑھو | Read text |
| medicine · دوا | Name, strength, expiry date |
| money · پیسے | Count notes |
| around me · ارد گرد | Describe surroundings |
| take it · تصویر لو | Take the picture now |
| repeat · دوبارہ | Say it again |
| details · تفصیل | More information |
| stop · رکو | Be quiet / cancel |
| slower / faster · آہستہ / تیز | Change speaking speed |
| Urdu / English · اردو / انگریزی | Change language |
| help · مدد | List commands |

**Keyboard:** Space = talk · Enter = scan/capture · R = repeat · D = details · Esc = stop · H = help · L = language · 1–5 = modes
**Touch (anywhere on the screen):** tap = talk (or take the picture while aiming, or stop IRIS talking) · hold = repeat the last answer

## Setup
**Best on an Android phone with Google Chrome**, opened over HTTPS (for example GitHub Pages).

1. Get a free API key from [Google AI Studio](https://aistudio.google.com).
2. A sighted helper opens IRIS **once** with the key in the link: `https://<your-site>/index.html?key=YOUR_KEY` — the key is saved on that phone and removed from the address bar. (Or use ⚙ Settings.)
3. On the phone: Chrome menu → **Add to Home screen**. From then on: tap the icon, tap anywhere, and talk.

### Key-free option (Vercel)
Deploy this repo on [Vercel](https://vercel.com) and add an environment variable `GEMINI_API_KEY`. The included `api/generate.js` keeps the key on the server, so users never see or enter one.

## Tech
- One HTML file — HTML, CSS, JavaScript, no installs
- **AI models** via the Gemini API (one free key), chosen in ⚙ Settings:
  | Setting | Models tried in order |
  |---|---|
  | **Best** (default) | Gemini 3.8 Flash → Gemma 4 |
  | **Fast** | Gemini 3.5 Flash-Lite → Gemma 4 |
  | Gemini only | Gemini 3.8 Flash |
  | Open-weight only | Gemma 4 (`gemma-4-26b-a4b-it`) |

  If a model hits its free limit or fails, IRIS switches to the next one automatically and skips the limited model for a minute, so the user never hears silence.
- **Web Speech API** — continuous voice recognition (en-US / ur-PK) and text-to-speech
- **Live camera analysis** in the browser — brightness, motion and object position from edge detection, used for spoken guidance
- Web Audio beeps, vibration and screen wake-lock

## Known limits
- Voice commands need Chrome and an internet connection.
- A web page can't run a true always-on wake word like "Hey Google". IRIS restarts the browser's speech recognition in a loop, so on some Android phones you may hear a small beep when it restarts, and it stops when the screen locks. A native Android app would fix both.
- Urdu speech needs an Urdu or Hindi voice installed on the device; otherwise IRIS shows Urdu text and speaks English.
- Hand guidance works best with a plain background (a table or wall) behind the object.
- On Google's **free tier**, inputs and outputs may be used to improve Google's products and may be read by human reviewers. Don't use a free key for private documents; use a paid key or the Gemma-only setting with a self-hosted model.
- Gemini is a closed model. Gemma runs on Google's servers today; because it is open-weight, a future version can run fully on the phone, offline.

> IRIS is an assistant, not a replacement for a doctor, pharmacist or white cane.
