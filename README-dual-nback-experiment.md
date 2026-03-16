# Dual N-Back Cognitive Experiment

A browser-based cognitive experiment implementing the **Dual N-Back task** — a working memory training paradigm that simultaneously tests both **spatial** and **auditory** memory recall.

---

## What is Dual N-Back?

The Dual N-Back task is a well-studied cognitive exercise where participants must track two independent streams of stimuli at the same time:

- **Spatial (Visual):** A cell lights up in a 3×3 grid. You must remember its position from *N* steps ago.
- **Auditory:** A letter is spoken aloud (and shown on screen). You must remember the letter from *N* steps ago.

If either the current position or the current letter matches what appeared exactly N trials back, you press the corresponding button.

---

## Features

- **Dual-channel stimulation** — simultaneous spatial grid flashing and spoken letter via Web Speech API
- **Configurable N-back level** — default is 2-back (adjustable in code)
- **20 trials** with seeded, reproducible sequences (seed: `20240101`)
- **Live score tracking** during gameplay
- **Countdown overlay** with "GO" animation before the task begins
- **Progress dots** showing current position in the trial sequence
- **Keyboard support** — `A` key for Position match, `L` key for Audio match
- **Detailed results screen** showing:
  - Final score, hit rate (%), and average reaction time (ms)
  - Position and Audio breakdown: Hits, Misses, False Alarms, Correct Rejects
  - Full trial-by-trial log table
- **CSV export** for data collection (includes participant ID, trial outcomes, reaction times, and timestamps)
- **Dark theme UI** with a modern, minimal aesthetic (Space Mono + DM Sans fonts)

---

## How to Use

1. **Download** `dual-nback-experiment.html`
2. **Open** the file in any modern browser (Chrome or Firefox recommended for best Speech Synthesis support)
3. **Enter a participant ID** on the intro screen
4. **Read the instructions** — then click Start when ready
5. During the task:
   - Press **`A`** or click **Position Match** if the grid cell position matches N trials ago
   - Press **`L`** or click **Audio Match** if the spoken letter matches N trials ago
   - You can press both buttons in the same trial if both match
6. After all trials, **view your results** and optionally **export a CSV**

---

## Controls

| Key / Button | Action |
|---|---|
| `A` | Respond: Position match |
| `L` | Respond: Audio match |
| Position Match button | Same as `A` |
| Audio Match button | Same as `L` |

> Buttons are disabled for the first N trials (while the memory buffer fills up).

---

## Scoring

| Outcome | Description | Score |
|---|---|---|
| Hit | Match present, response given | +1 |
| Correct Reject | No match, no response | +1 |
| Miss | Match present, no response | 0 |
| False Alarm | No match, response given | −1 |

Score applies independently to both the Position and Audio channels each trial.

---

## Exported CSV Columns

| Column | Description |
|---|---|
| `Trial` | Trial number |
| `Position` | Grid cell index (0–8) |
| `Letter` | Spoken letter |
| `PosMatch` | Whether position was a match (1/0) |
| `AudMatch` | Whether letter was a match (1/0) |
| `PosResponse` | Participant responded to position (1/0) |
| `AudResponse` | Participant responded to audio (1/0) |
| `PosResult` | hit / miss / false_alarm / correct_reject |
| `AudResult` | hit / miss / false_alarm / correct_reject |
| `RT_ms` | Reaction time in milliseconds |
| `Participant` | Entered participant ID |
| `Timestamp` | ISO timestamp of export |

---

## Technical Notes

- **No dependencies or installation required** — fully self-contained single HTML file
- Uses the browser's built-in **Web Speech API** for audio stimuli
- Sequence is generated with a **seeded linear congruential RNG** for reproducibility across participants
- Stimulus display: **500ms on**, total trial window: **3000ms**
- Built with vanilla HTML, CSS, and JavaScript

---

## File Structure

```
dual-nback-experiment.html   ← Everything in one file
```

---

## Version

`v1.0` — Initial release. Dual-channel (position + audio) N-back task.

> See also: [`nback-experiment`](../nback-experiment) — the follow-up single-channel version with a redesigned visual theme.
