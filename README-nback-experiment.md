# N-Back Cognitive Experiment

A browser-based cognitive experiment implementing the **N-Back task** — a classic working memory assessment where participants identify when a stimulus matches one shown *N* steps earlier.

This is the **second version** of the project, redesigned with a warm, paper-toned visual theme and streamlined to focus on a single spatial memory channel.

---

## What is N-Back?

In the N-Back task, a sequence of stimuli is shown one at a time. For each stimulus, participants must decide whether it matches the one that appeared exactly *N* trials ago. This experiment uses **spatial position** as the stimulus — a cell lights up in a 3×3 grid, and you must recall whether the same cell was active 2 trials back.

---

## Features

- **Single-channel spatial task** — position-only N-back (2-back by default)
- **24 trials** with a seeded, reproducible sequence (seed: `20240101`, 8 guaranteed match trials)
- **Live score tracking** during gameplay
- **Countdown overlay** before the task begins
- **Progress dots** showing trial progress at a glance
- **Keyboard support** — `A` key to respond
- **Detailed results screen** showing:
  - Final score, hit rate (%), and average reaction time (ms)
  - Position breakdown: Hits, Misses, False Alarms, Correct Rejects
  - Full trial-by-trial log table
- **CSV export** for research data collection
- **Warm paper-toned UI** with a clean, readable aesthetic (Lora + Source Sans 3 fonts)

---

## How to Use

1. **Download** `nback-experiment.html`
2. **Open** the file in any modern browser
3. **Enter a participant ID** on the intro screen
4. **Read the instructions** — then click Start when ready
5. During the task:
   - Press **`A`** or click **Position Match** if the current grid cell position matches the one from 2 trials ago
   - Do nothing if it does not match
6. After all trials, **view your results** and optionally **export a CSV**

---

## Controls

| Key / Button | Action |
|---|---|
| `A` | Respond: Position match |
| Position Match button | Same as `A` |

> The button is disabled for the first N trials while the memory buffer fills up.

---

## Scoring

| Outcome | Description | Score |
|---|---|---|
| Hit | Match present, response given | +1 |
| Correct Reject | No match, no response | +1 |
| Miss | Match present, no response | 0 |
| False Alarm | No match, response given | 0 |

---

## Exported CSV Columns

| Column | Description |
|---|---|
| `Trial` | Trial number |
| `Position` | Grid cell index (0–8) |
| `PosMatch` | Whether position was a match (1/0) |
| `Response` | Participant responded (1/0) |
| `Result` | hit / miss / false_alarm / correct_reject |
| `RT_ms` | Reaction time in milliseconds |
| `Participant` | Entered participant ID |
| `Timestamp` | ISO timestamp of export |

---

## Technical Notes

- **No dependencies or installation required** — fully self-contained single HTML file
- Sequence generated with a **seeded linear congruential RNG** for consistency across sessions
- Stimulus display: **600ms on**, total trial window: **4000ms**
- Built with vanilla HTML, CSS, and JavaScript

---

## File Structure

```
nback-experiment.html   ← Everything in one file
```

---

## Version

`v2.0` — Single-channel spatial N-back. Redesigned UI with warm theme and extended trial count (24 trials vs. 20 in v1).

> See also: [`dual-nback-experiment`](../dual-nback-experiment) — the original version with simultaneous spatial and auditory channels.
