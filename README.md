# 🎂 Erica's Birthday Quiz — K-Pop × Azeroth Edition

A pass-the-phone birthday party game. Every round is an open-ended prompt.
**Everyone types an answer** (Erica included). The four answers show up shuffled
and anonymous on the big screen, **Erica ranks them 1–4**, and the reveal shows
who wrote what and hands out points. After the last round there's a full results
screen — crown, winner, animated scoreboard, confetti.

Two devices:

- **📱 The Controller** — the phone you type on and pass around.
- **📺 The Big Screen** — a laptop or TV everyone watches. Prompts, the
  anonymous answers, live scoreboard, medal reveal, confetti, sound.

You can also just play on **one phone** (skip the Big Screen at pairing).

---

## Play it

Once it's on GitHub Pages (see below), open the same URL on both devices:

1. **On the laptop/TV:** open the page → tap **The Big Screen**. It shows a
   **6-character code** (big, on screen).
2. **On the phone:** open the page → tap **The Controller** → type that code →
   **Connect**.
3. Enter the four names, pick the number of rounds, go.

The two devices meet in a room named by that code, through a free public relay —
**no server to run, no camera, no long codes**. Both devices just need **internet**
(any Wi-Fi or cellular; they do **not** need to be on the same network).

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
2. Push these files (keep the structure — `index.html`, `vendor/mqtt.min.js`, `README.md`):
   ```bash
   git remote add origin https://github.com/<you>/erica-birthday-quiz.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: Deploy from a branch → `main` / root → Save**.
4. Wait ~1 minute. Your game is at `https://<you>.github.io/erica-birthday-quiz/`.

---

## Edit the prompts

Open `index.html`, find the `PROMPTS` array near the top of the `<script>`:

```js
{ cat: "Origin Story", q: "{E}'s villain origin story: it all started when ___" },
```

- `{E}` becomes the judge's name, `{F}` the first player's name.
- End prompts with `___`.

Names default to Ethan / Ellie / Mitch / Erica but are editable every game.

---

## Troubleshooting

- **Won't connect:** check both devices actually have internet. Double-check the
  6 characters (the code avoids look-alikes — no O/0, I/1, L). If a network blocks
  the relay entirely, the phone offers **"Play on this phone only"**.
- **Big Screen refreshed and lost the game:** it re-uses the same code for that
  browser tab and reconnects automatically; the phone holds the scores.
- **Edited the prompts but the site looks the same:** hard-refresh
  (Ctrl/Cmd + Shift + R) — GitHub Pages and browsers cache aggressively.
- **`#dev` in the URL** exposes debug hooks; ignore it for normal play.

### How the connection works

The phone and Big Screen exchange tiny JSON messages over a public MQTT broker
(`broker.emqx.io`, falling back to `test.mosquitto.org` / `broker.hivemq.com`),
in a topic named by the 6-character code. Answers pass through that broker, so
don't treat the game as private — but the room code is random and the data is
throwaway.
