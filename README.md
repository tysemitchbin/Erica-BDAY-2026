# 🎂 How Well Do You Know Erica?

A pass-the-phone birthday party game. Every round is an open-ended prompt.
**Everyone types an answer** (Erica included). The four answers show up shuffled
and anonymous, **Erica ranks them 1–4**, and then the reveal shows who wrote
what and hands out points.

Two devices:

- **📱 The Controller** — the phone you type on and pass around.
- **📺 The Big Screen** — a laptop or TV everyone watches. Prompts, the
  anonymous answers, live scoreboard, medal reveal, confetti, sound.

You can also just play on **one phone** (skip the Big Screen at pairing).

---

## Play it

Once it's on GitHub Pages (see below), open the same URL on both devices:

1. **On the laptop/TV:** open the page → tap **The Big Screen**. It shows a QR code.
2. **On the phone:** open the page → tap **The Controller** → point the camera at
   the laptop's QR code.
3. The phone then shows a QR code back — hold it up to the **laptop's webcam**
   (click *"Scan the phone's code"* on the Big Screen first).
   - No webcam? Use the **"Paste the code"** buttons on both sides — send the
     code to yourself via any chat app and paste it in.
4. Enter the four names, pick the number of rounds, go.

The phone and laptop talk **directly** to each other (peer-to-peer WebRTC) — **no
server**. They just need the **same Wi-Fi**. Pairing takes about 20 seconds.

### A round, step by step

1. Prompt appears on the Big Screen, e.g. *"Erica's villain origin story: it all
   started when ___"*.
2. Phone goes round the room — **Ethan, Ellie, Mitch, then Erica** each secretly
   type an answer. Erica goes last so she never reacts to anyone else's.
3. The four answers appear on the Big Screen, shuffled and anonymous.
4. Erica (still holding the phone) **ranks all four**, best to worst.
5. Reveal: each answer flips to show who wrote it — including which one was
   Erica's own — and points land.

### Scoring

| Your answer is Erica's… | Points |
|---|---|
| #1 | 3 |
| #2 | 2 |
| #3 | 1 |
| #4 | 0 |

One of the four answers is always Erica's own, so the goal is to land above it.
Most points after all rounds wins. Erica is the judge and isn't scored.

---

## Put it on GitHub Pages

1. Create a new repo on GitHub (e.g. `erica-birthday-quiz`).
2. Push these files (keep the folder structure — `index.html`, `vendor/`, `README.md`):
   ```bash
   git remote add origin https://github.com/<you>/erica-birthday-quiz.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / root → Save**.
4. Wait ~1 minute. Your game is at `https://<you>.github.io/erica-birthday-quiz/`.

> QR scanning needs **HTTPS**, which GitHub Pages provides. Opening `index.html`
> straight off the disk won't have camera access — use the Pages URL, or the
> paste-the-code fallback.

---

## Edit the prompts

Open `index.html`, find the `PROMPTS` array near the top of the `<script>`:

```js
{ cat: "Origin Story", q: "{E}'s villain origin story: it all started when ___" },
```

- `{E}` is replaced with the judge's name, `{F}` with the first player's name.
- End prompts with `___` so people know where their answer goes.

Names default to Ethan / Ellie / Mitch / Erica but are editable every game.

---

## Troubleshooting

- **Pairing won't connect:** both devices must be on the same Wi-Fi (not one on
  cellular). Some guest/office networks block device-to-device traffic — try a
  phone hotspot, or just play on the single phone.
- **Laptop can't scan the phone:** use the *paste the code* buttons on both sides.
- **Edited the prompts but the site looks the same:** hard-refresh
  (Ctrl/Cmd + Shift + R) — GitHub Pages and browsers cache aggressively.
- **`#dev` in the URL** exposes debug hooks; ignore it for normal play.
