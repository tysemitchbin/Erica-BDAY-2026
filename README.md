# 🎂 How Well Do You Know Erica?

A pass-the-phone birthday quiz game. Three friends (Ethan, Ellie, Mitch) secretly
guess how the birthday judge (Erica) thinks. Erica ranks the answers each round,
and points are handed out based on her ranking — plus a bonus for nailing her
exact pick.

Two devices:

- **📱 The Controller** — the phone you tap on and pass around.
- **📺 The Big Screen** — a laptop or TV everyone watches. Animated game-show
  visuals, live scoreboard, confetti, sound effects.

You can also just play on **one phone** (skip the Big Screen at pairing).

---

## Play it

Once it's on GitHub Pages (see below), open the same URL on both devices:

1. **On the laptop/TV:** open the page → tap **The Big Screen**. It shows a QR code.
2. **On the phone:** open the page → tap **The Controller** → point the camera at
   the laptop's QR code.
3. The phone then shows a QR code back — hold it up to the **laptop's webcam**
   (click *"Scan the phone's code"* on the Big Screen first).
   - No webcam? Use the **"Paste the phone's code instead"** buttons on both
     sides — send the code to yourself via any chat app and paste it in.
4. Enter player names, pick the number of rounds, and go.

The phone and laptop talk directly to each other (peer-to-peer WebRTC) — **no
server**. They just need to be on the **same Wi-Fi**. Pairing takes about 20
seconds.

### Scoring

Each round everyone (Erica too) secretly picks an answer. Then Erica ranks her
**top 3**.

| Your guess is Erica's… | Points |
|---|---|
| ranked #1 | 3 |
| ranked #2 | 2 |
| ranked #3 | 1 |
| exact answer she picked for herself | +2 bonus |

Most points after all rounds wins. Erica is the judge and isn't scored.

---

## Put it on GitHub Pages

1. Create a new repo on GitHub (e.g. `erica-birthday-quiz`).
2. Upload these files (keep the folder structure):
   ```
   index.html
   vendor/qrcode.min.js
   vendor/jsQR.min.js
   README.md
   ```
   Or from this folder:
   ```bash
   git init
   git add .
   git commit -m "Erica's birthday quiz"
   git branch -M main
   git remote add origin https://github.com/<you>/erica-birthday-quiz.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a
   branch → `main` / `root` → Save**.
4. Wait ~1 minute. Your game is at
   `https://<you>.github.io/erica-birthday-quiz/`.

> The camera (QR scanning) only works over **HTTPS**, which GitHub Pages provides.
> Opening `index.html` straight off the disk won't have camera access — use the
> Pages URL, or the paste-the-code fallback.

---

## Edit the questions

Open `index.html` and find the `QUESTIONS` array near the top of the `<script>`.
Each entry is:

```js
{ cat: "Category shown on screen", q: "The question?", options: [
  "Answer A", "Answer B", "Answer C", "Answer D"
]},
```

Every question needs **exactly 4 options**. Add, remove, or rewrite freely, then
re-upload `index.html`.

Player names default to Ethan / Ellie / Mitch / Erica but are editable on the
setup screen every game.

---

## Troubleshooting

- **Pairing won't connect:** make sure both devices are on the same Wi-Fi (not one
  on cellular). Some guest/corporate networks block device-to-device traffic — try
  a phone hotspot. As a last resort, play on the single phone.
- **Laptop can't scan the phone:** use the *paste the code* buttons on both sides.
- **Updated the questions but the site looks the same:** hard-refresh
  (Ctrl/Cmd + Shift + R) — GitHub Pages and the browser cache aggressively.
- **`#dev` in the URL** exposes debug hooks; ignore it for normal play.
