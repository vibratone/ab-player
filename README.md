[README-v5-no-headings.md](https://github.com/user-attachments/files/26761960/README-v5-no-headings.md)
# Wix / GitHub A/B Audio Comparison Player

This player lets visitors compare two versions of the same audio in sync.

## What it does

- Loads an **unmixed** and **mixed** file for each example.
- Plays both in sync using the browser audio engine.
- Only one version is audible at a time.
- Lets the user switch between the two versions during playback.
- Supports **one player card** or **multiple player cards** from the URL.
- If multiple cards are shown, only one card plays at a time.

---

## Basic URL structure

```text
https://vibratone.github.io/ab-player/?unmixed=UNMIXED_URL&mixed=MIXED_URL
```

Example:

```text
https://vibratone.github.io/ab-player/?unmixed=https://vibratone.github.io/ab-player/audio/song-unmixed.mp3&mixed=https://vibratone.github.io/ab-player/audio/song-mixed.mp3
```

---

## Query parameters

There are 3 groups of parameters:

1. **Global styling parameters**
2. **Single-card parameters**
3. **Multi-card parameters**

---

## 1) Global styling parameters

These act as shared defaults and visual settings. The player no longer shows a main page title or any eyebrow labels.

| Parameter | What it does | Example |
|---|---|---|
| `accent` | Main accent colour used for buttons, active states, and progress. Use hex encoded in URL. | `accent=%23ffffff` |
| `bg` | Card background colour. | `bg=%230f0f10` |
| `panel` | Main panel colour. | `panel=%2318181b` |
| `panel2` | Secondary panel/button colour. | `panel2=%23222226` |
| `help` | Default help text used on cards unless overridden per card. | `help=Switch%20between%20versions%20during%20playback.` |
| `count` | Number of cards to build in multi-card mode. | `count=2` |

---

## 2) Single-card parameters

Use these when you only want **one** player card.

| Parameter | Required? | What it does | Example |
|---|---|---|---|
| `unmixed` | Yes | URL of the unmixed audio file. | `unmixed=https://.../song-unmixed.mp3` |
| `mixed` | Yes | URL of the mixed audio file. | `mixed=https://.../song-mixed.mp3` |
| `title` | No | Card title. | `title=Mix%20Comparison` |
| `unmixedLabel` | No | Label for the left/default version. | `unmixedLabel=Unmixed` |
| `mixedLabel` | No | Label for the right version. | `mixedLabel=Mixed` |
| `help` | No | Help text shown below the buttons. | `help=Click%20play%20then%20switch.` |
| `startOn` | No | Which version is audible by default on first play. Allowed values: `unmixed` or `mixed`. Default is `unmixed`. | `startOn=mixed` |

### Single-card example

```text
https://vibratone.github.io/ab-player/?title=Mixed%20vs%20Unmixed&unmixed=https://vibratone.github.io/ab-player/audio/song-unmixed.mp3&mixed=https://vibratone.github.io/ab-player/audio/song-mixed.mp3&unmixedLabel=Unmixed&mixedLabel=Mixed&accent=%23ffffff
```

### Single-card example with more styling

```text
https://vibratone.github.io/ab-player/?title=Chorus%20Comparison&unmixed=https://vibratone.github.io/ab-player/audio/song-unmixed.mp3&mixed=https://vibratone.github.io/ab-player/audio/song-mixed.mp3&unmixedLabel=Raw&mixedLabel=Finished&startOn=unmixed&accent=%23d6b16f&bg=%230b0b0d&panel=%23141418&panel2=%231e1e24&help=Play%20the%20clip%20and%20switch%20between%20the%20two%20versions.
```

---

## 3) Multi-card parameters

Use these when you want **more than one player card** on the page.

You must set:

- `count=NUMBER`
- a matching set of `example1...`, `example2...`, `example3...` parameters

### Required per card

For each card number, these 2 are required:

| Parameter | Required? | What it does |
|---|---|---|
| `example1Unmixed` | Yes | Unmixed audio URL for card 1 |
| `example1Mixed` | Yes | Mixed audio URL for card 1 |

For card 2, use:

- `example2Unmixed`
- `example2Mixed`

For card 3, use:

- `example3Unmixed`
- `example3Mixed`

and so on.

### Optional per card

| Parameter | What it does | Example |
|---|---|---|
| `example1Title` | Card title | `example1Title=Example%201` |
| `example1UnmixedLabel` | Label for left/default version | `example1UnmixedLabel=Unmixed` |
| `example1MixedLabel` | Label for right version | `example1MixedLabel=Mixed` |
| `example1Help` | Help text for this card | `example1Help=Switch%20while%20playing.` |
| `example1StartOn` | Default audible version: `unmixed` or `mixed` | `example1StartOn=mixed` |

For card 2, use the same pattern with `example2...`

For card 3, use `example3...`

### Two-card example

```text
https://vibratone.github.io/ab-player/?count=2&example1Title=Example%201&example1Unmixed=https://vibratone.github.io/ab-player/audio/song1-unmixed.mp3&example1Mixed=https://vibratone.github.io/ab-player/audio/song1-mixed.mp3&example1UnmixedLabel=Unmixed&example1MixedLabel=Mixed&example2Title=Example%202&example2Unmixed=https://vibratone.github.io/ab-player/audio/song2-unmixed.mp3&example2Mixed=https://vibratone.github.io/ab-player/audio/song2-mixed.mp3&example2UnmixedLabel=Unmixed&example2MixedLabel=Mixed&accent=%23ffffff
```

### Three-card example

```text
https://vibratone.github.io/ab-player/?count=3&example1Title=Verse&example1Unmixed=https://vibratone.github.io/ab-player/audio/verse-unmixed.mp3&example1Mixed=https://vibratone.github.io/ab-player/audio/verse-mixed.mp3&example2Title=Chorus&example2Unmixed=https://vibratone.github.io/ab-player/audio/chorus-unmixed.mp3&example2Mixed=https://vibratone.github.io/ab-player/audio/chorus-mixed.mp3&example3Title=Bridge&example3Unmixed=https://vibratone.github.io/ab-player/audio/bridge-unmixed.mp3&example3Mixed=https://vibratone.github.io/ab-player/audio/bridge-mixed.mp3
```

---

## Important behaviour notes

- In the current version, **unmixed is shown on the left**.
- In the current version, **unmixed is the default audible version** unless you set `startOn=mixed` for a single card or `exampleXStartOn=mixed` for a multi-card example.
- In multi-card mode, **only one card plays at a time**.
- If `count` is present and greater than 0, the player uses **multi-card mode**.
- If `count` is not present, the player uses **single-card mode** when both `unmixed` and `mixed` are present.

---

## Recommended file structure on GitHub Pages

```text
ab-player/
├── index.html
├── .nojekyll
└── audio/
    ├── song-unmixed.mp3
    ├── song-mixed.mp3
    ├── song1-unmixed.mp3
    ├── song1-mixed.mp3
    └── ...
```

---

## Troubleshooting

### The page says audio could not be loaded
Check that:

- the audio URLs open directly in the browser
- the files are public on GitHub Pages
- the URLs are correct and point to real files
- the filenames match exactly, including capitals and hyphens

### The page stays on loading audio
Make sure you are using the latest `index.html` version.

### The audio sounds out of sync
For best results:

- export both files from the same timeline
- keep the exact same start and end points
- use the same file format and settings for both files

---

## Recommended starting URL

```text
https://vibratone.github.io/ab-player/?title=Mixed%20vs%20Unmixed&unmixed=https://vibratone.github.io/ab-player/audio/song-unmixed.mp3&mixed=https://vibratone.github.io/ab-player/audio/song-mixed.mp3&unmixedLabel=Unmixed&mixedLabel=Mixed&accent=%23ffffff
```
